# Docker image for CircleCI

This is a circleci node based docker image that has the following ;
1. Firefox and geckodriver
2. Chrome and it's webdriver
3. PhantomJs
4. Java
5. Pa11y for accessibility testing
6. Cloud foundry command line tool

This image was created specifically to handle selenium tests. It has been tested with 

### How to build
```
docker build -t <image_name> .

docker build -t saumarah/circleci_node_selenium .

```

### How to use or test locally
Create a new Dockerfile
``` 
FROM saumarah/circleci_node_selenium:1.1.0

WORKDIR /home/circleci/app

ENV DEBUG="nightmare*,electron*"

COPY package.json /home/circleci/app/

RUN npm i
RUN npm run build

EXPOSE 3000

CMD npm run start
```

Run it 
``` docker run -p 3000:3000 frontend-image ```

Execute a certain command
``` 
docker ps
docker exec -it 5f6f74a73d30 npm run test:acceptance
```

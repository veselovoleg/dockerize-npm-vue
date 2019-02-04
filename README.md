##Initialize the project 
docker run -v "${PWD}:/$(basename pwd)" -w "/$(basename pwd)" -it node:11.1-alpine sh -c "npm i -g @vue/cli && vue create ."

##Build => localhost:8000 
docker build -t dockerize-vue . docker run -it -p 8000:80 --rm vue-docker

##Develop => localhost:8081 (in docker-compose.yml) 
docker-compose up --build

##Install new package 
docker-compose exec frontend npm i packagename --save
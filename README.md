
cd /home/ubuntu/app
sudo npm install ejs mongoose express
#Populates data on http://development.local:3000/posts
node seeds/seed.js
node app.js

#reverse proxy:
cd /etc/nginx/sites-enabled
sudo vi default

#press i to insert and then edit location and add:
proxy_pass http://localhost:3000

#check that changes have worked
sudo systemctl stop nginx
sudo systemctl start nginx
sudo nginx -t

#start app again
cd /home/ubuntu/app
node app.js

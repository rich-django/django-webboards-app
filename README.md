Launch an amazon EC2 Ubuntu 16.04 instance with the below text set as the user data, and http and port 8000 connections allowed.
After the instance has initialised, visit http://[the instance IP]:8000 to use the app.

----------------------------------------------------------------------

#!/bin/bash

# install python
sudo add-apt-repository ppa:deadsnakes/ppa -y
sudo apt-get update -y
sudo apt-get install python3.6 -y
# install pip
wget https://bootstrap.pypa.io/get-pip.py
sudo python3.6 get-pip.py
# install package to create virtual envs
sudo pip3.6 install virtualenv
# copy over git repository
sudo apt-get install git
git clone https://github.com/rich-django/django-webboards-app.git
cd django-webboards-app
# create and start virtual environment
virtualenv venv -p python3.6
source venv/bin/activate
# install django within virtual env
pip install django
pip install django-widget-tweaks
cd myproject1
# start django server
python manage.py runserver 0.0.0.0:8000

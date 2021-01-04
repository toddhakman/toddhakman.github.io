---
title: "Raspberry Pi Home Web Server"
date: 2021-01-04
categories:
  - blog
  - practice
---

# setting up an old raspberry pi as a web server

I have had a Raspberry Pi 3 sitting around the house for a few years now collecting dust and wanted to put it to use. Until I can think of a more specific purpose (and a good justification to upgrade to a Raspberry Pi 4) I will be using it as a web server at home.

### the plan

For the first attempt of this, I intend to install Raspberry Pi OS, then nginx, mysql, and php. I landed on nginx as opposed to apache as I have some (very litle) previous experience with apache, but none with nginx. Raspberry Pi OS appears to be the new name for Raspbian, something I had used years ago with the original Raspberry Pi 1. For my purposes, I am also leaving my Raspberry Pi headless, and using SSH to connect from my laptop or desktop. For those reasons, I chose Raspberry Pi OS Lite.

### necessary equipment and software

- Raspberry Pi (I imagine any model will work, but newer the better)
- SD Card (mine is 16GB I believe)
- A computer that has a card reader
- Monitor, keyboard, and HDMI cable to make initial setup easier
- [Raspberry Pi Imager](https://www.raspberrypi.org/software/)
-  SSH client (I used PuTTY on Windows)

### setup

With my SD card plugged into my laptop, I ran the Raspberry Pi Imager program, chose my SD card, and had the Raspberry Pi OS Lite version installed. I put the SD card in my RPi and plugged it in near my computer, using my desktop monitor to do the initial OS setup and get my RPi on my local Wi-Fi network. After the OS loaded I used the default user and password for Raspberry Pi OS to get logged in and ran raspi-config to get connected to Wi-Fi, turn on SSH, and change its hostname to something of my liking, lets say myrpi. Now I was ready to leave the RPi headless somewhere with good Wi-Fi connectivity and connect using PuTTY on my laptop or desktop.

### getting the web server set up

With PuTTY up and connected by hostname to my RPi, I was ready to install updates, and begin downloading nginx, mysql, and php. First I followed the instructions on Raspberry Pi OS's website [for updating and upgrading Raspberry Pi OS](https://www.raspberrypi.org/documentation/raspbian/updating.md). Then it was time to install nginx. After it completed, I was able to verify it worked by going using the hostname in my web browser using http://HOSTNAME, in my case http://myrpi and saw the default nginx index.html. Great!

Next I set out to install mysql. But in running sudo apt install mysql, I found that mysql in Raspberry Pi OS is no longer available, so it was time to use mariadb. My experience with mariadb is limited to hearing it talked about at an old job doing tech support for a SQL based software. I had been writing SQL queries to generate reports for customers but was very new to SQL. As such, I dove right in with mariadb, much the same was I went with nginx over apache. With mariadb installed, my RPi now was also a SQL server and playground for me to start learning more about SQL.

Finally, I got php installed and checked by making a simple 'Hello World' index.php file and placing it in my /var/www/html folder. Further, I also learned that in order for nginx to read the php file, I would need to edit the defaults file in /etc/nginx/sites-available/. I was now able to see my simple 'Hello World' and knew php was working.

### conclusion

That's it! I have a playground to expand on my skills in HTML, CSS, PHP, and SQL, which will also double as a place to expand on python skills as well. Next will be establishing connection to the SQL database for both PHP and python. In setting up the web server, I have gleaned that I will need to modify a file to allow for remote connection to the database. Further, I will need to understand GRANT commands in SQL more to make sure that I will be able to remotely access my DB with python, PHP, or software like SQLYog.

If there are any mistakes that I have made, or questions about the process, please feel free to email me. I will take a look and add a new post to make clarifications or corrections.

Happy New Year!

Todd

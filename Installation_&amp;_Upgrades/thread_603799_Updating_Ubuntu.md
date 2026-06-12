---
title: "Updating Ubuntu"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by echolink on 2007-11-05
Hello all, my name is Ben, I am new to ubuntu, I recently have come from using PCLinuxOS 07, I installed and when I booted from my drive into ubuntu, I had a update notification in the task bar. I started the Download, and Installation of the updates, about 1min into the install I recieved a message saying. [SIZE="4"]**E: tar: subprocess post-installation script returned error exit status 9 **[/SIZE] what is this message. I need to install the updates so I can upgrade to Gusty 7.10 i  am currently running Feisty 7.04.

---

### Post by ROBarber on 2007-11-05
it seems that you are using a proxy server for connecting to internet. you have to configure it so you can complete your task, on the other hand you can try using the following commands:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install.

if you are root, don't use sudo.

good luck

---

### Post by echolink on 2007-11-05
How do I make it to were its not a proxy server. Im behind router at the moment but its a basic home network. I tried the commands I still got the message E: tar: subprocess post-installation script returned error exit status 9, Im really not to sure about this. I to familiar with KDE Enviorment this is my first time on gnome desktop. Thxss.

---

### Post by ROBarber on 2007-11-06
try this command on a terminal and paste the messages here please

sudo apt-get install -f

---


---
title: "gpg: Conflicting Commands"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by Lisaj on 2012-04-30
Hi, i am relatively new to Linux (have used many live disks) and have had my install of ubuntu 12.04 for a few days now. For the most part i have found it easy to use and have been comfortable with it. 
now i have the first question i can't resolve myself: Adding Googles repository to my list. when i first ran the command supplied by google i found that i did not have wget installed. so used apt-get to install it. This worked fine (as far as i can tell) so i re-ran [googles code]("http://www.google.com/linuxrepositories/"):

wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add -deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

and get the message 'gpg: Conflicting Commands' could someone tell me where i am going wrong and how to fix this please

---

### Post by NoonesF0oL on 2012-04-30
new script :
wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add linux_signing_key.pub

then you need to edit 
/etc/apt/sources.list 
and add this line at the end

[deb http://dl.google.com/linux/deb/]("http://dl.google.com/linux/deb/") stable non-free

the end

hope you find this usefull
:popcorn:
edit:
you will need to be root or use sudo to make changes to the /etc/apt/sources.list
so run 
sudo vi /etc/apt/sources.list
or if you use midnight commander (i have done for as long as i can remember)
sudo mc /wtc/apt
select the sources.list and press F4 to open enter the line and press F2 to save then F10 to exit out

---

### Post by Lisaj on 2012-04-30
Thanks for your reply. 
All is now working :) and yes i do use mc.

---


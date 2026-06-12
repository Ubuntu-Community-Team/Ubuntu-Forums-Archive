---
title: "apt-get install command"
date: 2010-12-12
forum: Installation &amp; Upgrades
---

### Post by raac on 2010-12-12
Hello guys, I have kubuntu 10.10 and I tried to install a driver for wireless card with the apt-get install command and did not work (firmwireb43....) anyway, I got my wireless to work afterwards, but now everytime that I install something through apt-get install command, it would install the program and then show the same errors from the previous installation attempt, how can I make it not to show anymore???


When I install kwrite, it'd show this (I'm installing it for the second time, I did this so you can see the error at the end)...

sudo apt-get install kwrite

Reading package lists... Done
Building dependency tree       
Reading state information... Done
kwrite is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 173 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
[COLOR=Red]Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]



//No matter what I installed it'd show the same errors at the end (firmware-b43-installer)

//By the way, I'm still learning linux...I just want it to dissapear

Thanks

---

### Post by ryadav on 2010-12-12
give this a try

sudo aptitude autoclean
sudo aptitude clean

---

### Post by raac on 2010-12-12
I'm not sure if I did it right. I did this....

sudo aptitude autoclean
[sudo] password for tony: 
sudo: aptitude: command not found


sudo aptitude clean
sudo: aptitude: command not found


What am I doing wrong?

---

### Post by FreezWay on 2010-12-12
try using
```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```

---

### Post by raac on 2010-12-12
This was my output....

tony-Inspiron-1525:~> sudo apt-get clean
tony-Inspiron-1525:~> sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tony-Inspiron-1525:~> sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 173 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)


I tried to install another program and did not fix it... what should I do?

Thanks again

---

### Post by sikander3786 on 2010-12-12
firmware-b43-installer has been causing problems for many users recently. Most of them solved by removing it completely.

```
sudo apt-get remove --purge firmware-b43-installer
```

---

### Post by oldos2er on 2010-12-12
> **raac said:**
> I'm not sure if I did it right. I did this....

sudo aptitude autoclean
[sudo] password for tony: 
sudo: aptitude: command not found


sudo aptitude clean
sudo: aptitude: command not found


What am I doing wrong?

Nothing. Aptitude is not installed by default in 10.10. You can safely substitute 'apt-get' for 'aptitude' in the above commands.

---

### Post by raac on 2010-12-12
Thank you so much guys

the command

sudo apt-get remove --purge firmware-b43-installer
fixed my problem

---

### Post by ryadav on 2010-12-12
just realized i like using aptitude over apt-get =P and for that to work you would 1st need to install aptitude :) ..mental note, use apt-get when replying to post on here!

---


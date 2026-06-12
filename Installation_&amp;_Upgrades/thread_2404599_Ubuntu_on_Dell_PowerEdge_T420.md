---
title: "Ubuntu on Dell PowerEdge T420"
date: 2018-10-25
forum: Installation &amp; Upgrades
---

### Post by kylepaddock on 2018-10-25
Please move if this post is in the wrong section. This is my first time digging into Linux. I currently am running Ubuntu on a USB drive for testing on my laptop. I want to install drivers on it for the computer it is going to be used on which is a Dell PowerEdge T420. Online Ubuntu says that the T420 is supported. On Dells website only the driver for Suse and Redhad are listed. What do I need to load to the system for it to all work.

---

### Post by kc1di on 2018-10-26
Hello kylepaddock and welcome to Ubuntu forums, 

Most dells work quite well out of the box with Ubuntu.   If the usb live session is working properly most likely the installed version will work as well.  If there is something that is not working properly IE wifi or something it may require a propriety driver.  My Dell use a broadcom wireless card and I have to install the driver for that after install but it is in the Ubuntu repository so I don't have to down load it from a third party.  Give us some details about which drivers you are talking about and we should be able to help you. 

One good way to give an over view of your system is to install inxi a command line tool from the ubuntu repositories with this command in a terminal ```
sudo apt install inxi
``` once that is installed issue this command ```
inxi -Fxz
``` and copy and post the output in your next post.  That will give us most of the info needed to advise you.

Again Welcome to the wonderful world of Ubuntu.

---

### Post by kylepaddock on 2018-10-26
Ok, Thanks. I wil have access to the Dell computer on Sunday to test it all out. If it works out of the box that would be awesome.  The main thing I need to work is the NIC Ethernet and the RAID card. I have a Nvidia graphics card in it but I know that will work. For now I am just setting up my samba, remote access, and ftp and such so that it will all be ready for the Dell. I will let you know what I find on Sunday.

---

### Post by 7-glenn on 2019-06-11
I have a T410 which works perfectly with Ubuntu 18.04 (and also 16.04 before that)

---


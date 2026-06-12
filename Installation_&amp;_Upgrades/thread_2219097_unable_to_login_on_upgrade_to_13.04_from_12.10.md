---
title: "unable to login on upgrade to 13.04 from 12.10"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by chimanrao on 2014-04-22
Hi, 
I am facing multiple issues on upgrading from 12.10 to 13.04

After upgrade when the machine restarted, I starting this error " permission of the setuid helper is not correct".
The KDE session would not start after that.

On searching, I found that the solution that was suggested was to switch to console and run 

sudo dpkg --configure -a

When I ran that I got an error which read "too many errors" (I do not remember the precise error, I am writing this from a different computer.)

The other recommendations where to run 
sudo apt-get install

But here the problem is that the computer is not connecting to my wireless
If I do 
ifconfig
I see only eth0 and lo. wlan0 is not found.

How do I get the console to connect to wlan0 if the upgrade has goofed up?

---

### Post by mörgæs on 2014-04-24
Both of these are obsolete. You will save yourself time by doing a fresh install of 14.04.

---

### Post by chimanrao on 2014-04-24
thankfully, I did not have to fresh install. For others who land in this trouble,
boot with live cd,
mount the partition as chroot
run the update scripts from this.

---

### Post by mörgæs on 2014-04-24
But 13.04 is unsupported. You should be using 13.10 or 14.04.

---


---
title: "reinstall from scratch and keep personal files?"
date: 2008-10-12
forum: Installation &amp; Upgrades
---

### Post by AGSzabo on 2008-10-12
hi,

just annother question: i want to install (not to update but really do it from scratch) the 8.10 from cd over my updated 7.4 but i need/want to keep all data in my home dir, all personal files and if possible all the installed applications/software (update them, too, if possible). is there a way?

thank you,
AGS

---

### Post by upchucky on 2008-10-12
if you created a separate home partition on your original install then yes, everything in your home partition will be intact on a new install.

If you do not have a separate home partition then you need to back up whatever you want to save to a external drive or other partition if you have it, if you have room on the internal drive you could partition it then back up to the new partition you have created.

when you redo your install, make a separate home partition, and only install and save stuff there, then if you ever need to reinstall it will be intact on the new install. if you set up linux properly you should never have to reinstall.

if you experiment with the pc and the install, then make a iso image of your install, before making any changes. then if you hose the system, it takes about 20 minutes to be up and running by restoring from the image you created and you wont have to redo any installs or settings.

I have a image of my install stored on an eight gig thumb drive, and I have only used it once, that was to see if it actually works.

---

### Post by AGSzabo on 2008-10-12
hi upchucky,

thank you for the lot of informations you gave me. you say it wont ever be necessary to reinstall linux, however my 7.4 got pretty messed up after many updates. then the upgrade to 8.4 even made these errors more complicated... it would be the best to reinstall...

btw, may my /home directory partition be ntfs? and are you sure ubuntu 8.10 install wont overwrite or write anything to my /home ..?

well, regards,
AGS

---

### Post by upchucky on 2008-10-12
linux /home must be ext3 partition, but you can back up stuff to the ntfs partition cause linux reads/writes those just fine now. windows still cant read/write linux partitiions tho, that is why you install windows first then linux.

if your home partition is a separate partition than where linus is installed then it will be intact after a new install.

if your 7.04 is messy it is easy to clean up with apt-get

use apt-get to purge remove any software you do not want then apt-get update it. when it is all updated then do apt-get upgrade to 8.10

keep in mind that depending on how you have your video set up you may have to redo it after the upgrade.

I use knoppix and supergrub advanced to keep system running and repair windows or linux files. especially after doing any partitioning or reinstalling,

---

### Post by AGSzabo on 2008-10-12
do you think the user rights and links for the files copied to ntfs are preserved?

i had no luck with apt-get, my system is totally up to date and ... messy,full of warnings here and there...

---

### Post by WWSmith36 on 2008-10-12
I do this to fully check and upgrade my system.

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean all
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean all
sudo apt-get autoremove

This usually keeps it happy.

Here is a link that might help you with reinstalling applications.
[http://mybrainrunslinux.com/node/2](http://mybrainrunslinux.com/node/2)

Hope this helps

---

### Post by AGSzabo on 2008-10-13
> **WWSmith36 said:**
> 
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean all
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean all
sudo apt-get autoremove

this did not do anything changes. is suppose the desktop applications for update/upgrade do the same...

---


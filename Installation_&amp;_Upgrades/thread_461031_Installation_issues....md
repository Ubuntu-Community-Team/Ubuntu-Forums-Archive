---
title: "Installation issues..."
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by njsdaredevil on 2007-06-01
Hi all,
First time poster, long time reader... I've made the change from windows to linux last night using Kubuntu (and I've searched, posted, etc... at their forum) and I've been having some serious issues.

I do have VERY little Linux knowledge but obviously not enough.  I've installed flash (which took FOR EVER AND A THIRD to figure out) and to me, that's an accomplishment!!! Anywho, I've tried installing other apps, such as firefox, and vlc viewer since there's no way of the Kaffeine will read my mpg files and such.

Aside all of that, I've encounterd an issues right out of the box! IT WON'T DETECT MY SECOND HDD! what drives me insane is that when I was first installing Kubuntu, it recognized it, even asked me if i wanted to install the os in it.. a friend of mine whom's pretty good with linux and knew all the correct commands to run STILL couldn't find the hdd... all in all this sucks...

I've tried reading some tutorials, but the steps start you off on a "ok you already know linux... you already know what to type these commands" type of feel... up until 2 in the morning i found out what terminal was and what i should do to install things BY MISTAKE! lol

Please, PLEASE I beg of you, help me out... I'm currently creating the ubuntu cd so i can use it instead of kubuntu... SOLELY BECAUSE there seems to be more documentation than Kubuntu (and I totally understand why too)

Thanks for all your help, in advanced!

---

### Post by blazercist on 2007-06-01
sudo fdisk -l

should give you a list of all the block devices

once you determine which one is your second drive (itll be something like /dev/hda2 or /dev/sda3 depending on the configuration of your system and what type of harddrive it is) you can do

edit: i should explain this:  /dev/ is a folder which contains a list of all the block or storage devices, each device for instance a regular old IDE harddrive will have a name, for regular IDE HDD's its going to be hda or hdb depending on which IDE cable its hooked up to... for SATA and PATA , I believe its sda, each of these can have a number too like hda1 or hdb3.... when doing sudo fdisk -l in terminal each drive and/or partition will display its format type and size, this should help you determine which one is your 2nd drive.

sudo mkdir /media/drive2  #here you are making a new folder inside the media directory called "drive2"
sudo mount /dev/(here you must substitute your drive) /media/drive2   #here you are making a link or "mounting" your 2nd harddrive to the folder you made in the previous step

if all goes well you will be able to see your drive under /media/drive2

now to make it auto mount each time you boot:

sudo gedit /etc/mtab   #this is using a text editor to edit a file which contains information regarding your MANUALLY mounted filesystems
 find the line that references your 2nd drive and copy it and close that

sudo gedit /etc/fstab  #this is using a text editor to edit a file which contains your AUTOMATICALLY mounted filesystems. 
and paste the line you copied from the other file and save.

now when you reboot it should automount.

---

### Post by njsdaredevil on 2007-06-01
Awesome!
I'll try that once I get home - hopefully it works...

now, should i leave kubuntu in the dust and go with ubuntu? in your opinion... knowing my background at this point.

---


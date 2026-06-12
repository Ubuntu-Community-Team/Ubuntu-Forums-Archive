---
title: "Intaller freezes"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by adromidon on 2007-07-22
I recently decided to start my computer from scratch so I erase all 3 OS on my system.

When I try to re-install Ubuntu everything seems to run fine until the installer gets to the partitioner where it scans up to 46% then freezes if i close the installer out in the first 60 seconds it freezes the desktop is still operational but upon going to a menu it locks up if i let it site longer then 60 seconds the entire system locks up forcing me to do a hard reset of the computer

---

### Post by Pumalite on 2007-07-22
One hard drive? Sure of the iso and CD? Then use Gparted. Erase everything in there and partition as you wish. Then install.

---

### Post by adromidon on 2007-07-22
> **Pumalite said:**
> One hard drive? Sure of the iso and CD? Then use Gparted. Erase everything in there and partition as you wish. Then install.
I tried that but the partitioner still attempts to load when i run the installer.

I have 3 harddrives one usb and 2 internal

I have Fedora 7 on my first HD and want this on the second if i patition it the way i want the partitioner still loads is there a way to bypass this ?

---

### Post by Pumalite on 2007-07-22
I you use an entire drive for Ubuntu, you could go the 'Guided> Use Entire Drive'. Maybe somebody else knows better.

---

### Post by adromidon on 2007-07-22
> **Pumalite said:**
> I you use an entire drive for Ubuntu, you could go the 'Guided> Use Entire Drive'. Maybe somebody else knows better.

it never gives me an option right after i select the keyboard layout language it goes to the patitioner

---

### Post by Pumalite on 2007-07-22
What are you installing? You better check your iso with md5sum and the CD for corruption before install. Can you do with English?

---

### Post by adromidon on 2007-07-22
> **Pumalite said:**
> What are you installing? You better check your iso with md5sum and the CD for corruption before install. Can you do with English?

Yes I infact need english lol I select english then it is supposed to install this is one of the cds from the free media program I have used it to install from before and it worked but this time it appears to be screwing up

I am just trying to install basic i386 x86 Ubuntu 7.0.4 nothing fancy

---

### Post by Pumalite on 2007-07-22
Have you checked the CD for corruption? It may be scratched. If so, better download yourself a new iso.

---

### Post by adromidon on 2007-07-22
> **Pumalite said:**
> Have you checked the CD for corruption? It may be scratched. If so, better download yourself a new iso.
How would I check for corruption? And is there an installer i can download to install it from a different linux distro?

---

### Post by Pumalite on 2007-07-22
If you have a 'Live CD' of Ubuntu, second or third in the menu is 'Check CD'. I don't know about installing from another linux distro. Maybe somebody else does.

---

### Post by adromidon on 2007-07-22
> **Pumalite said:**
> If you have a 'Live CD' of Ubuntu, second or third in the menu is 'Check CD'. I don't know about installing from another linux distro. Maybe somebody else does.

Ok I will try that later then

---

### Post by tuku on 2007-07-24
I had the same problem when I tried to install Ubuntu  7.04 on my HP laptop.  I was doing a manual partition since I had PCLinux Os before and I wanted to install Ubuntu over PCLinux. The live CD installer always locked up trying to format/partition the disk. I checked the CD for defects, even checked the MD5 checksum. 

Finally I installed Ubuntu 6.06LTS and then upgraded to Feisty Fawn via the Update Manager. Everything worked fine after that.

I think there is a bug in Feisty Fawn installer when you try to change an existing ext3 partiton from /media/hd* to /

---

### Post by adromidon on 2007-07-24
I managed to get it to work but i needed to use the alternate installer

---


---
title: "partition help..."
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by allzzzzz on 2009-12-03
hi im trying to install ubuntu 9.10 and i want to overwrite the old "gos" i have that tc2502 and i would like to completely overwrite the mbr can anyone tell me how to set it up?

---

### Post by darkod on 2009-12-03
Sorry, I didn't understand all of it. You want to install 9.10 on the whole disk? If you have all the data you need from it backed up, just boot with the 9.10 cd and select Use Whole Disk option at step 4 where it asks where to install.

---

### Post by allzzzzz on 2009-12-03
yes my ma ****** up the whole system and there are no files to back up or nothing i care about while im installing the new disk it gets to the partition part and kinda shows nothing ill try again in a min. and see if i can figure it out thank u for the response

---

### Post by darkod on 2009-12-03
There is graphical guide here:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by allzzzzz on 2009-12-03
ok after i pick my keyboard config i get to the partition step and then there are no choices a largly empty screen with device/type/mount point/format/size/used (on top) and add, change, delete, and revert on bottom left, and quit, back, and forward on the bottom right these three things are the only things i can click, right clicking only brings up the revert option, your graphical thing was almost the same until i get to this step there is no "guided" option...

---

### Post by darkod on 2009-12-03
You mean it's not presenting any hard drive to select?

If it's that, there might be some raid array leftover on it. Boot with the cd but select Try Ubuntu option. When it loads, open terminal (Aplications-Accessories-Terminal) and execute:
sudo apt-get remove dmraid

Then reboot and see if it will show you the drive this time.

---

### Post by allzzzzz on 2009-12-03
well the command did something but it still shows the same almost blank page with no options any other ideas? i appreciate your time and effort on the subject, thank u

---

### Post by darkod on 2009-12-03
I don't know why it's doing that. Another thing you could try is boot again with the Try Ubuntu option, or maybe you are already booted like that, open Gparted (System-Administration) and it will show you your drive and partitions. So see what it shows you.
In fact, if you are sure you don't need anything from the data on the hdd, you can also use Gparted to delete all the partitions on the hdd, or just reformat some of them. Maybe that would help for the disk to be recognized by the installer.

---

### Post by allzzzzz on 2009-12-03
i already tried dparted but nothing is recognized its empty...i have no idea whats up

---

### Post by darkod on 2009-12-03
Does your hdd work at all???

---

### Post by allzzzzz on 2009-12-03
idk im a noob by hdd do u mean hard drive? like i said i opened gparted and the only option is quit lol i cant create edit or delete anything how do i check the hdd

---

### Post by darkod on 2009-12-03
Yes, I meant the hard drive. If you boot your computer without the cd inside, it should try to boot any OS from the HDD. What does it show? Any error? Anything happening at all?

PS. Or first in ubuntu in terminal execute
sudo fdisk -l (small L)

Copy the reslts here, what it shows.

---

### Post by allzzzzz on 2009-12-03
the command didnt do anything first i typed it wrong and it said so but then it just went to the next line....
ubuntu@ubuntu:~$ sudo fdisk-l
sudo: fdisk-l: command not found
ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$

---

### Post by allzzzzz on 2009-12-03
oh and it wont boot without a bootdisc, ive been using the gos one for some time and i just got my ubuntu one and wanted to install it, is my hard drive shot im running off the ubuntu disk now as i said it will not boot with out one i cant remember the error when the boot fails i can try but it may take a few minutes...

---

### Post by darkod on 2009-12-03
It looks like the HDD is gone. Dead or similar. Gparted doesn't show it, the ubuntu installer doesn't show it, fdisk doesn't show it...
I'm out of ideas. If you are running from a CD maybe the HDD is gone long ago.

---


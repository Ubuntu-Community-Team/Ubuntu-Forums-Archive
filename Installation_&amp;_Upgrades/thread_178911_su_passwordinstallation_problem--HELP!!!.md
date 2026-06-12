---
title: "su password/installation problem--HELP!!!"
date: 2006-05-18
forum: Installation &amp; Upgrades
---

### Post by macbeth0006 on 2006-05-18
Hello,

I am new to this forum and to linux installations in general.  I have a problem installing Ubuntu.  

I recently had to upgrade my pavilion laptop that had a 20GB harddrive.  I replaced it with a 60 GB hard drive.  Bios detects the hard drive, but I suspect there is a problem with bios because when it boots up with Ubuntu or any other system, it completely stalls at GRUB.  I basically only see GRUB and loading...please wait.

I looked on the forums, and other people who have experienced this say its a bios problem and when they have upgraded there is no longer a problem.  For my computer however, I do not see any upgrade and when I contacted HP, I cant find anything.  

So since I cant get Ubuntu to work, a friend of mine suggested to use the live cd to diagnose and possibly get around the problem. 

But in order to do this we need the su password for the live cd...

In his words:  I need to gain root access (su, superuser, even sudo will do) so that we can mount your hard drive and see what the problem might be.

I know that the Ubuntu makes partitions and everything and is getting on the hard drive....but the only way I can use this is via the live CD.

I cant put windows back on.

Any ideas???????

---

### Post by Sef on 2006-05-18
Try this:

Ubuntu and no password

---

### Post by macbeth0006 on 2006-05-18
Hello, thank you very much...but that doesnt do anything.
It says su: authentication failure

---

### Post by Sef on 2006-05-19
> I looked on the forums, and other people who have experienced this say its a bios problem and when they have upgraded there is no longer a problem. For my computer however, I do not see any upgrade and when I contacted HP, I cant find anything.

Who made your BIOS? Contact them.  There are downloads via the net.  It may cost about $30 US, but if it gets your computer running, it will be worth it.

---

### Post by Walter Rau on 2006-05-19
This worked on my **winXP**-system with a **FAT**-partition /dev/hda1:

cd /home/ubuntu
mkdir ./test1
sudo mount /hda1 ./test1
cd ./test1
ls -l
cp testfile1 /home/ubuntu

This worked on my **winXP**-system with a **NTFS**-partition /dev/hda2:

cd /home/ubuntu
mkdir ./test2
sudo mount /hda2 ./test2
sudo ls -l ./test2
sudo cp ./test2/testfile2 /home/ubuntu

So you should at least have read-access to your harddisc.

---

### Post by Fjellfisk on 2006-05-19
HP seems to have abandoned the machine my friend has.  Moral of the story is don't count on HP.  Depending on which distro used (tried Fedora Core, Knoppix, now Ubuntu) GRUB will stall at different places too.  I'm pretty sure it's the BIOS / HD size issue but want to make sure.

---

### Post by Sef on 2006-05-19
> I recently had to upgrade my pavilion laptop that had a 20GB harddrive.
> HP seems to have abandoned the machine my friend has. Moral of the story is don't count on HP.

Since your machine only had a 20 GB harddrive, then the warranty would have expired a few years ago.  

> I'm pretty sure it's the BIOS / HD size issue but want to make sure.

I have a 20 GB HD too, and plan on getting the BIOS upgraded when I get a new hard drive installed on it.

---

### Post by Fjellfisk on 2006-05-20
How much do you think the BIOS upgrades are?

---


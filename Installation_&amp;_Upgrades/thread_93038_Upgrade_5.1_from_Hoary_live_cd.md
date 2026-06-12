---
title: "Upgrade 5.1 from Hoary live cd?"
date: 2005-11-21
forum: Installation &amp; Upgrades
---

### Post by tay on 2005-11-21
I have a Hoary live cd, and want to upgrade to 5.1 server installation.  I don't have a working o.s. , but i do have 10 GB partitioned ext3 with nothing wrote to the partition.  Since i cannot eject the live cd and burn the 5.1 image on the cd, can I write to the partition and then ....?

From my own research i don't know very much.  I have only been working w/ linux a couple months.  

so can you guys give me a couple of clues..

I guess i want to   mount   the partitino,  which is /.dev/hda7   "i think..."

by the command:
~$ mount /.dev/hda7 -F

but then i get the error message of 
mount: can't find /.dev/hda7 in /etc/fstab or /etc/mtab

so.. i go to look in those

ubuntu@cpe-66-91-22-168:/etc$ cd /etc/mtab
bash: cd: /etc/mtab: Not a directory
ubuntu@cpe-66-91-22-168:/etc$ cd /etc/mtab/ -F
bash: cd: /etc/mtab/: Not a directory
ubuntu@cpe-66-91-22-168:/etc$

and i can't.    so once that problem is figured out  i can move on to the next part
which is writing the image to the partition. and then booting from the partition.   I'm sure this thread has come up before, if someone could throw me some bookmarks.

---

### Post by yesplease on 2005-11-21
Are you using the live CD for install? You need the install CD for installation of ubuntu.

The 5.10 installation CD can be downloaded here [http://www.ubuntulinux.org/download](http://www.ubuntulinux.org/download) or with bittorrent.


**Edit: **I seem to have misunderstood you. What is stopping you from installing an OS on the free partition, so you can burn any server software you need on CDrom?

---

### Post by tay on 2005-11-21
um..  thanks..  please read the above post again..  and i'll try to restate this again for anybody else.

I do not have any o.s. installed to my harddrive.   I want to ugrade to 5.1 server.
Now i am looking through the internet from a 5.04 hoary live cd.  From the live o.s. i can download 5.1.  But.. i cannot burn that iso image to cd because i cannot use the cdrom while using a live cd.   My usb flash drive is also recently fried.  so that is not an option.

---

### Post by wakatobi on 2005-11-22
So.... first step, you must buy CD UBUNTU 5.1 INSTALL at computer shop near you

---

### Post by tay on 2005-11-23
um.. as far as i know, ubuntu is shipped for free and is free.  

sorry for the confusion, i just edited the title of this thread because of the confusion.

what i want to do is install the base system in one of my logical drives, and then reboot, then boot that drive, so that is continues the install, without having to burn an iso image, and without having to waste shipping charges.  

I have seen a thread before that served as a guide towards this, but i am lost for finding it again.

---

### Post by yesplease on 2005-11-23
Perhaps this helps

HOWTO: Install Ubuntu Linux without burning a cd -  04-22-2005

[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948) 

or the guide it refers to.

---

### Post by tay on 2005-11-23
thanks, thas what i was looking for.  i did'nt have time to fully look it over, but later i will.   

the guide is a little not quite specific to what i need. because he is taking extra steps to avoid conflict with his windows partition,. but i guess i may need to  do the same thing because of an empty fat32 partition i set up for windows networking.

---

### Post by ranf on 2005-11-23
[QUOTE=tay]I have a Hoary live cd, and want to upgrade to 5.1 server installation.  I don't have a working o.s. , but i do have 10 GB partitioned ext3 with nothing wrote to the partition.  Since i cannot eject the live cd and burn the 5.1 image on the cd, can I write to the partition and then ....?
[/QUOTE]
Just a totally different approach: are there no LUG (Linux User Groups) in your area? Try to find out and just go to a meeting. Most likely there is someone which has a Ubuntu (or other Linux) CD to share.

---

### Post by tay on 2005-11-26
I have a 5.04 installation cd.  and their are no groups in my area.  I live in kauai, hawaii.

---


---
title: "Just Installed. Desktop won't boot on log in"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by Literati on 2008-03-12
Hey all,

I just finished installing 7.10 on my home desktop. I downloaded the 286MB of updates it had for the computer, and as it was instaling, began loking at some System Tools, just to set up the computer. 

I instaled an ATI Radeon driver, and had yet to restart (as it was instaling upgrades) 

So, I changed my resolution, and just looked at sceensavers (going in order through list) I THOUGHT I double clicked on a screensaver, and that it would preview me, but apparently, the computer just decided to boot me out. So I restarted (not sure if packages finished installing or not as it was very abrupt).

Now, when I try to log in, I'm able to log back in, but it just shows me the tan coloured background, and my mouse cursor, and won't load the desktop.

I've tried 

"sudo /etc/init.d/gdm restart

but it didn't work. I'm hoping someone here can help me :) Thank you very much!

---

### Post by Pumalite on 2008-03-12
Boot your Ubuntu Live CD and post:
sudo fdisk -lu

---

### Post by Literati on 2008-03-12
I don'tmean to undermine your advice, and I WILL do that. (Just, I had to transport a CDROM drive from elsewhere into this computer to instal, and now it's back in said other computer and I can't get it right now.)

But first, I would just like to know, what, at this point, the ive CD would have to do with anything? (I'm just trying to understand, not second guessing you)

Secondly, I'd just like to add that now the LOGIN screen is displaying at the resolution I selected (1280x1024) AND, I've tried this too:

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

and still no dice.

EDIT: I just reset, and tried again, and it's working .
o_O

---

### Post by Pumalite on 2008-03-12
I'm trying to see the lay out of your drives/partitions, so I can help you mount the appropriate partition and get at menu.lst. That way I can eliminate some possible errors.

---

### Post by Pumalite on 2008-03-12
> **Literati said:**
> I don'tmean to undermine your advice, and I WILL do that. (Just, I had to transport a CDROM drive from elsewhere into this computer to instal, and now it's back in said other computer and I can't get it right now.)

But first, I would just like to know, what, at this point, the ive CD would have to do with anything? (I'm just trying to understand, not second guessing you)

Secondly, I'd just like to add that now the LOGIN screen is displaying at the resolution I selected (1280x1024) AND, I've tried this too:

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

and still no dice.

EDIT: I just reset, and tried again, and it's working .
o_O

Glad you got it working.

---

### Post by Literati on 2008-03-12
I sure did :) I'm posting from it now ;)
Thank you for your help both last night and tonight Pumalite 
*gives thanks*

---

### Post by Pumalite on 2008-03-12
You are welcome. Good luck.
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---


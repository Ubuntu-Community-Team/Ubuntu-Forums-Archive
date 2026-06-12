---
title: "Ubuntu 12.04 with windows 7 help needed..."
date: 2012-05-18
forum: Installation &amp; Upgrades
---

### Post by ki2002rom on 2012-05-18
Have Ubuntu installed within Windows.  Was running Ubuntu today, prompt showed up to Upgrade to 12.04 (New Version).  Attempted, and progressed through to last step before auto reboot (Iintialization of files I think?!?), then it locked up.  Tried to reboot, etc. and nothing.  Had to shut computer down.  When arrived at screen to choose Windows or Ubuntu as normal, selected Ubuntu and it started but went to balnk Ubuntu screen without request for my password as normal.  Please help and thanks in advance.

---

### Post by darkod on 2012-05-18
A blank screen might be video driver issue. Do you have nvidia?

---

### Post by ki2002rom on 2012-05-18
How do I check the video type?

---

### Post by darkod on 2012-05-18
You don't know what you've got in your computer???

It's probably faster to try using nomodeset to do a one time boot. You have instructions in this link, since you already have it installed you can start from the second part where it explains how to add nomodeset to the grub2 boot menu lines:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

### Post by ki2002rom on 2012-05-18
The screen looks like the normal color ubuntu screen except it's missing the login block for entering password.  I've rebooted several times and keeps coming to that screen.  I actually typed in my passowrd assuming the cursor is there somewhere and when I hit enter I can see the hard drive light fickering as if it progresses through to the normal ubuntu screen.

---

### Post by wilee-nilee on 2012-05-18
You might try from the recovery using straight from the command line.

[FONT=Verdana, sans-serif][SIZE=1]sudo dpkg --configure -a [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]sudo apt-get -f install [/SIZE][/FONT] 

may not need sudo if you see this at the cli #
  
The second command will resume any stuff that was stopped hopefully. 

Not sure if this will fix your setup but worth a try.

---

### Post by ki2002rom on 2012-05-18
How do i get to the command line to attempt this?  I also would like if possible just to go back to original version I had at least because I'm stuck and can't access all the files and information I have saved in ubuntu.  Tried to start in windows and can't figue how to access this info.  SCARED to loss it, this is my biggest concern at the moment.

---

### Post by wilee-nilee on 2012-05-18
> **ki2002rom said:**
> How do i get to the command line to attempt this?  I also would like if possible just to go back to original version I had at least because I'm stuck and can't access all the files and information I have saved in ubuntu.  Tried to start in windows and can't figue how to access this info.  SCARED to loss it, this is my biggest concern at the moment.

The second line in the grub menu is a recovery, there are options there to get a cli. Use the shift key at powering on if you need to se the grub menu if it does not show.

You can't go back, if you can't get this fixed you will have to use a live cd to get the stuff you need.

To be honest a upgrade without having full backups and or a clone of the OS is really not a good way to roll.

A HD can fail at anytime or a computer just breaks, backups are very important, if you want to assure the safety of your goodies.

Not trying to lecture you or be harsh just state the facts. :)

---

### Post by ki2002rom on 2012-05-18
I take the spanking like a man, thanks.  Your chastening was palatable.  I have a backup I do maybe every 4-6 months, but I'm caught now in a twixt.  Not a computer nerd either will confess.  If you have the patience to bear with me and guide me...
 
Thanks, in advance! Karl

---

### Post by wilee-nilee on 2012-05-18
> **ki2002rom said:**
> I take the spanking like a man, thanks.  Your chastening was palatable.  I have a backup I do maybe every 4-6 months, but I'm caught now in a twixt.  Not a computer nerd either will confess.  If you have the patience to bear with me and guide me...
 
Thanks, in advance! Karl

Lol, you can boot the live cd and pull out the stuff you need from the install to add to the backup if it is in a accessible state. You can get the ppa's if you had any from /etc/apt/sources.list.d you would just have to make sure that if you do a reinstall of 12.04 they are covered and that you have the keys for them a well.

If you have a full image a clone you can just put it back in place over the old install.

I use grsync to do backups it saves in a copy of what ever you save usually home in the same exact state and can be opened and just do a drag and drop back in.

Sometimes you have to run a gksudo nautilus to get to some stuff, just be aware that if you do it this way it will saved root protected I believe. I'm not a real expert in this area or any really so hopefully others will post, but I think if you are just going to do data recovery and use your backups a new thread with a appropriate header will get you help the quickest and of a higher quality I suspect.

I'm not really a geek in the open source clan just a poser really with a few specialized but limited skills. :)

---

### Post by darkod on 2012-05-19
I still didn't understand did you try using nomodeset and the problem is still there, or you didn't manage to find how to use it?

Since you have wubi installed, in the windows bootloader that loads first, select Ubuntu.

That should show the grub2 boot menu from wubi. Highlight the ubuntu entry but hit 'e' for edit. That will show the boot lines.

Use the arrows to move the cursor in the line starting with linux, to the end. Add nomodeset after the 'quiet splash'.

Press Ctrl + X to boot. See if that helps.

---

### Post by ki2002rom on 2012-05-21
I can't get to the grub menu.  When I select ubuntu it goes to a blank ubuntu colored screen.  At this point I'm desparate to just have a way to access my files created in ubuntu, copy to disk, reload ubuntu and take off.  Man believe me I take the rebuke for not backing up more frequently, but if someone with alot of patience can just coach me through how to recover the files, would be welcomed.

---

### Post by darkod on 2012-05-21
Looks like you need this:
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)

---

### Post by wilee-nilee on 2012-05-21
You can boot a ubuntu cd and get access, even better a OS running in root like puppylinux or slitaz, both are tiny downloads and will run on a cd or usb flash, to drag and drop off the install.

[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm")

[http://www.slitaz.org/en/](http://www.slitaz.org/en/)

Above post looks good as well, we posted simultaneously.

You might post in the wubi megathread on a recover for wubi as well with a link here to get help from the main wubi helper on the forum as well.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by ki2002rom on 2012-05-21
My son created a boot cd over the weekend.  We tried, but when I went to look for the files and folder in the upper left side icon they weren't there.  Is there another way or specifically how would I get them after the cd is running?

---

### Post by wilee-nilee on 2012-05-21
> **ki2002rom said:**
> My son created a boot cd over the weekend.  We tried, but when I went to look for the files and folder in the upper left side icon they weren't there.  Is there another way or specifically how would I get them after the cd is running?

You have to find the wubi file in the windows programs folder I believe.

Been a while since I installed wubi for just the experience, post in the megathread if you want help from the best here.

---

### Post by darkod on 2012-05-21
The link I posted has all the details you need for mounting the wubi disk and finding the files.

That is a short and clear procedure. Try that first.

---

### Post by ki2002rom on 2012-05-21
Actually I went fishing in windows under Ubuntu Folder and found the root.dsk file, is this what they mean by wubi file?  If so, can I just copy this to a cd, eload ubuntu and then access my files by reloading or reading the disk?!?

---

### Post by wilee-nilee on 2012-05-21
> **ki2002rom said:**
> Actually I went fishing in windows under Ubuntu Folder and found the root.dsk file, is this what they mean by wubi file?  If so, can I just copy this to a cd, eload ubuntu and then access my files by reloading or reading the disk?!?

I'm not going to answer any more as I have given you where to go to get help from a user who really knows this stuff, and is on daily, just so you know, best of luck. :)

---

### Post by darkod on 2012-05-21
By reading the cd you can't, it will be only root.disk file on it. You would still have to mount it somewhere, and that brings you back to the procedure about mounting the root.disk and reading it.

You can do it as it is now, from live mode loaded from the cd.

I don't use wubi so I can't help much. I have posted the procedure you need, the rest is up to you.

This is one of the disadvantages of using wubi, the files are inside the root.disk, not directly in a partition so that you can read it easily.

I suggest your next install to be proper dual boot, not wubi.

---

### Post by ki2002rom on 2012-05-21
Courtesy of bcbc on megathread, thanks and to those who patiently coached/schooled me along the way.
 
*From windows you can use *[[COLOR=#444444]*http://ext2read.blogspot.ca/*[/COLOR]]("http://ext2read.blogspot.ca/")* (download the tool, and point it at the root.disk)*
 
This allowed me to read the disk file and I'll save it.

---


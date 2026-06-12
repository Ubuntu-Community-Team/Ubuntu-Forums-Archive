---
title: "Upgrading to 8.10 and moving files"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by oygle on 2008-11-13
Computer A - Ubuntu 8.04 and has all the data files and apps I use on it. It is not _quite_ up to date (21 updates to do) as I only have dialup.

Computer B -  Ubuntu 8.04, it has no data files or apps that I use at all, and it would be approx. 2 months behind in updates.

I want to upgrade Computer B to 8.10 (will be getting the ISO in the mail soon), and then move all the files to it, from Computer A.

Can someone recommend the best method to do this, especially how I can ensure that 

(i) All my current settings are applied to Computer B
(ii) All the data files are copied/moved across without corruption.

I don't want to use APTonCD, [here is the reason why]("http://ubuntuforums.org/showthread.php?t=979440")

I do have an external (USB) drive, so I could copy everything from Computer A to the external drive, install 8.10 on Computer B, then copy the external drive contents to a seperate folder on Computer B, and then move the data files to the appropriate folders.

In regards to ensuring data integrity for the move, I do have a trial copy of Beyond Compare installed, so could use that, or there may be other methods, like CRC checks, or other tools that make sure the file/s moved are eaxctly the same as the originals, and that **all** files are copied/moved.

---

### Post by Pumalite on 2008-11-13
Take a looki at Clonezilla:
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by oygle on 2008-11-13
Thanks, is Clonezilla 'safe' ?  I don't see it under the apps with Ubuntu.

---

### Post by Pumalite on 2008-11-13
'Safety' depends on how you use it. The human factor...you know.

---

### Post by iponeverything on 2008-11-13
Make sure your data is backed up, so that when thing so pear shaped you can try again.

---

### Post by oygle on 2008-11-14
Aren't there any specific recommendations somwhere, for doing this ?

---

### Post by oygle on 2008-11-16
I see there are some instructions on [Upgrading to Ubuntu 8.01]("https://help.ubuntu.com/community/IntrepidUpgrades") , but I can't seem to find any inforation about moving data files from one computer to another ??

It seems there is no bug in APTonCD either, it was my /var/cache/apt/archives path that was not up to date, for some reason.

---


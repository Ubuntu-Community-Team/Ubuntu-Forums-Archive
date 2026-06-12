---
title: "Can I do a clean install of Ubuntu and keep my old files, without partitioning?"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by marmaladeskies on 2007-12-27
I've had Ubuntu for a couple months, and I love it of course.  But after browsing around on the internet, I decided actually that Xubuntu is a little more what I want (my system isn't really slow or anything, but I basically prefer speed to prettyness, and other reasons).  In any case, I've decided to just do a clean install of Xubuntu, and, though it seems like it should be obvious, I wanted to know if I could do a clean install of Xubuntu, while keeping my many old files, without worrying about a separate /home partition or anything of that sort.  Is there such an option during the installation?  Yes, I've searched for this on google and these forums, but somehow couldn't find an answer; I basically don't want to take any risks.  Thanks in advance!

---

### Post by bergersau on 2007-12-28
The are two thing I can suggest.


1: Install the xface-desktop on your existing system then remove the Gnome desktop.  If my memory serves, there are ubuntu metapackages for both desktops which makes this simple.


2: Backup imporant data first for this one.

Boot with the Gparted live cd. Shrink your current partition. 
Add a new one in the space free'd up and mount /home on the new partition.
Then you can blow away the old install (Except for /home of course) and install clean.   
All your files and settings should be preserved.


There are good howtos out there for all these tasks already.
Good luck.

---

### Post by marmaladeskies on 2007-12-28
Thanks for your prompt response!  So I take it there's no way to keep my old data without making a /home partition?

---

### Post by bergersau on 2007-12-28
Not the I'm aware of. 
During install, the installer will format the / partition.
Unless you have /home on a separate partition I can't see how you could keep your data.

Why not try the option of installing xface and removing gnome?  Unless your system is very untidy now you'll achieve what you want without a clean install.  Come to that, you can have both desktops installed side by side and select which you want to use during boot in GDM.

---

### Post by Herman on 2007-12-28
I never use a separate /home partition myself. I don't like them, all I do is resize my existing operating system to half the size of the hard disk and install the new operating system beside it. Then I transfer any files across when I have tested the new installation and I have it all set up.
That depends on how much of the hard disk is occupied already though. It's easy for me because I have lots of hard disk space and not too many files.

I wonder what would happen if someone had a complete operating system with the files still in it and just resized it to make enough free space on the hard disk to install the '/' of the next installation beside it and mounted the whole original system as /home during the install? 
Then when it boots just go in and delete all the operating system files that you don't need anymore until you get down to the old /home/username directory and then just turn that inside out. (I mean copy out of it what you want and restore it to the newer system's /home). Sort of like the new operating system swallowing the old one and then spitting out the bones! :lolflag:

Regards, Herman :)

---

### Post by marmaladeskies on 2007-12-28
So would it be possible to create a /home partition with all my old files in it, install Xubuntu, completely eliminating Ubuntu and everything except /home, then copy everything from home onto the new partition, and then delete home?  But I may just end up getting xfce and getting rid of gnome, for simplicity's sake.

---

### Post by Herman on 2007-12-29
Yes, there are ways you can do that if you really want to.
I have to agree with the advice bergersau already gave you in the first place though. It would be much safer and simpler to just add the XFCE desktop.
```
sudo aptitude install xubuntu-desktop
```There's nothing wrong with adding another desktop. I have one computer here running four desktops; Fluxbox, IceWM, XFCE and Gnome. 
Right now I'm adding kubuntu-desktop to it as well.
I just select whichever kind of desktop I want at the login screen before I log in, it's under 'Options'-->'Select Sessions', down in the left lower corner of the monitor.  
Having four desktops doesn't slow my system down at all, it just depends which desktop I'm running at the time. When I boot into IceWM it's lightning quick, XFCE is pretty quick too and now that I finally have some new RAM added, I can use Gnome properly too.
IceWM was good when I only had 64 MB or 128 Mb of RAM, now I have 393 MB and can use any desktop I like. If it's pure speed you're after, try IceWM, it's faster than XFCE.
The only disadvantage of having multiple desktops is you might have a few more updates to download from the internet from time to time.

If you tell me how big your hard disk or disks are and how full it or they are, I should be able to give you some good specific advice if you still want to install again.  
You can do almost anything you want with Ubuntu if you know how.  :)

Generally speaking, it's best to make a backup of all your data before doing any work that involves hard disk partitioning. If you have too much data for the available media you usually keep your data backed up on, at least back up your important files before you do anything.

Regards, Herman :)

---


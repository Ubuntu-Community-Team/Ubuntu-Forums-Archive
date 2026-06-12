---
title: "[SOLVED] Ubuntu 8.10 System Requierments"
date: 2008-08-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by adrian007 on 2008-08-10
Hello all. i hope that my question is not stupid and is the correct forum but i need to know what the system requierments are for ubuntu 8.10 as i have a new computer which i keep up to date with the latest ubuntu distrobution but i have a slightly older computer that has lower system specs:

320MB RAM
800 Mhz Pentium 3
4 MB Intergarted Graphics Card

I would like both computers to have the same version so i can have one system througout the home.

I have seen this video on Youtube: [http://www.youtube.com/watch?v=LYGBfmqAa4Q](http://www.youtube.com/watch?v=LYGBfmqAa4Q)

And i am in doubt as if it will work.

so can anyone give me minimum system requierments or tips of it will work on the specs above



Thanks

---

### Post by Gina on 2008-08-10
I think you should be alright though you may need to use the Alternate CD to install - I gather you need a minimum 384MB to install from the Live CD.  I have a Pentium 3 desktop which works with Intrepid (and Hardy).  It's 650MHz with 384MB RAM.  But I could unplug a module to give 256 to test.  You are limited in resolution by your graphics but that would apply to any OS.  

You are very unlikely to be able to use the advaned display effects such as Compiz - only one of my PCs will run it.  No great loss in my opinion.

---

### Post by adrian007 on 2008-08-10
Thats fine as i already have 8.04 and i will use the update manager to upgrade once the stable version comes out in october and i dont need compiz effects.




Thaks for the help

---

### Post by robert shearer on 2008-08-11
If you are running Ubuntu on more than one computer you may want to install 'aptoncd' from the repos.(Install on each computer)

This will allow you to download updates and new apps onto a single computer then using System->Administration->Aptoncd->Create make an iso that you can transfer via flashdrive, or, burn a cd  both being back-ups of your apt-cache.

Move them to the target computer and select 'restore' in Aptoncd to transfer them to your apt-cache on that machine.
 After doing that you will be prompted that new updates are available and you can install them from the cache- no download needed.

Or just insert the cd into the drive on the target computer and wait. It will ask if you want to open it with the 'Package Manager'.  Select yes and the cd will be added as a local repository. 
 No files are loaded to the apt cache but it will(eventually) prompt you that updates are available.If you choose to apply them you will be prompted to insert the cd and they will be downloaded from the cd.The same applies if you use Synaptic to add apps that are on the cd.

I currently use this to keep 4 computers running Ubuntu and one running Xubuntu up to date with only one machine downloading updates and a weekly transfer via cd-rw(or more often if large/critical updates).

Sure saves bandwidth.

---

### Post by Gina on 2008-08-11
Thanks :)  I'll give that a try - I have 4 machines running Ubuntu.  There's a LAN method too but that's none too helpful if wireless isn't working.

---

### Post by ronacc on 2008-08-11
gina you could always do what I do and have a jungle of cat5 cable :lolflag:

---

### Post by robert shearer on 2008-08-11
And cat5 spaghetti is fine if your machines are local.

A couple of the installations I use Aptoncd for are friends machines and they're on Dial-Up.

By applying regular updates I've downloaded they get to stay current and spend their online time doing more enjoyable things than waiting hours for 50Mb of updates to download.

Sneaker-net still works!

---

### Post by Gina on 2008-08-12
I have a 10m cable I can run into the other room but can't close the doors if I do and risk pulling the router off the shelf.  Fortunately Netgear routers seem pretty robust :lol:

Got errors reading the CD -  I'll try again.  Not a writing fault as the write checked out with the verify (K3b).

I tried a USB stick but couldn't get Update Manager to recognise it.  I could use Restore from aptoncd though and used debi package manager to install aptoncd from the ISO archive.

---

### Post by robert shearer on 2008-08-12
It does take forrrrrever to update itself (10-15 minutes is not unusual and 30 minutes has been known)
 
Just restore in aptoncd or add the cd as repository then have cheesy comestibles or coffee until the notification applet pops up in the panel.Then click on it and update manager should open and show the updates available.

I find that it works best if I load the cd and wait for the "open with package manager prompt" then click yes and wait.wait.wait.

---

### Post by stinger30au on 2008-08-12
> **robert shearer said:**
> 
I currently use this to keep 4 computers running Ubuntu and one running Xubuntu up to date with only one machine downloading updates and a weekly transfer via cd-rw(or more often if large/critical updates).

Sure saves bandwidth.


out of interest. i just had an idea. can you save the data as an .iso file and put it in a shared directory on the network and then point the other machines on the lan to that shared directory and let then do their updates ?????

---

### Post by robert shearer on 2008-08-12
Yes Aptoncd can make an .iso file.
Yes you can move it where you like.

As for the rest, I don't know.
Try it and see if it works ? and let us know.

Anyone else know?

---

### Post by Gina on 2008-08-12
There is a way of using your LAN to update other computers but I forget the details now.  I'll try to find the info I'm sure I've got it somewhere.

---

### Post by Gina on 2008-08-12
I've found something...  This is about setting up a server on one machine to carry the updates and then this is used by the other machines as a repository.  I haven't tried it myself. 

Here are a couple of links :-
[http://ubuntuforums.org/showthread.php?t=564301](http://ubuntuforums.org/showthread.php?t=564301)
[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)

This link may also be of use:- [http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)

---


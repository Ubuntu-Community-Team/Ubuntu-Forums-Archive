---
title: "dapper to edgy using the .iso file"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by tchoklat on 2006-10-29
Hi,

Looking for a helping hand here.

Am ruinning Dapper ona dual boot with XP. All is great. I hae now downloaded the edgy sio and burnt it to CD. It cloads as a LiveCD fine, no problems.

I would like to overwrite/upgrade to Edgy from the CD as my dialup on this PC is very slow.

I have tried these commands;

gksu "sh /cdrom/cdromupgrade" 
sudo apt-cdrom0 add
sudo sh /cdrom/cdromupgrade

which I found on various foruems but the result is invariably;

"no such file or directory"
"command not found".
Any advice is most welcome!

Tony

---

### Post by morequarky on 2006-10-29
quick question:  Did you read this help file?  [https://help.ubuntu.com/community/EdgyUpgrades]("https://help.ubuntu.com/community/EdgyUpgrades")

---

### Post by tchoklat on 2006-10-29
Yep, certainly did. I use the command;
sudo apt-cdrom add

and I get told that the system failed to mount the CDROM even though it opens a file browser displaying it's contents whe I put it in.

I have installed Edgy by installing it from the LiveCD but it is a clean install on a separate partition with none of my 'personalizations'. How can I upgrade to Edgy keeping my Dapper set-up, as, might I say, the other OS does.


Tony

---

### Post by confused57 on 2006-10-29
You have to use the Edgy alternate cd in order to perform a cd dist-upgrade from Dapper to Edgy.

---

### Post by tchoklat on 2006-10-29
finally light at the end of the rainbow!  Where do I get it, the update site ony had the regular one?

Tony

---

### Post by argie on 2006-10-29
You have to choose "Other Installation Options" and then pick "Alternate Install CD". For example I would download:
[http://ftp.kaist.ac.kr/pub/ubuntu-cd/edgy/ubuntu-6.10-alternate-i386.iso](http://ftp.kaist.ac.kr/pub/ubuntu-cd/edgy/ubuntu-6.10-alternate-i386.iso)

---

### Post by tchoklat on 2006-10-29
I will downlaod it at work tonite on the T1. What command do I use to overwrite my existing Dapper insatllation so to, in effect, update it to Efty?


regards and thanks ...

---

### Post by confused57 on 2006-10-29
This should explain how:

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

Make sure you change all occurrences of dapper to edgy in your /etc/apt/sources.list before you add the cdrom.

> Edit your /etc/apt/sources.list as root. Change every occurrence of dapper to edgy.

    *

      Long route: Use your preferred editor. If you have a CD-ROM line in your file, then remove it.

        gksudo gedit /etc/apt/sources.list
        sudo nano /etc/apt/sources.list
        sudo vi /etc/apt/sources.list

You might want to turn off your screensaver before beginning the dist-upgrade, or do the upgrade from a console, similar to what's described here in this Breezy to Dapper "howto":
[http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

---

### Post by Cynical on 2006-10-29
Thats not true. Look at the screenshot below, this is what happens when I put an edgy desktop iso into my computer (and I'm on edgy)

---

### Post by confused57 on 2006-10-29
> **Cynical said:**
> Thats not true. Look at the screenshot below, this is what happens when I put an edgy desktop iso into my computer (and I'm on edgy)
I wasn't aware the Edgy Desktop cd had the option to perform an automatic dist-upgrade...the method I gave is the only tried & true method that I've used in the past to dist-upgrade from Breezy to Dapper and from Dapper to Edgy.
Be interesting to know if the automatic dist-upgrade from the desktop cd works ok...there are no guarantees of a successful upgrade regardless of the method.
In fact, I wouldn't recommend someone upgrading to Edgy if their Dapper installation was working "great"...

---

### Post by beameup on 2006-10-29
I'll try that when I update my wifes laptop.

I used this procedure on my desktop(I have posted this elsewhere)

[I]If you have the edgy alternate install CD, you can save bandwidth by using: 

gksu "sh /cdrom/cdromupgrade" [/I]

All went well. I had more updates once I rebooted though, and I had to reinstall some apps like AMSN, Scribus, NVU, and Inkscape.
No big deal. Gnomebaker was gone too and I don't see it in Add/Remove but it's in Synaptic. I have Nero so not a big deal. 

That box you showed had popped up and I closed it](*,)

---


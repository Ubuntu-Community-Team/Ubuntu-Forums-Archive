---
title: "Copy application list from pc to pc"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by tk1269 on 2010-12-02
Hello, I searched the forums for a while trying to find an answer to my question, and hours searching the internet for a how-to that worked for me, but to no avail.

I recently got a new desktop, and did a fresh install of Ubuntu 9.04 Jaunty Jackalope.  The reason I installed 9.04 is because the laptop I have been on for the last 7 years or so suddenly stopped operating with grub updates.  I would t urn the computer on and it would never get past the 'grub loading' screen. but thats a whole different story.  So I did a fresh install of 9.04 off of a startup disc I made a while back.  Then I copied my /home file from my laptop (the old one) and inserted it into the new desktop's /home directory.  Worked like a charm (more or less), and all my settings were transferred to my new computer.  Desktop, Preferences, Admin stuff, I can't find a problem with it.  Now for the applications.

I've tried multiple how-to's but none of them have worked.  I found one that told me to do the following in terminal.  Keep in mind, although I've been running Ubuntu for about three or four years now, I would still consider myself a noob.  Anyway:

sudo dpkg --get-packages <filename><destination> 

this left me with a text only file called 'package.selections'

I was then to copy this file into the home folder on the new computer and run the following:

sudo dpkg --set-selections <directory>

Up until that last command, everything worked just fine.  The list had tons of package titles (none with a .deb or anything though) and their state, got it on to the new computer and ran the code only to get the following error:

dpkg --set-selections does not take any argument

So i ran it without the directory, and it gave me a new line.  So I typed in the directory and it gave me the following:

dpkg: unexpected end in package name at line 1

I've tried numerous other commands changing up the syntax as I go, but haven't gotten any farther.  My goal is to have all the same applications installed on my new rig without having to go and install all the packages one by one.  Please help me get my computer applications back!

---

### Post by zvacet on 2010-12-03
```
 aptitude  --display-format '%p' search '?installed!?automatic' > ~/my-packages

```Move that file to another comp and put file in home directory and run

```
 sudo xargs aptitude --schedule-only install < my-packages 
sudo aptitude install
```

---

### Post by tk1269 on 2010-12-03
Perfect!  Thanks Zvacet!

---

### Post by drs305 on 2010-12-03
Just so you know, the dpkg commands should be:
To save:
```
dpkg --get-selections   > ~/Desktop/packages.txt
```

To input:
```
sudo dpkg --set-selections < ~/Desktop/packages.txt
```

Another way via GUI is to use Synaptic. From the Synaptic menu:
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.

To restore, you would use File, 'Read Markings'

---

### Post by tk1269 on 2010-12-03
Also great DRS!  The how-to I was looking at had some syntax errors I guess.  Either that or it wasn't proper to Jaunty.  Either way, that is good information, thank you.

And the Synaptic thing?  I wish I would have known it was that easy.  Thanks again.

---


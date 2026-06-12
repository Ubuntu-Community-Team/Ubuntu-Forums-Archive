---
title: "Reinstalling Ubuntu with same settings."
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by diabolicalangle on 2010-11-05
Hey everyone,

I've spent quite a bit of time customizing the environment to my liking. I currently have Ubuntu installed under Wubi, but now that I've tried it out, I want to make the switch and use Ubuntu as my primary OS (perhaps with running W7 with VMware or something like that).

I was wondering if there was a way to save all my customizations (desktop, conky, theme, compiz config etc) so I don't have to reconfigure all of that when I reinstall. I remember reading offhand that most everything is stored under /home, but I'm not too sure. 

I'm assuming that if I make the installation CD it will completely wipe everything and install ubuntu (what i want, correct me if I;m wrong).

I can back up my documents and imp files, but I was wondering about the configurations

Thanks again!

---

### Post by bcbc on 2010-11-05
You can migrate your wubi install to partition and keep everything. [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

You'll have to create partitions before running the migration though.

---

### Post by diabolicalangle on 2010-11-10
It seems as if that would transition my system to a dual boot correct? 

What I would like to do is completely get rid of windows, and only have one partition with ubuntu on it. Is that possible?

---

### Post by bcbc on 2010-11-10
> **diabolicalangle said:**
> It seems as if that would transition my system to a dual boot correct? 

What I would like to do is completely get rid of windows, and only have one partition with ubuntu on it. Is that possible?

You want to migrate your wubi to take over your whole hard drive? It's certainly possible, but not straightforward.

The simplest is to migrate the wubi to a new partition, then format and reuse the windows partition (perhaps as a separate /home).

Or just backup all your data and reinstall over the whole drive.

---

### Post by diabolicalangle on 2010-11-10
Alright. I think the best thing would be to back up my data. Is there an easy way to print a list of apps I have installed?

---

### Post by bcbc on 2010-11-10
Look at the LVPM howto [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

It has 'alternative instructions' further down in the post that are basically manual migration instructions. Including backing up your /home directory and getting a list of installed packages. You can tailor that to your needs. Good luck :)

---

### Post by Rebelli0us on 2010-11-10
I'd asked the same question about copying your profile settings:

[http://ubuntuforums.org/showthread.php?t=1557034](http://ubuntuforums.org/showthread.php?t=1557034)

Apparently your customizations are contained in .dot directories.

---


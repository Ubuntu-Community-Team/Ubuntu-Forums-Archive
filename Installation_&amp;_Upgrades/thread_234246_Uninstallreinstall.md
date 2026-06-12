---
title: "Uninstall/reinstall"
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by Graham Gardner on 2006-08-11
I decided to try Ubuntu and was given a Hoary Hedgehog disc which I installed.  I really need the Dapper Drake for my network card and have downloaded and copied it.  Can I unistall HH and do a 'clean install' of DD.  This avoids the need for a double upgrade.

---

### Post by orb9220 on 2006-08-11
Well if you want a clean then during the install just have it reformat the partition you are installing to which I assume is the HH installation?

And make sure you have the very latest iso which just came out and has all the updates on the cd then you won't have to connect to the insternet for  170 updates.

[http://www.ubuntuforums.org/showthread.php?t=233444](http://www.ubuntuforums.org/showthread.php?t=233444)

---

### Post by kaffelars on 2006-08-11
If you have the /home folder as a separate partition, you can use this in Dapper too (without formatting it) :)

---

### Post by Graham Gardner on 2006-08-12
Dear Orb9220
As a complete Ubuntu/Linux beginner I have no idea where the Os is as I just followed the install instructions!.  CAn you tell me how to reformat the partition (in detail if possible as I've read some other threads and don't understand a word) -  I'm sure I'll get better as time goes on

---

### Post by confused57 on 2006-08-12
You might want to open up a terminal, I don't anything about HH, but in Dapper it's...Applications---Accessories---Terminal, then enter:

```
sudo fdisk -l
```
The -l is a small "L".

This will show the partition table on your hard drive, then we can go from there.

---

### Post by Graham Gardner on 2006-08-13
Thanks

Thats seems to have sorted things for now

Graham:)

---


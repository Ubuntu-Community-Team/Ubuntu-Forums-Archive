---
title: "[SOLVED] Xubuntu 7.10 install problems"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by Theo148 on 2008-03-02
Okay, I guess I'll just start from the beginning: about a month ago, a system crash corrupted the registry on my old Windows XP system, so I decided that it was time to try a different OS. I downloaded, burned, and installed Ubuntu 7.10 on my laptop successfully first time, with absolutely no problems. It has run perfectly with only 1 mishap (power outage while updating system files + useless battery) ever since, and in fact it's the system I'm posting from now.

A friend of mine saw me using Ubuntu and decided he would like to try it himself, so he asked me to help him install it. However, when I booted from the install CD, the computer hung at the orange-brown login screen background for several hours. After several tries and a bit of research (which I admit I should have done much earlier), I realised that his system didn't have the RAM to install Ubuntu from the Live CD (or run it with desktop effects for that matter).

So I downloaded the Xubuntu ISO (the md5 checksum was correct), burned it to another CD, and tried to install it. The install worked fine up to the point where the disk needed to be partitioned. I selected the guided option to automatically shrink his NTFS partition, and hit 'forward'. The computer ran for a while, and then suddenly stopped - neither the hard disk nor the CD drive was running. The screen still displayed the Live session and the install wizard, but it was frozen. I left it like that for about 15 minutes, hoping that something would happen, but nothing did and I eventually gave up and shut down the system (the power button wasn't responding, but the laptop model will shut itself down if you hold the power button down for 4 seconds).

After reading up some more, I downloaded PartedMagic (mentioned in [this article]("https://help.ubuntu.com/community/WindowsDualBoot")) and used it to shrink the NTFS partition on the laptop. I booted from the CD again, selected 'largest contiguous free space' at the partitioner, but I ran into the same problem as before - the computer worked like crazy for a while, then froze.

The specs for the laptop I am having problems with are as follows:

Acer Travelmate 4050
Intel Pentium M Processor, 1.60 GHz
250 GB RAM
Toshiba MK4025GAS Hard Drive, 40 GB, ~16 GB free

My experience with Ubuntu has been pretty much flawless up to now, but I'm stumped as to why this is happening. I'm hoping somebody here has a better idea of what's going on than a Linux newbie like me, and can post a solution to this problem.

---

### Post by bikeman01 on 2008-03-02
I too have an Acer Travelmate 4050 and couldn't get it to install 7.10 yet it works fine with 7.10 live cd and installs 7.04 ok.
I read elsewhere on this forum that there are known problems with 7.10 and Acer laptops. Don't know how true this is.
Perhaps someone more in the know can advise.

---

### Post by Josh1 on 2008-03-02
Tried using the alternate installer?

---

### Post by Theo148 on 2008-03-02
Not yet - I'm downloading it now, and will probably give it a shot soon.

---

### Post by Theo148 on 2008-03-04
Well the alternate install went fine, and Xubuntu is now running properly on the laptop.

But I would still appreciate it if anybody could enlighten me as to what might have caused the problem.

---


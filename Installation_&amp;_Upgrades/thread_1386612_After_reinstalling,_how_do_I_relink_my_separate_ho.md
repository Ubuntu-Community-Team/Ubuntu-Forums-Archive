---
title: "After reinstalling, how do I relink my separate /home partition?"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by picante on 2010-01-20
I've looked around at posts about how to do this but it seems most people are not having exactly the same problem as me, and much of the discussion goes well over my head. The story is that I repartitioned my hard drive to create a separate /home partition following [[COLOR="Green"]these instructions[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome"). 

That worked well, but then after playing around with a few things in the advanced Compiz settings, my entire GUI would freeze up after the startup splash. It did the little ubuntu jingle and so on but wouldn't actually load up the desktop. I would've booted into recovery mode and deleted the settings that were messing it all up for me, but pressing ESC during grub did nothing! So as a last effort I reinstalled Ubuntu (Karmic) from the live CD on the first partition only, but I don't know how to make the second partition (with my old /home directory) the normal /home directory. The instructions linked above seem to require having done the whole process of moving the partition (so as to create "old" and "new" dirs, etc.).

So there are really two problems here: 1) How does one restore things to normal when a few too many cheeky moves with the desktop effects turns everything to pot? And 2) How does one reinstall Ubuntu with a separate /home partition?

Any help would be met with very big smiles.

---

### Post by raymondh on 2010-01-20
> **picante said:**
> I've looked around at posts about how to do this but it seems most people are not having exactly the same problem as me, and much of the discussion goes well over my head. The story is that I repartitioned my hard drive to create a separate /home partition following [[COLOR="Green"]these instructions[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome"). 

That worked well, but then after playing around with a few things in the advanced Compiz settings, my entire GUI would freeze up after the startup splash. It did the little ubuntu jingle and so on but wouldn't actually load up the desktop. I would've booted into recovery mode and deleted the settings that were messing it all up for me, but pressing ESC during grub did nothing! So as a last effort I reinstalled Ubuntu (Karmic) from the live CD on the first partition only, but I don't know how to make the second partition (with my old /home directory) the normal /home directory. The instructions linked above seem to require having done the whole process of moving the partition (so as to create "old" and "new" dirs, etc.).

So there are really two problems here: 1) How does one restore things to normal when a few too many cheeky moves with the desktop effects turns everything to pot? And 2) How does one reinstall Ubuntu with a separate /home partition?

Any help would be met with very big smiles.

Hi,

Let me answer #2 first :

When re-installing ubuntu (and you have a separate /home) ... you'll have to choose manual method.  You identify and click to highlight the root partition then, mount (using the dropdown, selecting / ) and format ext3 or ext4 for the new Ubuntu.  Next is to ID and highlight the /home partition ... this time, you MOUNT (/home) but DO NOT FORMAT.

* Formatting, as you know, will erase any data.  By not formatting home and just mounting it ... you retain the data.

Proceed with the install and at the step where you create a username/password, use the same username and password as the existing.

Raymond

---

### Post by picante on 2010-01-21
Thanks so much for replying with such clear instructions! Unfortunately, the first problem persists (but at least that means the second partition is being used as the /home directory, as hoped). I get to the splash screen and then usually get stuck there - sometimes some panels and icons load or I can move the mouse for a few seconds, but then the display inevitably freezes. What's more, Grub only occasionally lets me enter recovery mode, so I guess everything needs to be fixed through the live CD. Right now I'm using the live CD to post, as I don't have any other OS installed. I tried deleting the compizconfig file (in ~/.config/compiz/compizconfig) but it apparently didn't work.

Basically what happened was that I was trying to get the teched-out visual effects (rotating cube, etc.) and everything worked fine until I tried the "reflection" effect feature. Does this extra information help? If I can just return everything to standard visual effects that would be great.

---

### Post by jocko on 2010-01-21
Compiz uses gconf for storing it's settings, so you could try to delete your ~/.gconf/apps/compiz folder.

---

### Post by HugoSerrano on 2010-01-21
You can mount your home directory after the fresh install.

edit the file /etc/fstab and add a line similar to this one:

> /dev/sda3 /home   ext4    defaults   0 2
You can chek wich is the drive by using the following comand:
> sudo fdisk -l

---

### Post by picante on 2010-01-22
Thanks so much to everyone for your help. I tried all of those things and after a reboot, everything is working as it should be. Much appreciated!

---


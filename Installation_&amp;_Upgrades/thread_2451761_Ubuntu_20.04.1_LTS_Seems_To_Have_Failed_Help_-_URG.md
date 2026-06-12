---
title: "Ubuntu 20.04.1 LTS Seems To Have Failed????? Help - URGENT"
date: 2020-10-10
forum: Installation &amp; Upgrades
---

### Post by skyesharica on 2020-10-10
I got the pop up message for the latest Ubuntu LTS version ... and I upgraded from 18.04 to 20.04.1 LTS. But I've got a 'dancing desktop' ... it just alters all the time. I can't do anything much without a clear desktop. Stuff disappears and it rearranges all the time. And other little things are a bit funny, like filtered spam on Thunderbird. Is there any way I can 'back pedal' to the previous version? Or fix this problem? It is extremely important and URGENT.

Thanx in advance.   :popcorn:

---

### Post by sudodus on 2020-10-10
- The method that is best is to restore from the backup that you made just before heading into the upgrading adventure.

- The second best alternative is to use an older backup (if you have no recent backup).

I'm sorry but I don't think there is any back pedal. But before doing anything else, you should backup the still not backed up data files, that you cannot afford to lose.

---

### Post by skyesharica on 2020-10-10
> **sudodus said:**
> restore from the backup that you made just before heading into the upgrading .... OR ... use an older backup

Thanx pal. I aint done no backup ... I've backed up my data recently, except for the odd thing here or there, but I haven't done a Windows-like snapshot of my system to restore to, or backed up my OS ... how green was my cactus, LOL. I don't think I've lost much data. Do you think I have? Do you have any idea why my desktop dances, Word opens funny, spam isn't filtered well etc? WHAT CAN I DO WITH AN UNSTEADY WHEEL ON MY SHIP, brother?  :popcorn:

---

### Post by dragonfly41 on 2020-10-10
> [COLOR=#000000]I work for the feds. I really do.
[/COLOR]An Untouchable.
Try in a guest user account to see if symptoms persist .. or even Live USB.

---

### Post by skyesharica on 2020-10-10
Who's untouchable pleez?
Guest user account is a no go for me, but thanx.
Will I just clean install the new OS on top of the old one ... with [64-bit PC (AMD64) desktop image]("https://releases.ubuntu.com/20.04/ubuntu-20.04.1-desktop-amd64.iso")? I forget coz geeks did my last Ubuntu install ... can I install with a CD?

---

### Post by T6&amp;sfpER35% on 2020-10-10
CD? no 
DVD is better 
in which case yes u can use a disk

---

### Post by skyesharica on 2020-10-10
'Sudodus', you are my friend here. 
Will I just download the [64-bit PC (AMD64) desktop image]("https://releases.ubuntu.com/20.04/ubuntu-20.04.1-desktop-amd64.iso") and clean install again, FROM A CD, on top of the same OS ... so the same OS on top of an old faulty installation?

---

### Post by sudodus on 2020-10-10
> **skyesharica said:**
> 'Sudodus', you are my friend here. 
Will I just download the [64-bit PC (AMD64) desktop image]("https://releases.ubuntu.com/20.04/ubuntu-20.04.1-desktop-amd64.iso") and clean install again, FROM A CD, on top of the same OS ... so the same OS on top of an old faulty installation?

I'm sorry that you have no convenient whole image backup, but I'm glad that you have good backups of your data files. So just look for the most recent [personal] data files and back them up too.

Then, yes, it is a good idea to make a fresh installation from [FONT=Courier New]**ubuntu-20.04.1-desktop-amd64.iso**[/FONT].

- Check that the download was good, now with sha256sum (which is better than the previous md5sum)

- Create a DVD disk or USB pendrive with the system from the iso file and boot from it.

- Make a fresh installation. (This way is much more reliable compared to upgrading from the previous LTS version, where you probably have installed things and added tweaks that can disturb the function of 20.04.1 LTS.)

- Restore (copy back) your [personal] data files from your backups to the new system.

- Install whatever program packages you need when you need them. There were probably lots of programs that you installed long ago, but no longer use. This way you get a much cleaner system compared to an upgraded system.

[hr][/hr]
It is probably both easier and faster to get a useful, and even good system running via a fresh installation compared to trying to fix your 'dancing desktop'.

---

### Post by grahammechanical on 2020-10-10
Can I make a suggestion?

When booting bring up the Grub boot menu and select Advanced options for Ubuntu. Then select a Linux kernel with a recovery mode option. At the Recovery menu select Resume. That should load to the desktop using a basic video driver. If that works you can use Software & Updates>Additional Drivers to search for a proprietary video driver. You will need to be connected to the internet.

If you do get to that basic video driver desktop rebooting from there will load Ubuntu with the standard open source video driver. It all depends what is causing the video problem. The open source driver or the proprietary one.

By the way, the Boot menu Advanced Options should show a list of Linux kernels. As this is an upgrade from 18.04 the older 18.04 kernels should be in the list. You could try loading with that to see if that works. It will be the second or third on the list.

Regards

---

### Post by skyesharica on 2020-10-10
> **sudodus said:**
> I'm sorry  ... your 'dancing desktop'.

Thanx again Sudodus. It's a gr8 reply - at my level.

---

### Post by skyesharica on 2020-10-10
> **grahammechanical said:**
> Regards

Thanx 4 all ur effort Graham ... but that is all far too above my head. You'll get use to us normal folks and low IQ and not so hot maths people ... I don't know one line of programming, LOL.

---


---
title: "System boot badly screwed up."
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by kuantum_fizax on 2008-06-28
Hi all, I seem to have really screwed up my computer... I should probably tell the whole story just in case something is important. I have a thinkpad T60 laptop, in case that's important.

1. I had a windows vista / ubuntu 8.04 dual boot system using GRUB.

2. Got virus on windows, screwed up windows booting. 

3. Used Lenovo recovery partition (Came with my Thinkpad) to try to restore the C: drive. I told it to only touch the C: drive, not my ubuntu partition.

4. It failed during recovery, saying something like "%s failed at recovering hard disk".

5. It seems to have overriten the GRUB boot loader, because now some Intel thing loads. It tells me there are no bootable hard drives. Great... aparently it really screwed up.

6.Okay... so I decide to scrap trying to get windows running. Lets just get my ubuntu back

7. I burn a Desktop install cd for ubuntu, with the goal of first trying to just reinstall grub, and if that doesn't work reinstall the primary ubuntu partition, hoping my home directory partition is still intact.

8. The cd splash screen loads alright. However, it doesn't function correct. Selecting "Try ubuntu without any change to your computer", "Install Ubuntu", "chech memory", or "Chck CD for defects" cause it to freeze. Selecting "Boot from first hard disk" works as expected, sending me back to the intel boot loader.

Please help. If I can't even reinstall ubuntu, how can I recover my laptop?

---

### Post by Pumalite on 2008-06-28
Get Super Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
You can fix your Windows. (try to boot it first) and then reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by kuantum_fizax on 2008-06-28
Okay, looks good... 

Is there any way to get supergrub onto a pen drive without root access? The tutorial seems to think I need it. I have some other linux computers around, but nothing that I have root priviliages on.

---

### Post by Pumalite on 2008-06-28
[http://www.supergrubdisk.org/index.php?pid=7](http://www.supergrubdisk.org/index.php?pid=7)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by kuantum_fizax on 2008-06-28
Okay, I actually found a blank cd and copied an ISO to it.

But it isn't working. Whatever I choose, from recovering linux to reinstalling grub into the MBR, I get:

Error 15: File not found
Booting 'not lucky'

---

### Post by Pumalite on 2008-06-28
If there is a functioning Vista; Super Grub can boot it. If you can't, you might as well save data and start from scratch.

---

### Post by kuantum_fizax on 2008-06-28
That's the problem, I can't seem to start from scratch. I don't really care anymore about using vista. Ubuntu is more important. However, the live cd doesn't seem to work. It freezes if I try to run it. 

Maybe I'll try the alternate install cd...

---

### Post by kuantum_fizax on 2008-06-28
Oh yeah, only one partition is listed. A 7GB windows partition. Unless that is the recovery partition, I don't know what that could be.  So I assume my partition table (or whatever you call it) is screwed up. Is there any way to recover from this?

---

### Post by Pumalite on 2008-06-28
Try a Knoppix Live CD:
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

---

### Post by kuantum_fizax on 2008-06-28
Okay... well I did a md5sum check on the cd... looks like it was burned to incorrectly. Unfortunately, I'm all out of writable cds. 

Since I'm in Switzerland, I'll probably have to wait for Monday to get any more cds. Don't think anything will be open tomorrow. Sigh.

Anyways, thanks for all your time and help.

---

### Post by Pumalite on 2008-06-28
You are welcome. I love Lake Lucerna.

---


---
title: "Error after install to 10.04"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by Micehorns on 2011-03-29
I updated my Ubuntu to 10.04.2 this morning, the install appeared to go smoothly. I restarted to find a message saying "An error occured while mounting /media/JM90-G8", "Press S to skip mounting or M for menual recovery".

I tried pressing the S key and nothing happened, I switched the computer off and tried again, nothing. I have tried it 10 times now (including trying the 'M' key).

If I press the down arrow key I get a more detailed description of the problem. 

"/dev/sda1: clean, 324515/29982720 files, 1254604/119913168 blocks (check in 2 ounts)
NTFS signature is missing.
failed to mount /dev/sda1' : invalid argument,
The device doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a partition? Or the other way around?
Mountall : mount /media/JM90-g8 [718] terminated with the status 12
mountall: filesystem could not be mounted"

Am I right in guessing that this harddrive that isn't loading is one that I mounted and not my main hard drive? If so, I unmounted and disconnected that hard drive months ago :confused:. I tried putting that hard drive back in and loading up, but the error is still there. I seriously do not care for that hard drive at all. The data I wanted off it was taken off ages ago. I'm guessing I'm needing to work around Ubuntu loading without it looking for/trying to mount this hard drive? 

I've googled the problem and i've found very little relating to Ubuntu or having this problem after an install. I'm also a complete novice with Linux, i'm sorry if I've missed anything out in my post. If you need any answers please ask and I'll try my best to reply. Thanks.

Edit : After a few more attempts at restarting the PC, I got a message saying "Your harddrives are being checked for errors, this may take some time", I got 100% and the computer restarted itself and i'm back to the mounting error screen again. It felt so close to actually working there :(.

edit 2 : Sorry for all the edits, i'm just trying to get as much information down as possible. What I find strange is this, when I press S or M, nothing happens but if I wait for the screensaver to come up and press either or these two keys, the screen saver goes at away. At first I was concered that my keyboard drivers may not have installed correctly...but this does'nt seem to be the case. Hmm.

---

### Post by Sean Moran on 2011-03-29
> **Micehorns said:**
> I"Press S to skip mounting or M for manual recovery".

I've had that one from time to time booting into 10.10.  It seems to be due to permanently mounted partitions I've added to the /etc/fstab file using MountManager that have since been reformatted with a new UUID or else deleted.

If you can get past the disk-check with the S key, and wait until you get to the GUI desktop, maybe download MountManager:

sudo apt-get install mountmanager

or else 

sudo gedit /etc/fstab

which is the less obvious way to reset your fstab file so that Ubuntu only looks for extant parftitions with the correct UUID when booting, the future disk checks shouldn't get confused about the contents of your hard disk/s anymore..

It's looking for something on removable media if I remember.  Just a matter of removing it from the fstab, and mountmanager is a nice easy GUI way to fix it,

---


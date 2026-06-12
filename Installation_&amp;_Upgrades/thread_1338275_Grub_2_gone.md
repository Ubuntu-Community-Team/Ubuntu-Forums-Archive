---
title: "Grub 2 gone"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by nexoncore on 2009-11-26
[B]Problem
[/B]Installed Geexbox which corrupted on install which basically left me with a useless from. Deleted partition and now I have no GRUB. I need some way to install just grub, nothign else as my ubuntu installation is intact.

[B]Tried
[/B]1) Using Remastersys backup, but that fails to install GRUB2, giving an error message indicating so.
2) Followed many tutorials for regarding grub-install and mounting drives.

[B]Temporary Fix
[/B]Installed ubuntu 9.10 on a seperate partition, its GRUB2 is allowing me to access my real ubuntu installation. But its not Ideal.


Basically I need a way to Install GRUB on an existing ubutnu partition, ext3

---

### Post by darkod on 2009-11-26
Can this help?
[http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11](http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11)

PS. Are you trying to restore grub or grub2? The above is for grub.
Grub2 is here, item number 12:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by nexoncore on 2009-11-26
Grub 2 and I tried that topic. Nothing worked.

---

### Post by darkod on 2009-11-26
Was there a specific message? That number 12 procedure seems to have worked for a few people.
At which step is it failing?

---

### Post by nexoncore on 2009-11-26
no errors, follow it through but i still have no grub.

Might help if i list some more info.

I have 2 drives., sda and sdb, sdb is purely storage so can be ignored.

SDA has 2 partitions

sda1 = New Ubuntu 9.10 installation ( Used for Loading sda5 )
sda5 = Actual ubuntu installation I used.


I have tried grub-install hd0

Sometimes it comes up saying grub command does not exist
but mostly that device map does not exist, even though it does.

Isnt there a live CD or something, which can just install GRUB2. I dont want one built in with a linux distro because I cant get any working.

---

### Post by darkod on 2009-11-26
You also have the instructions here:
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

Look at 2) Using Ubuntu 9.10 liveCD.

It basically the same procedure but here it's more compact and looks shorter.
There is no command grub-install hd0, I'm confused now. You have to use:

```
sudo -i
mount /dev/sda7 /mnt
mount /dev/sda6 /mnt/boot (only if you have separate /boot partition)
grub-install --root-directory=/mnt/ /dev/sda
```

And when doing the restore use your original installation partitions, the one you are trying to restore. The temporary fix of second ubuntu might have confused things, be careful what you are telling it to restore.

---

### Post by nexoncore on 2009-11-26
Since the Ubuntu I want to use is sda5, would it be

sudo -i
mount /dev/sda5 /mnt/boot 
grub-install --root-directory=/mnt/ /dev/sda

---

### Post by darkod on 2009-11-26
No, the other command.

sudo -i
mount /dev/sda5 /mnt
grub-install --root-directory=/mnt/ /dev/sda

Basically you are mounting sda5 as root (/mnt). And telling grub to install on /dev/sda with root directory=/mnt (=/dev/sda5)

---

### Post by JBAlaska on 2009-11-26
> **nexoncore said:**
> 
Isnt there a live CD or something, which can just install GRUB2. I dont want one built in with a linux distro because I cant get any working.

[Super Grub Disk](http://www.supergrubdisk.org/) will work (Not the old version for legacy grub). Available on CD Image / USB and Floppy

---

### Post by nexoncore on 2009-11-26
> **darkod said:**
> No, the other command.

sudo -i
mount /dev/sda5 /mnt
grub-install --root-directory=/mnt/ /dev/sda

Basically you are mounting sda5 as root (/mnt). And telling grub to install on /dev/sda with root directory=/mnt (=/dev/sda5)

works perfect, thanks

---


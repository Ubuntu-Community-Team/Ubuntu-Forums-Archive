---
title: "Reinstating Grub2 Karmic 9.10 - no stage 1"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by meep_meep on 2009-12-06
Hi all,

I had ubuntu 9.10 installed and then I installed vista x64 afterwards.  I then booted into 9.10 live CD where I went into grub and did

root (hd0,0)
setup (hd0)

but it can't find Stage 1....because I don't have one.  I'm guessing this is the case because this is grub2?  I also dont have a menu.lst maybe because I only had one OS before.

I also tried using startupmanager which generated a menu.lst but only for the live CD and not for my Ubuntu on the harddrive.

Anyway so I went into gparted and tick the flag to make my computer boot into Ubuntu partition.  When it starts up it says that OS is missing....

What can I do?  I want to reinstate grub and have it updated to include vista as well. Any help would be appreciated!

meep

---

### Post by meep_meep on 2009-12-06
Going to try part 12 from this really good post

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

ill be back to update in a mo

---

### Post by meep_meep on 2009-12-06
That didnt work and gave me this error...

```
ubuntu@ubuntu:/dev$ sudo grub-install --root-directory=/mnt /dev/sda1
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly

```

EDIT:  (so I'm going to try this guide [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708))

EDIT: I looked that that guide and it told me to do the same thing again so I still have the same problem

---

### Post by darkod on 2009-12-06
You used /dev/sda1 in your command grub-install. That's a partition and the warning is it's not recommended to install it there. You should use /dev/sda, the device.

sudo grub-install --root-directory=/mnt/ /dev/sda

If you have 9.10 clean install then you have grub2 and you should follow procedures for grub2 not grub1. Using Startupmanager to create menu.lst can't help, only confuse things. Grub2 does not use menu.lst.

---

### Post by meep_meep on 2009-12-06
thanks darkod you are a legend!

thanks a lot.  If i'm ever in bulgaria I'll buy you a beer :D

---


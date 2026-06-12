---
title: "Kernel panic -&gt; unable to mount root fs on unknown block"
date: 2005-07-28
forum: Installation &amp; Upgrades
---

### Post by wizer on 2005-07-28
My apologies for asking this

I wanted to upgrade to Linux 2.6.12 because it will solve several of the prob I'm facing on my laptop (Fujitsu S7021) including sound.

following the HowTo [http://ubuntuforums.org/showthread.php?t=43065&page=10&pp=10&highlight=unable+to+mount+root](http://ubuntuforums.org/showthread.php?t=43065&page=10&pp=10&highlight=unable+to+mount+root)
 (excellent, by the way), I got the new kernel running but bec of a mistake in config, did not have networking support.  I removed it using synaptics & after reconfig, tried to get it run it.  This time, I got the panic message

I have tried various advice given in the post mentioned above but am still getting get Kernel panic.  I have a feeling it may be linked to GRUB bec I saw some posts about it messing up their Windows XP.

(I should mention that I am exploring migration from Windows so am on Dual Boot with WinXP.  XP was installed first so I think block 0,0 is prob in NTFS format
/dev/sda1 -> XP
/dev/sda2 -> FAT format Data share disk
/dev/sda3 -> swap
/dev/sda4 -> Linux
)

Luckily I am still able to boot into my original Hoary but I would appreciate it if someone has any idea how I can get back the new kernel

---

### Post by wizer on 2005-08-01
ok. after days of trial & error, found the prob. apparently Ubuntu requires cramfs ROM support in the kernel.

---

### Post by savimonty on 2005-08-08
Same panic...heres a case : 
Well i already have ubuntu installed with kernel 2.6.10-5-386

i installed fedora4 on another partition but i used the same swap partition which was formerly being formatted by ubuntu and now by fedora4. Now does formatting the same swap partition  by fedora cause this kernel panic.....saying that it could not mount root fs into an unknown-block(0,0)...!!!

well this is how my HDD looks

hda1  vfat       # windows2k (/)
hda2  reiserfs # ubuntu (/)
hda3  ext3      # fedora4 (/)
hda5  vfat       # (/MyData)
hda6  swap     # first created and formatted by ubuntu5 then by fedora4.
hda7  ext3       # lfs

thanks in advance if someone helps me out of this panic....

Savio

---


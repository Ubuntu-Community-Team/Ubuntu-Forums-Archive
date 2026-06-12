---
title: "GRUB MBR relocation problem"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by yookoala on 2009-12-09
Hello.

I'm using Ubuntu 9.10
When I installed my system, I installed my MBR to /dev/sda
But I actually need to install it on /dev/sda3

I know I can run grub-install afterward.
But I'm not quite sure if this is done.
For example, if I update my kernel version, will GRUB update my /dev/sda MBR?
How can I avoid that? Can I set GRUB's default location to /dev/sda3?

---

### Post by darkod on 2009-12-10
> **yookoala said:**
> Hello.

I'm using Ubuntu 9.10
When I installed my system, I installed my MBR to /dev/sda
But I actually need to install it on /dev/sda3

I know I can run grub-install afterward.
But I'm not quite sure if this is done.
For example, if I update my kernel version, will GRUB update my /dev/sda MBR?
How can I avoid that? Can I set GRUB's default location to /dev/sda3?

If you do that you are aware that you will not be able to call grub2 on /dev/sda3 directly right?
I think you can install it with grub-install and have to use -f argument to force it install on partition instead of the MBR. Something like:
sudo grub-install -f /dev/sda3

---

### Post by yookoala on 2009-12-10
But how about software update (apt-get)?
Will any update to grub package ruin my MBR (/dev/sda) instead of maintaining my installation to /dev/sda3?

---

### Post by mikewhatever on 2009-12-10
When grub gets updated, it involves files in /boot/grub, and not the mbr, so you are safe to follow the plan.

---

### Post by darkod on 2009-12-10
> **yookoala said:**
> But how about software update (apt-get)?
Will any update to grub package ruin my MBR (/dev/sda) instead of maintaining my installation to /dev/sda3?

You need to explain more clearly what are you trying to achieve. Running update-grub does not ruin your disk MBR.

---

### Post by presence1960 on 2009-12-10
I think the OP is using terminolgy incorrectly. The MBR is not located in a partition, it is located at a Main Boot Record area in front of the first partition of a hard disk.

I believe he is referring to GRUB being installed to the boot sector of a partition (sda3) rather than installed on MBR of sda.

---

### Post by efflandt on 2009-12-10
I know that you can boot with grub or grub2 in /dev/sda3, because I am doing that.  That will work if sda3 is a primary partition, but not sure it will work if sda3 is an extended partition.

You need to restore the mbr of your hard drive to a standard mbr, or that grub may get confused.  You can do that with Windows setup disk in recovery console (**fixmbr** command), or there is a Linux package you can install from Synaptic appropriately called "mbr".  If you install that see **man install-mbr** in a terminal.

Then you need to mark sda3 as the boot partition so the standard mbr can find grub.  If you do everything properly, **update-grub** while running from the system you installed grub from should work properly.

For example my system has standard mbr with grub2 on sda3 configured from sda6, and kernel updates worked properly from sda6.  I think kernel updates on sda3 left grub alone (did not update grub menu).  I could still boot previous sda3 kernels, but had to update-grub from sda6 before it picked up a new sda3 kernel. 
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         619     4679608+   b  W95 FAT32 (HP Recovery)
/dev/sda2             620       17194   125307000    7  HPFS/NTFS (WinXP Home)
/dev/sda3   *       17195       21366    31540320   83  Linux (32-bit Ubuntu 9.10)
/dev/sda4           21367       25841    33831000    5  Extended
/dev/sda5           21367       21669     2290648+  82  Linux swap / Solaris
/dev/sda6           21670       25841    31540288+  83  Linux (64-bit Ubuntu 9.10)

```

---

### Post by meierfra. on 2009-12-10
> 
Will any update to grub package ruin my MBR (/dev/sda) instead of maintaining my installation to /dev/sda3? 


Yes. During updates of  the "grub-pc" package,  "grub-install /dev/sdX"  is executed.  But one can use 

```
sudo dpkg-reconfigure grub-pc
```

to select for which hard drive "grub-install /dev/sdX" should be run. In your case you should  deselect all the hard drives, so that "grub-install" does  not run when "grub-pc" is updated.

Also  be aware that "core.img" will move during kernel and grub updates. So you will have to run  "grub-install -f /dev/sda3" manually after each such event.

---


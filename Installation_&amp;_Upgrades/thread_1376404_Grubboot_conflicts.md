---
title: "Grub/boot conflicts"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by gotanothergrot on 2010-01-09
I have a Wubi install of Ubuntu 8.04.01 LTS upgraded online to Ubuntu 9.10 in the windows/vista partition.

I installed openSUSE 11.2 from magazine disk

The new openSUSE boots, openSUSE, windows/vista but not Ubuntu, although its listed there, 

I get:  busybox v1.1.3 (initramfs) ect. when i try to boot Ubuntu

---

### Post by gotanothergrot on 2010-01-09
I would like to put Ubuntu in its own partition and delete openSUSE If possible.

---

### Post by darkod on 2010-01-09
openSUSE will not be able to boot wubi because wubi is working virtually inside windows, not on a dedicated ubuntu partition. If you want to delete SUSE and install proper ubuntu on its own partition, first boot your windows and remove wubi from add/remove programs like any windows application. Then boot with the ubuntu cd, Try Ubuntu option, open Gparted and delete the openSUSE partition(s). That will create unallocated free space.
Then boot with the ubuntu cd again, select Install Ubuntu and tell it to use Largest Available Free space which should set up ubuntu on the unallocated space you created deleting SUSE. The installer should also install grub2 on the MBR of your hdd which is all you need to dual boot your windows and ubuntu.

---

### Post by gotanothergrot on 2010-01-09
Thanks darkod,  I need to order some kind of storage device for all _my data thats currently in Ubuntu _. I only have one dvd drive can I burn it to disk before using the live DVD?

---

### Post by darkod on 2010-01-09
Yes, you can burn all your data on DVDs before deleting it. If you need more than one DVD just burn them one by one.
When you are sure you have all the data copied, and you have checked you can open the data from the DVDs, remove the wubi install, delete the SUSE partition(s) and install ubuntu on the unallocated space from the deleted SUSE partition(s).

---

### Post by gotanothergrot on 2010-01-09
> **darkod said:**
> Yes, you can burn all your data on DVDs before deleting it.  

I need all my music Mail Pictures and video's, Do I copy them from within vista?

thanks

---

### Post by darkod on 2010-01-09
If you have any data within ubuntu/wubi you want to keep, you have to copy it because it will be gone by removing wubi.
The data from vista should remain intact but it is good practice to have a backup anyway. Otherwise removing wubi and installing full ubuntu will not delete vista of course. Your docs/music/videos in vista should remain untouched.
But make a backup anyway. Your vista data should be burned from within vista, that's easiest.

---


---
title: "Dual booting Ubuntu 8.10 and Windows Vista"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by darksoul7 on 2008-10-30
Hey guys,

I recently got a new computer which came packaged with Windows Vista Home Premium. I'd like to set it up to run Ubuntu and Vista. 

Now, I've successfully done Dual Boots with Windows XP, but I've heard that Vista can be tricky. 

I've already partitioned my disc via the MMC in Vista so I have 40GB on a RAW partition ready for the Ubuntu install. 

My question is this... is there anything special I need to do to make sure that both OS's start properly? Will GRUB work with Vista? 

I don't have any disks to re-install Vista, only a factory image partition, so if I can avoid any Vista reinstalls, I'll be ecstatic. Worse come to worse, I can always get rid of Vista altogether and install XP for the few Windows programs I use. 

In any case, please let me know if you have any ideas. I don't want to start toying with it until I get some info from people with more expertise.

Thanks!

---

### Post by Gigabit on 2008-10-30
Yesterday I installed Ubuntu onto its own partition with Vista on the other partition. I didn't need to do anything special I just installed Ubuntu on there and then rebooted and Grub had both the new Ubuntu 8.10 and Vista listed. 

To be honest I have not tried to boot up to Vista so I don't know if there is a problem getting it going but, it is listed in grub.

---

### Post by logos34 on 2008-10-30
here you go:
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

good luck and enjoy ubuntu

---

### Post by hyperdude111 on 2008-10-30
Grub fully recognises vista and you will need nothing special to dual boot.

If you want to dual boot with xp I used this guide

[www.apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](www.apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)


~hyper~

---

### Post by lemming465 on 2008-10-30
Since you aren't using bitlocker, just install ubuntu normally and let GRUB take over the MBR.  If you had vista ultimate/enterprise and were using bitlocker, you'd need to muck around with bcdedit in Vista to boot Ubuntu, because bitlocker won't tolerate tampering with the MBR.

---

### Post by johanhartman on 2008-10-30
I used [EasyBCD]("http://neosmart.net/dl.php?id=1") to configure the Vista bootloader, I reckon it might be safer (I've had problems with grub)

---

### Post by darksoul7 on 2008-10-30
As I said before, I have dual booted XP and Ubuntu, so I'll just follow the same steps with Vista as I did with XP.

Should be rather simple since I already made the partition.

Oh and thanks to all for the replies. 

One more thing, the 64 bit version of Ubuntu will work with 64bit Intel processors, right?

---

### Post by logos34 on 2008-10-30
> **darksoul7 said:**
> 
One more thing, the 64 bit version of Ubuntu will work with 64bit Intel processors, right?

Yes.  Which is always why I have wondered why they label the x64 iso "amd64" (???)

---

### Post by darksoul7 on 2008-10-30
Totally. It should just say 64bit in my opinion, but hey! As long as it works :D

---

### Post by lemming465 on 2008-10-30
There are a lot of 64 bit processors out there.  IBM has several, MIPS had them, DEC alpha's were 64-bit, Sun has them, etc.  Intel's original ploy was to make a non-x86 "Itanium" 64-bit architecture, reserving the x86 market for lower power, slower 32-bit chips only.  Itanium has some very cool features (guard bits, explicit cache loads), but it was late, buggy, the yields sucked, and it ran emulated x86 code very sluggishly at a time when there was no native binary code from 3rd party vendors.  AMD responded by enhancing the x86 architecture with 64-bit extensions, better virtual memory page tables, and more registers, and started selling Opterons like hotcakes.  Intel had to eat crow and borrow AMD's extensions to stay in the game.  So the 64-bit variant of x86 is usually called either "amd64" (because AMD invented it) or "x86-64".  The Itanium is usually called "ia64", for intel architecture 64-bit.

---


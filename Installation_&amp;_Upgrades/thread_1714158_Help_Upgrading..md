---
title: "Help Upgrading."
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by ayrrow on 2011-03-25
Hey all,

I'm having difficulty upgrading from 6.06lts to 10.10. 

I have downloaded and burnt a cd, however it freezes on any option from the boot menu. I've tried the various options to no avail.

So i then tried a frugal install using unetbootin however when I try bootin through that using the 10.10 iso it comes up with this
```
root (hd0,0)
file system type is ext2fs, partition type 0x83
kernel /boot/ubnkern
Error 15: File not found

press any key to continue.
```

And before anyone asks, no my computer cannot boot from a usb. I have tried.

---

### Post by Hedgehog1 on 2011-03-25
The install may be choking on the ext2 files system.

You will likely have to back up your data and do a clean install of 10.10



***The Hedge***

:KS

p.s. How much RAM does your computer have?  What is the video card?

---

### Post by ayrrow on 2011-03-25
> **Hedgehog1 said:**
> The install may be choking on the ext2 files system.

You will likely have to back up your data and do a clean install of 10.10



***The Hedge***

:KS

p.s. How much RAM does your computer have?  What is the video card?

Hi, I am trying to do a clean install, but i'm having all of these errors =(

I have a m200 portege with 1.5gb of ram and a 32mb nvidia card.

---

### Post by Sef on 2011-03-25
Instead of installing go down to "Check Disk for Errors" (or something similar.) I suspect that you have a bad disk or the data on the disk is bad, so try reburning the iso. Also, did you md5sum the iso?

---

### Post by Hedgehog1 on 2011-03-25
> **ayrrow said:**
> Hi, I am trying to do a clean install, but i'm having all of these errors =(

I have a m200 portege with 1.5gb of ram and a 32mb nvidia card.

OK - I think the installer needs to not see the ext2 file system.

Can you run gparted from the LiveCD, and setup a new partition layout with ext4?

Do you need some guidance on how it would be best to layout your drive?  If so, please let me know the drive size (and if you dual boot).

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-25
Sef has a good point - is this happening right when you are booting off the CD?

If so, the CD is likely a bad burn or a damaged ISO.

---

### Post by ayrrow on 2011-03-25
I think I will try with a new cd. And I'll get back to you all. I can't even  run check for disk errors without the boot menu freezing.

Thanks!

---

### Post by kansasnoob on 2011-03-25
> **Sef said:**
> Instead of installing go down to "Check Disk for Errors" (or something similar.) I suspect that you have a bad disk or the data on the disk is bad, so try reburning the iso. Also, did you md5sum the iso?

+1!

When booting the Live CD, right after the system/BIOS screen passes, you'll see the purple screen with two small images at the bottom (a stick man and what's supposed to indicate a keyboard). When that screen appears you have 3 seconds to press any key and then you'll have to select language.

After that you can select boot options. Start with "Check disc for defects". That can take several minutes and if it's OK it'll say, "no defects found, press any key to reboot".

---

### Post by Hedgehog1 on 2011-03-25
Always happy to help folks 'down-under'.

Does that mean I live 'up-above'?!!??!

***The Hedge***

:KS

---

### Post by kansasnoob on 2011-03-25
> **ayrrow said:**
> I think I will try with a new cd. And I'll get back to you all. I can't even  run check for disk errors without the boot menu freezing.

Thanks!

Verify the iso:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Then burn it right:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---


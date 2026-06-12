---
title: "Install, but not boot"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by Eatrice on 2007-04-14
My PC spec is below:
CPU: AMD Athlon 64 X2 (cant remeber the speed)
MB: Biostar T550
RAM: 2 x 512 DDR800
HD: 2 x 80GB SATA (running on hardware RAID1, and installed Win XP)
       1 X 250GB SATA (Partitioned to 1, 80GB ext3
                                                        2, 160GB NTFS
                                                        3, 2GB swap)

I downloaded the ubuntu 7.04 beta AMD and 6.10 AMD version. 

I set my bios to boot from the 250GB drive, because ubuntu will not see the RAID drive.
When I booted from both CD without any optiion. It said something worng with Kenrel and didnt want to boot from live CD. 
If I used the option "acpi=off", then it allowed to boot the live CD and run installation. 
I set the installation to install in the 80GB ext3 drive.

After it restarted (still boot from the 250GB), the PC just hang in a black screen.

Please Help:( 

2nd Question - What is the acpi=off for?

---

### Post by TheWizzard on 2007-04-14
please don't try the 7.04 beta if you're new to linux.

you can try to download ubuntu with the x86 kernel (standard). this kernel is more generic and will probably work.

---

### Post by Eatrice on 2007-04-14
Thx for answer my question!

I tried to install with the 6.10 x86 CD. I give me the same kenrel problem and didn't want to boot with the live CD.

Then I tried the "live acpi=off", it jumped to the momery test screen and it was just running test for 1 and half hour. 
So I finally restrarted my PC and just used the "acpi=off", then it said something like file checksum fail and didnt boot.

Actually which version of ubuntu should I use.
I have the 6.10 desktop for PC, 6.10 AMD64 and 7.04

---

### Post by bulldog on 2007-04-14
I should go for the 6.10 desktop cd [32 bit version]
Burn the ISO on a low speed to avoid errors,** and check the cd after burning and before installing**

When you boot the cd,you'll see in the menu an option to check the cd for errrors,just do so.

---

### Post by Eatrice on 2007-04-14
Thx BullDog!

I tried the check the cd for defer option. It still gave me the kenrel panic error.

Did I do something wrong in the process? Do I need to set the ext3 partition to be active?

I tried to install the all versions. The PC just didn't boot. 

I was successfully installed on an old celeron PC and on an AMD 64bit PC with dual boot. I don't understand why it doesn't work this time.
_____________________

I tried to use this method to reburn the ISO again:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
But I still get the same result, Pls Help!

---

### Post by bulldog on 2007-04-14
Can you disconnect the RAID configuration?
Maybe ubuntu can't understand this for some reason.

If you do disconnect the raid,and you select the line which boot ubuntu in GRUB,hit the  'e' key to edit the line.
Edit the line so you boot your ubuntu partition (hd0,0) if it's the first partition or (hd0,1) if it's the second one.
Read the instructions in your screen,I think you can hit the  'b' after editing but I'm not sure.

---


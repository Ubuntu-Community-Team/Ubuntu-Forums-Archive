---
title: "uninstall ubuntu sidebyside, without losing windows files"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by miko sims on 2012-01-21
Hey guys, 
 
My first time posting as I have a little problem on my hands. I currently use windows for all my autocad work and ptw32 work and much more important stuff, sooo, I installed ubuntu side by side with windows. This is perfect and working fine..
 
I want t uninstall ubuntu and install backtrack 5 over its place, how do this???
 
I thought f deleting the partitions I made while in windows, but then will the grub mess everything up on startup if i restart??? or do i just delete partitions while in windows then insert my usb containg backtrack right away and let it do its thing.... 
 
 
MOST importanly I cannot lose information on my windows drivers, or partions. To much valuable info on that half.. 
 
 
any help is greatly appreciated:D

---

### Post by darkod on 2012-01-21
There are many options.

1. Use the windows cd to install/repair windows bootloader to the MBR. That will make windows boot regardless of ubuntu. Then just delete the ubuntu partitions.

2. Boot with ubuntu cd in live mode, open Gparted and delete the uubntu partitions. Why do you care whether the computer can boot after that or not, if you continue with the BT install right away? Even if the computer doesn't boot because you deleted the ubuntu partition, simply boot with the BT usb and start the install. You need to boot from the usb to install anyway.

3. Simply start the BT install without deleting the ubuntu partitions. In the partitioning step, use the manual option (should exist like in ubuntu), delete the partitions of ubuntu and create partitions for BT.

Basically, you can do it in a number of ways, depending what is more comfortable for you.

---

### Post by miko sims on 2012-01-21
First off, thank you for the quick response!! 
 
The third option sounds easy, and I will try that, i will insert my BT usb, restart my computer and go from there. 
 
Also, I created empty partiones for ubuntu in terminal by splitting my windows drive in half. This shouldnt matter right? .... well we'll see very soon

---

### Post by miko sims on 2012-01-22
worked perfectly thanks you ! working on wifi problems now, but os is running perfectly!!!!

---


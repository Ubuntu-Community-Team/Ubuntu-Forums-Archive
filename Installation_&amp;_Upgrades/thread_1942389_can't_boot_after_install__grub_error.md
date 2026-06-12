---
title: "can't boot after install / grub error"
date: 2012-03-17
forum: Installation &amp; Upgrades
---

### Post by mgh24 on 2012-03-17
So I installed Ubuntu 11.10 on a previously made ext4 partition that I was dual-booting with Linux Mint.  Install went OK, but now PC will not boot to anything!  Cannot get past the Grub screen, just get 'no such device.... Entering rescue mode'
But then is just hangs there with blinking cursor.

What can I do now?  I tried booting off my Windows installation CD in RE mode, and tried startup repair, but it does not detect any problems.

What can I do to fix this?

Thanks for any help.

OK.  Found a link to a program called Boot Repair.  Downloaded the ISO image and burned it to a disk.  Booted off of it, used the 'repair' option, and I am good to go.

I would highly recommend this program!

[https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

---

### Post by coffeecat on 2012-03-17
Let's get an overview of your system.

Boot up the live Ubuntu CD or USB, choose 'try Ubuntu' to get to the live desktop, ensure you are connected to the internet, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---


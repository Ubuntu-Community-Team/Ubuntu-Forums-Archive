---
title: "Ubuntu refuses to boot after forced shutdown"
date: 2022-10-05
forum: Installation &amp; Upgrades
---

### Post by admiralcanaris on 2022-10-05
So basically what happened was that I accidentally fried my computer after running Minecraft (I was bored), and after force shutting it down, Ubuntu now refuses to boot. I can access the GRUB menu, but selecting the "Ubuntu" option just leads me to a blank screen. I have tried [https://askubuntu.com/questions/1155671/ubuntu-doesnt-boot-properly-after-forced-shutdown](https://askubuntu.com/questions/1155671/ubuntu-doesnt-boot-properly-after-forced-shutdown) and used Boot Repair's Recommended Repair, but they did nothing to fix my issue. It would be extremely helpful if anyone could help resolve my issue, since I have quite a few projects which I did not back up.

BootInfo Summary: [https://paste.ubuntu.com/p/RhkzZXGDKp/](https://paste.ubuntu.com/p/RhkzZXGDKp/)

Thanks in advance.

---

### Post by yancek on 2022-10-05
A method that should work on Linux so you do not have to shut down with the power button is to simultaneously hold down the alt+prtsc keys.  While doing that consecutively type in the following letters:  reisub  That should reboot.

Did you try the Advanced options for Ubuntu on the Grub screen?
Is the screen blank or do you see a grub prompt (grub>) or grubrescue or a blinking cursor in the upper left?

Your boot repair shows you also have windows installed.  Are you able to boot windows?  Are you able to boot either windows or Ubuntu from the EFI boot options? Were you running minecraft on Ubuntu? 

I don't see any obvious problem with boot repair.  Do you get any warning or error messages when you run boot repair?

---

### Post by ajgreeny on 2022-10-05
Forced shutdowns can occasionally also cause filesystem damage so you may need to boot to your live Ubuntu system from the USB that you used to install the system.

Choose the ***Try Ubuntu*** option and when you get to the desktop open a terminal and run command ```
sudo e2fsck /dev/sda2
```
Do not just copy  /dev/sda2 that I show but use your own root partition device name which looks as if it could be **/dev/nvme0n1p2** but you can check that from the live system with **sudo blkid**.

That may show some filesystem faults and offer to repair them.

---

### Post by admiralcanaris on 2022-10-05
Boot repair shows no problems and I am able to boot Windows from the EFI boot options. After selecting Ubuntu, however, I'm just met with a screen with the Dell logo (the manufacturer of my laptop). And yes, I was running Minecraft on Ubuntu which caused it to crash.
I'm suspecting the file system might be damaged, but all methods I've tried so far don't work.

---

### Post by yancek on 2022-10-06
>  I'm suspecting the file system might be damaged, but all methods I've tried so far don't work. 		

Not knowing what you have tried, I'm posting a link to a site which has a thorough explanation with examples of using fsck.

I'm suspecting the file system might be damaged, but all methods I've tried so far don't work.

---


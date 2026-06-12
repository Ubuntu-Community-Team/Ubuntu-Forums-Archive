---
title: "boot repair for dual boot question"
date: 2013-07-13
forum: Installation &amp; Upgrades
---

### Post by lukew101 on 2013-07-13
Hi, I recently got a new computer, Dell Inspiron with Windows 7 64 bit. I am trying to install Ubuntu Precise Pangolin 64 bit to dual boot with the windows.  I installed it once, but the computer still automatically booted to windows.  I re-installed hoping that would fix the problem, but it still booted directly to windows.  I got boot-repair which gave the following url log:

[http://paste.ubuntu.com/5872073/](http://paste.ubuntu.com/5872073/)


Does anyone have any advice on how to get it to give me the grub menu at startup so I can choose between windows and ubuntu?

Thanks,
Luke

---

### Post by papibe on 2013-07-13
Hi lukew101. Welcome to the forum ):P

The bootloader that Ubuntu uses (grub) is not installed.

You can installing itusing your installation media as a Live CD/USB, and using the Boot-Repair. Here are the detail steps:[ Boot-Repair tutorial]("https://help.ubuntu.com/community/Boot-Repair").

Pressing **'Recommending Repair'** should do the trick.

Let us know how it goes.
Regards.

---

### Post by lukew101 on 2013-07-13
I ran it and it gave me this url log:

[http://paste.ubuntu.com/5872259/](http://paste.ubuntu.com/5872259/)

I'm going to reboot and see if it worked.

---

### Post by lukew101 on 2013-07-13
That worked, it now gives me the grub screen and both windows and ubuntu boot correctly.  Thanks for the help.

---

### Post by papibe on 2013-07-13
:D Glad you worked it out.

BTW, now the report says grub is installed:
>  => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
When you have the chance, please mark the thread as SOLVED ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how).

Regards.

---


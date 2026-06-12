---
title: "Wubi freezing"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by smalvarez on 2011-06-17
Hi my friend has a Asus Eee PC and we where doing a windows installation and it kept freezing at the point it said "downloading information on installation file."

So we then sign on to the free wifi where we are at and try again, same thing. Keep in mind wubi is still frozen, yet when we run it again it allows us to uninstall and try again. Didn't work, still freezes.


What do you think is the problem? Is there a way to skip this step?

Also, when we ran to try out ubuntu from the usb boot menu, linux was working fine. Can we install linux without partitioning the HD through usb bootable?

Thanks!

---

### Post by Rubi1200 on 2011-06-17
Hi and welcome to the forums :-)

Correct me if I am wrong, but if you have Ubuntu loaded on a USB stick and can try it like that what is the problem with installing Wubi?

Are you saying that Wubi tried to download the ISO image again?

If that is the case, you can place the ISO image and wubi.exe in the same folder and then run the executable file. This should help solve most problems.

Finally, just to be clear; if you want to install Ubuntu (or any other version of Linux) other than via something like Wubi then you will need to partition your hard-drive.

Here is a guide I recommend you start reading:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

If you have any questions, feel free to ask.

---

### Post by smalvarez on 2011-06-17
No,

You can boot straight from usb if you want to create a partition or do a live cd. However if you just want a windows installation it freezes at that part I mentioned before.

---

### Post by Rubi1200 on 2011-06-17
As I mentioned before, the recommended solution in such a situation is to place the wubi.exe and downloaded ISO image in the same folder on your Windows installation and then run the executable.

Make sure you have the right desktop ISO version (Desktop CD version) and wubi.exe:


> For 10.04 use [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/) 

For 10.10 use [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/) 

For 11.04 use [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)


---


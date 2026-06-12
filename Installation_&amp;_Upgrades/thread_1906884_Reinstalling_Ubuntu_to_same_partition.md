---
title: "Reinstalling Ubuntu to same partition"
date: 2012-01-10
forum: Installation &amp; Upgrades
---

### Post by robhol111 on 2012-01-10
Recently, my Ubuntu installation was messed up when the computer crashed during an upgrade. I therefore need to reinstall Ubuntu from scratch, and have made USB stick for the latest version. However, I am unsure about what to do for the partitioning part of the installation. 

My computer is set up as a dual boot with both Ubuntu and Windows 7. I get to the point where the installer says I have multiple OSs installed, and asks whether to install alongside, erase the disk, or something else. 

I assume I need to select something else, and can identify the Ubuntu partitions in the screen that shows up (an ext4 partition at /dev/sda5 and a swap partition at /dev/sda6), but it is not clear to me what I need to do in this screen. I want to use the same partitions I had Ubuntu installed on before. What am I meant to do here? Thanks in advance.

---

### Post by nothingspecial on 2012-01-10
Choose the ext4 partition (/dev/sda5)

Right click it to edit it.

Choose to use it as an ext4 journaling file system.

Choose to format it.

Give it a mountpoint of /

The installer should recognise your swap partition but check it is recognised as swap space if you like.

**[COLOR="Red"]DO NOT TOUCH THE OTHER PARTITIONS[/COLOR]**

That's it.

Except for backing up anything you don't want to loose. Partitioning drives can go wrong.

---

### Post by robhol111 on 2012-01-10
Thanks for the help; the installation appears to have worked.

---

### Post by nothingspecial on 2012-01-10
Great :)

Next time you solve your issue on the forums, use "Thread Tools" at the top of the page to mark your thread as solved.

(I've done it for you this time ;))

---

### Post by ON-F on 2012-01-12
Thanks a lot, I reinstalled my Ubuntu using your instructions and now it works better than ever :)

---


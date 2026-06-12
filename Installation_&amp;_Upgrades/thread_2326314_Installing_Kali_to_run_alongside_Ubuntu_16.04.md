---
title: "Installing Kali to run alongside Ubuntu 16.04"
date: 2016-05-30
forum: Installation &amp; Upgrades
---

### Post by chris331 on 2016-05-30
I am having difficulty with installing Kali.
I want to run it alongside Ubuntu 16.04, which I have already installed as the main and only OS currently.
My problem right now is trying to shrink my lvm2 partition so  that I can create a swap partition, as well as make room for the new OS.
I have 500Mb space.
Here is a picture of my HDD's filesystem, as given by Gparted:

edit: deleted as inline and moved to attachments


I boot from a live USB, run Gparted, and try to shrink the sda5 partition, given here:


edit: see above


I deactivate/unmount the partition, and there is no key or busy icon next to the partitions that would indicate I am not allowed to resize them, but when I try to, the window pops up, but I am disallowed from changing anything.  Here is a picture of the Gparted resize window for my sda5 partition:



edit: see above


As you can see I have 0.0 MiB space preceding the partition, which is my guess as to why I can't resize it.  However, I really don't know why.  If this is the reason, what do I do next, and what are my options?  
Thank you all for taking the time to read this, and help me 
=)

---

### Post by oldfred on 2016-05-30
Please attach screen shots, not post in line.
Easy to add screen shots with the Forum's advanced editor and the paperclip icon. Post #4
       [http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098) 
    

I do not know LVM, but you only use gparted on the physical partition, not the logical partition.
You have to use LVM tools.
But the advantage of LVM is only when it manages the entire drive other than /boot.
I would then think you would install kali inside the LVM.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

### Post by chris331 on 2016-05-30
> **oldfred said:**
> Please attach screen shots, not post in line.
Easy to add screen shots with the Forum's advanced editor and the paperclip icon. Post #4
       [http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098) 

I do not know LVM, but you only use gparted on the physical partition, not the logical partition.
You have to use LVM tools.
But the advantage of LVM is only when it manages the entire drive other than /boot.
I would then think you would install kali inside the LVM.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

 I edited my original post to reflect the forum guidelines for posting pictures =)

Thank you so much!  This is exactly the advice I needed.  Cheers!

---


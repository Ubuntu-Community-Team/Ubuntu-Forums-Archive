---
title: "USB need advice"
date: 2013-03-07
forum: Installation &amp; Upgrades
---

### Post by robin 123 on 2013-03-07
Hi,
I'd like to ask you what you think is the best solution. I want to have a working USB stick with Ubuntu 12.04, fully customizable, upgradable, with Gnome Classic as the default DE and other applications I need. I suppose a persistent Live USB is not the best option. But then I want to retain the ability to install the complete customized system from the USB to a desktop computer. Or to 50 of them.
How would you do this?
Thank you for answers

---

### Post by ajgreeny on 2013-03-07
If you want to use it as a way of installing Ubuntu I don't think you have any other option than to use a persistent live USB setup.  If the USB drive is big enough, you can use a separate ext4 partition instead of the usual casper-rw persistence file, which is limited by the fat32 filesystem to 4GB.  Using a partition gives you the option of a partition as large as the remaining space on your live USB.

See:  [http://ubuntuforums.org/showthread.php?t=1910412](http://ubuntuforums.org/showthread.php?t=1910412)
[http://ubuntuforums.org/showthread.php?t=1629477](http://ubuntuforums.org/showthread.php?t=1629477)

Remember that any changes you see when using the persistent live USB, eg your classic desktop, will not be carried over to the installations made using that same USB which will be standard vanilla Ubuntu.

---

### Post by robin 123 on 2013-03-07
> **ajgreeny said:**
> 
Remember that any changes you see when using the persistent live USB, eg your classic desktop, will not be carried over to the installations made using that same USB which will be standard vanilla Ubuntu.

That's the reason I can't use a live USB then. So is there another option how to fine-tune a system and then install it's copy to different computers?

---

### Post by ibjsb4 on 2013-03-07
There is Remastersys, but I do not use it.  So maybe someone else can tell you about it.

[http://www.remastersys.com/](http://www.remastersys.com/)

What i do use to copy a system from one computer to another is Clonezilla.

[http://clonezilla.org/](http://clonezilla.org/)

I do not have 50 computers laying around :) but clonezilla also has the ability to clone up to 40 computers.

---


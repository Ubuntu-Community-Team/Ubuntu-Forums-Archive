---
title: "Ubuntu on a Removable Hard Drive Shared Between two PC's"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by deepee_oz on 2008-02-05
Hi

I would like to be able to use a 32bit Ubuntu Gutsy installation on a removable SATA hard drive on two different PC's. One is at home and one is at the office.
I have read posts in the forums about people who have been amazed at the capablity of Ubuntu to probe the hardware on a very different machine than which it was originally installed and adapt to the new environment.

I have tried this but X windows returns an error on boot and won't start from the consol.

I don't want to change my config file manually each time I swap the drive to the other machine.

Given that the Live CD does such a great job of probing the hardware and configuring X for any PC, is there an easy way to use this capability on a hard disc installation so it will boot on just about anything?

Thanks
DP

---

### Post by Scavok on 2008-02-05
Perhaps by editing GRUB's menu.lst to include an option for home and an option for work, the difference being the command line options that specify which config (?) file to use.

---

### Post by deepee_oz on 2008-02-05
Thanks, that is a very good thought.
I would still prefer my installation to mimic the automatic configuration capabilites of the live CD, if there was a way to do it.

---

### Post by Scavok on 2008-02-05
Try: [http://ubuntuforums.org/showthread.php?t=578376](http://ubuntuforums.org/showthread.php?t=578376)

Then there are these--pertaining to a USB thumb drive:
> In 'this' ([http://www.ubuntuforums.org/showthread.php?t=71567](http://www.ubuntuforums.org/showthread.php?t=71567)) thread

([http://www.ubuntuforums.org/showpost.php?p=1062799&postcount=100](http://www.ubuntuforums.org/showpost.php?p=1062799&postcount=100)),

([http://www.ubuntuforums.org/showpost.php?p=1221276&postcount=153](http://www.ubuntuforums.org/showpost.php?p=1221276&postcount=153)) and

([http://www.ubuntuforums.org/showpost.php?p=1229101&postcount=158](http://www.ubuntuforums.org/showpost.php?p=1229101&postcount=158))

People managed to copy the LiveCD to a USB Pendrive and boot from it in
persistent mode. Based on this I then managed to hack the initrd.gz to
boot it from a Compact Flash card in an IDE Adapter.

Related: [http://ubuntuforums.org/showthread.php?t=678146](http://ubuntuforums.org/showthread.php?t=678146)

HTH

---

### Post by deepee_oz on 2008-02-05
Thanks, I'll try these and paost an update.

---


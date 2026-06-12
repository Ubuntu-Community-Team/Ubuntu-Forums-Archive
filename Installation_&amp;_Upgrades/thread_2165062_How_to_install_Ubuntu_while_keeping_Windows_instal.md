---
title: "How to install Ubuntu while keeping Windows installation partition"
date: 2013-08-03
forum: Installation &amp; Upgrades
---

### Post by VegasTamborini on 2013-08-03
I want to install Ubuntu 12.04 onto my laptop as my only OS (not alongside Windows). However, as is becoming standard practice instead of receiving an Windows 7 installation CD there is just a partition that does the same thing. I want to keep this partition but install Ubuntu. What is the best way to do this?

---

### Post by Jack_Yuan on 2013-08-03
You should be able to actually shrink the windows partition from within windows. Once you do that you can install Ubuntu on the newly created partiition.

---

### Post by amra.sonntag2 on 2013-08-04
You can choose to keep the "Windows rescue" partition and get rid of all other Windows partitions. But I'm not sure how well Grub Bootloader will recognize this.

 You could also download a Windows 7 DVD for testing with 30-day usage and enable it with your Windows 7 Product Key (you should find it somewhere on the back of your machine). This might be the best solution for you. No need to keep anything unneccesary on your hard disk.

---

### Post by oldfred on 2013-08-04
The auto install options may overwrite entire drive if you choose that option. Generally better to use the Something Else and manually create partitions you need or want. And then you do not overwrite partition(s) you may want to keep.

Still best to make a set of DVDs to reinstall. That really is only if you want to restore to as purchased. Usually all data is then lost and it is more if you later want to sell system with an original install of Windows. Also best to just make a full backup of your Windows.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
W

---

### Post by VegasTamborini on 2013-08-04
Thanks oldfred, that is exactly the info I was looking for, and thanks for the links to other related questions, very helpful

---


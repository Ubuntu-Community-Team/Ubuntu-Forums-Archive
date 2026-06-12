---
title: "Reinstalling over a trashed upgrade??"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by imphil on 2010-03-04
I'm poised to reinstall Ubuntu 9.10 over a failed but semi functional upgrade to Ubuntu 9.04.

Normal upgrades are inhibited by the trashed version of 9.04.

I'm assuming it is advisable to format the offending partition, or disk in this case, before installation, or can I just install over 9.04?

Do I have to remove anything else from the system like the GRUB menu? 
I believe the GRUB for 9.10 is a different version to 9.04.

Any advice or cavaets??

Would it be more adviseable to try and reinstall 9.04 from a CD first and then upgrade?

Look before you leap this time!

---

### Post by presence1960 on 2010-03-04
I would do a clean install. First back up any data you don't want to lose. If you can boot into ubuntu you can use [this how-to]("http://ubuntuforums.org/showpost.php?p=7157175&postcount=5") to have all your packages (from current version) from the repositories installed on your new install after the installation completes. This can save you a lot of time getting the same packages installed versus installing them manually. Thanks to lovinglinux for sharing that info!

---

### Post by viper250 on 2010-03-04
grub may give you a problem re-installing. so if it is the only os you are going to have on the drive then you should wipe the drive. this will give you a clean installation.
the best wiper program I have seen is d-ban, It will sterilize a drive and perform a brute force drive test (if any errors are found it will display the message) if it finishes early with errors the disk is failing.
you can find d-ban at [www.linuxlinks.com](www.linuxlinks.com)
I use d-ban to clean drives for forensic purposes.

---

### Post by wojox on 2010-03-04
If the only thing on their is Ubuntu, I'd just fire up a live cd and delete the partitions for it and install 9.10. A fresh install is better to take advantage of Grub2 and ext4. ;)

---

### Post by imphil on 2010-03-05
Thank you so much guys, I finally got this nightmare sorted out and learned more than I intended to, ;),  in the process.

---


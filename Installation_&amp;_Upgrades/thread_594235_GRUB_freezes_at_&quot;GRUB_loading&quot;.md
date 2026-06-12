---
title: "GRUB freezes at &quot;GRUB loading&quot;"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by Skootles on 2007-10-27
Alright, so I've tried every install - server, desktop, and alternative on my new machine. With Server and Alternative, it actually gets installed, but when I reboot, GRUB hangs at the "GRUB loading, please wait..." 

Now, I tried booting to a liveCD and installing GRUB again [using these instructions]("http://ubuntuforums.org/showthread.php?t=224351") and everything seemed to work, so I rebooted, but still the same thing.

Now, I figure that this may be because I'm using a 2GB Compact Flash drive with a CF to IDE adapter as my main drive, but it should work, shouldn't it?

EDIT: Just as I'm typing this, after about 10-15 minutes of waiting, GRUB actually loaded, and I chose the regular boot. Now it's just a black screen with a blinking cursor..

---

### Post by It_Was_Luck on 2007-10-27
2GB flash isn't much... I actually don't even beleive thats enough. You need a minimum of 2GB just for ubuntu, and at least 256mb for the swap partition.

Anyway you can always burn yourself a Super Grub Disk
Heres the site in case you want to read up on it...
[http://supergrub.forjamari.linex.org/?section=home](http://supergrub.forjamari.linex.org/?section=home)
and heres the download link...
[http://forjamari.linex.org/frs/download.php/605/sgd_0.9598.iso.bz2](http://forjamari.linex.org/frs/download.php/605/sgd_0.9598.iso.bz2)

Its very helpful I must say (I burned my own copy awhile ago) and it might help you with your grub issues.

hth

---


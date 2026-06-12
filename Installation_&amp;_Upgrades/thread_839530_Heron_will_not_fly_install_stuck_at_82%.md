---
title: "Heron will not fly: install stuck at 82%"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by Jamface on 2008-06-24
I am relatively new to Linux and Ubuntu.  I had installed Ubuntu 7 but could not get the internet connection to work.  Now, while trying to install Ubuntu 8.04 after cleaning out 7 by deleting and restoring and formatting partitions the installation of Ubuntu 8 hangs at 82% while Configuring apt and scanning CD-ROM.  I gave the system 18 mins to do this during which there was no DVD drive activity and no change on screen.  After power down I was able to reboot Windows XP on its partition. The same happens if I try to install from the live session.  If I go to the drive via Places and double click the drive I get 'Unable to mount location. No media in the drive.'

Any suggestions for how I might install Ubuntu 8.04?

---

### Post by pytheas22 on 2008-06-24
Did you check your CD for defects?  There's an option to do this at the boot screen.

If the checksums ran alright, then you could try using the alternate install CD.  Go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and make sure you check the box saying you need to download the alternate CD.  There's also [wubi]("http://wubi-installer.org/") if you really can't get Ubuntu to install from CD.

I'm also wondering why you tried to mount the CD during the live session.  There should be no need for that.  Just click the icon on the desktop to start the install.  Trying to mount file systems in the live session can cause the installer to fail.

Also just so you know, there's no need to do delete partitions if you want to wipe out an old installation of Ubuntu.  Just install the new Ubuntu on top of the old ones and it should all be fine.

And I'd be happy to try to help with the networking problem once you get Ubuntu installed.

---

### Post by Jamface on 2008-06-25
Many thanks for your help and suggestions.  I tried installing by deleting the partitions I had added and letting Ubuntu use the free space.  It worked! Previously I must have messed up the partition settings.

And it set up the internet connection!  My Heron is flying!

---

### Post by meindian523 on 2008-06-25
Please mark thread as solved

---


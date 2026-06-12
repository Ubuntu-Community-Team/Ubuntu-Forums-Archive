---
title: "merge wubi installation to a clean partition"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by laviams on 2011-02-01
Hey, about 3 weeks ago I decided to install Ubuntu 10.10 after being familiar and well experienced with it for several months using grub boot loader. Since grub menu did some troubles the last time I installed Ubuntu I decided to install it through wubi and if I'll be okay with Ubuntu for 2½ weeks without using Windows I'll reinstall it on a clean installation without any menus (not grub menu which have done lots of troubles and not mbr through wubi that limits my Ubuntu installation lots!) - without Windows.

I have two hard drives:
[LIST]
[*]150 GB sata drive as my primary hard drive - Windows 7 installation (ntfs)
[*]80 GB old IDE drive as my secondary drive with some backups and wubi installation on
[/LIST]
And a 500GB external disk so I could copy pretty much everything that needs back up.
What I want is to pretty much copy wubi's virtual disk installation to a clean ext4 partition on my sata drive - I couldn't realize how much I used Ubuntu and almost used the entire 30GB wubi has!
The only tutorial I found for moving wubi only scared me about losing my data - so hmm.. Is there any way to do this without having to clean install and reinstall all of my packages?
I would also need help partition my disks - I mean I know how and what should be there.. just what would be best in my case right now?
It could also be nice to keep a little Windows partiton (about 30-50GB) for "emergency" - I mean - a week ago was the only time I used windows to do a firmware update which was only available for Windows - so is there a way to use MBR as a boot menu without grub menus at all? if not I would rather not to keep Windows.. Grub menus are trouble makers.
And one last question on this list (XD): Is it possible to clean install Ubuntu and then just install back all of my packages and data? without having to manualy download and install? (and also keep the data for each package?)

**Thank lots for even just reading and for any attempt to help!**

---

### Post by Rubi1200 on 2011-02-01
Hi and welcome to the forums :-)

The best guide I know of is written by forum member bcbc:
[http://www.art.ubuntuforums.org/showthread.php?t=1519354](http://www.art.ubuntuforums.org/showthread.php?t=1519354)

If you have specific questions/concerns, ask in the thread there.

---

### Post by laviams on 2011-02-01
Hey! Thank you very much for your help. But I think it will be better to clean install and just copy all of my packages on it.. is that possible? I tried APTonCD but I couldn't really get too much of it =/

---

### Post by Rubi1200 on 2011-02-01
Hi,
this link might be what you are looking for as to restoring your favorite programs:
[http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)

As far as GRUB is concerned, you will need to use it for bootloading. Once set up properly it shouldn't cause problems.

If you want to install 10.10, be very careful as there have been problems with the installer wiping out Windows.

See here for more:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)

This site has probably the best guides I know of for setting up a dual-boot system, including with more than one hard-drive:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---


---
title: "Oversize is a pain since Updates are killing us"
date: 2008-12-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2008-12-04
I do O.K. with early broken Alpha's if I can download a CD and try it.  If it blows, wait for the next, or try some workarounds.

Since Jaunty Daily Builds are consistently oversize I try updates which killed sound on one after the other until now all four of my test systems are "dumb" as in deaf, dumb, and blind.

Now the updates are killing video too.  Can't someone dump some extra stuff, example Gnome Games, to get rid of oversize?  I can always use Synaptic to get them if I wanted to (not).

I'm back to the original Alternate install on Jaunty until Daily Build goes on a diet.

Thanks for anyone's consideration. Jerry

---

### Post by erkiha on 2008-12-05
You can easily just burn this oversize cd image to DVD media. I've done that and it works fine.

---

### Post by plun on 2008-12-05
Or skip CDs and DVDs and use a USB stick...just great !

[http://tombuntu.com/index.php/2008/11/12/create-a-bootable-usb-drive-the-easy-way-in-ubuntu-810/](http://tombuntu.com/index.php/2008/11/12/create-a-bootable-usb-drive-the-easy-way-in-ubuntu-810/)

---

### Post by jerrylamos on 2008-12-05
> **erkiha said:**
> You can easily just burn this oversize cd image to DVD media. I've done that and it works fine.

I tried DVD R/W on Ubuntu.  Tried to use the DVD for the next Daily Build and Ubuntu wouldn't erase the DVD.  Much too $$ for me to buy a new one often.

Jerry

---

### Post by jerrylamos on 2008-12-05
> **plun said:**
> Or skip CDs and DVDs and use a USB stick...just great !

[http://tombuntu.com/index.php/2008/11/12/create-a-bootable-usb-drive-the-easy-way-in-ubuntu-810/](http://tombuntu.com/index.php/2008/11/12/create-a-bootable-usb-drive-the-easy-way-in-ubuntu-810/)

USB flash boots on one of the four test PC's I use.  Pendrivelinux.com makes a CD that will boot a USB Flash on the others, but their latest version only boots 8.10.  I tried it, and there are changes in Jaunty file system that don't match 8.10.

Jerry

---

### Post by Kevbert on 2008-12-05
> **jerrylamos said:**
> I tried DVD R/W on Ubuntu.  Tried to use the DVD for the next Daily Build and Ubuntu wouldn't erase the DVD.  Much too $$ for me to buy a new one often.

Jerry

Same here Jerry. There seems to be a number of bug reports on Launchpad reporting this problem. I end up going into Windows just to erase a disk!!!
Can you confirm that [[COLOR="Red"]Brasero[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/301240") doesn't work ?

---

### Post by erkiha on 2008-12-05
But why do you need to download a new image every day????

I installed from intrepid and upgraded to jaunty. I upgrade daily. And it just works. You need to be careful sometimes but there are no more problems as there are on daily image.

> **Kevbert said:**
> Same here Jerry. There seems to be a number of bug reports on Launchpad reporting this problem. I end up going into Windows just to erase a disk!!!
Can you confirm that [[COLOR="Red"]Brasero[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/301240") doesn't work ?

---

### Post by plun on 2008-12-05
> **jerrylamos said:**
> USB flash boots on one of the four test PC's I use.  Pendrivelinux.com makes a CD that will boot a USB Flash on the others, but their latest version only boots 8.10.  I tried it, and there are changes in Jaunty file system that don't match 8.10.

Jerry

Ok...I needed to upgrade SysLinux version to Debians when I tried another USB disk  (Parted Magic)  Maybe the same problem for Jaunty isos  ?

Ubuntus USB creator is not compatible with newer Syslinux versions.

I also don't think this problem has "high priority" because the majority of core devs are going to MountainView and Fosscamp/UDS 

[http://www.jonobacon.org/?p=1464](http://www.jonobacon.org/?p=1464)

An upgrade from Alpha 1 or Intrepid cannot be any problem.

---

### Post by Gina on 2008-12-05
I stopped using brasero some time back as it didn't have a verify option and have used K3b ever since.  I've had no problems with that with DVD+RW discs but for DVD-RW ones, it seems to need something extra.  With DVD+RW it's very simple - you get asked if you want to Overwrite the data, say yes and off it goes :)  With DVD-RW you need to reformat.

---

### Post by Kevbert on 2008-12-05
Thanks Gina. I'll give K3b a go.

---

### Post by BwackNinja on 2008-12-05
As I posted in IIT&D:

Also - another way of installing without a CD - [http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093) I've done it, so I know it still works, but make sure you have up to date vmlinuz & initrd.gz downloaded, not the edgy ones linked (just modify the download link to say "jaunty" instead of "edgy").

---

### Post by jerrylamos on 2008-12-06
O.K. daily build squeaked by 700 MB on 20081206.  Yay!

Installed on my four test systems, dual booted with Intrepid.

Compaq Presario CD Live install goes as expected except sound is faint cracking, similar to Jaunty from updates.  System Preferences Sound Test maybe faint crackling.  Volume max.  Intrepid no updates sound O.K.

IBM Thinkpad T40 CD Live install went as expected, splash can play sound, not sure about anything else (except Intrepid un-updated of course) will check tomorrow.  I did re-check, it does play You Tube sound.

IBM ThinkCentre A30 with Jaunty from updates had a dead desktop altogether.  Partly up and hang. This is integrated Intel Graphics, Intrepid hangs unless Compiz removed.  Hardy fine.
CD Live Jaunty running mostly O.K., Gnome fail-safe mode.

IBM Thinkpad R31 with Jaunty from updates put desktop almost up and then hang.  This is integrated Intel Graphics, Intrepid hangs unless Compiz removed.  Hardy fine.
CD Live Jaunty running O.K., no mention of Gnome fail-safe mode and of course System Preferences Sound Test is silent, volume max.

Having been burned to a crisp with updates, I'm not about to install the 204 updates that Ubuntu thinks I should put on, do note this is today's Daily Build and 204 changes already?!

After I catch my breath I'll do another days Daily Build if it fits and try again.

In the meantime I run Intrepid (unupdated) so I can hear something.

Jerry

---

### Post by ShirishAg75 on 2008-12-07
On Intrepid with all updates, including intrepid-updates sound cool :)

Jerry, perhaps you can put up your experiences on ubuntu-testing 

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/) although the page itself needs an update atm it seems.

---

### Post by Gina on 2008-12-07
I've installed Jaunty on both AMD64 and laptop from the Alpha 1 Alternate CD and use both regularly for web browsing.  Both are updated daily.  I haave no problem except that when mounting other partitions/drives I get "Unable to mount..." after entering my password, yet the mount works fine - I can then open the partition and access the files and folders.  Sound is now fine.  

I have yet to install Jaunty on my P3 (haven't had time) but when I do I'll probably use the daily build Live CD on DVD+RW  media.  I don't expect to put Jaunty on the P4 until near release when there is little chance of a complete trashing.

---


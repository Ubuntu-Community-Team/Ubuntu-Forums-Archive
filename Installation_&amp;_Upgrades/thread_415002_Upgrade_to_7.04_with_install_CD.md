---
title: "Upgrade to 7.04 with install CD ?"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by The Pinny Parlour on 2007-04-20
I have the complete version 7.04 on a CD. Is there a way to upgrade my Edgy to Feisty using the disc? I don't want to hose my files and emails etc that are already on my hard drive.

Thanks

---

### Post by frodon on 2007-04-20
You need the alternate install CD for that no the desktop one, all is documented there :
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by rich.bradshaw on 2007-04-20
Next time, make a seperate home partition, that way you can just install over and your files and settings in /home will still be there - this is what I have just realised, and it makes things much easier!

I think you must be able to... If the package files are on the CD the perhaps you could tell apt to look on the CD... try opening Synaptic and see if you can tell it where to look for packages, choose the CD if there is such an option....

It might be easier to backup, reinstall and create a seperate home partition, then you never have to worry again.

Sorry I wasn't much help! :)

---

### Post by The Pinny Parlour on 2007-04-20
Thank  you greatly.  :)

---

### Post by mayamaniac on 2007-04-20
They should've added the Alternative CD download links into this page: [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

But you can find it among the mirrored sites: [LINK]("http://www.google.com/search?q=ubuntu-7.04-alternate-i386.iso&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")

I guess for upgrading, this should be the easiest way:

> Upgrading using the alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet.

   1.

      Download and burn the alternate installation CD
   2.

      Insert it into your CD-ROM drive
   3.

      A dialog will be displayed offering you the opportunity to upgrade using that CD
   4.

      Follow the on-screen instructions

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

gksu "sh /cdrom/cdromupgrade" 

---


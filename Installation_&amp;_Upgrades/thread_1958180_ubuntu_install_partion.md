---
title: "ubuntu install partion"
date: 2012-04-13
forum: Installation &amp; Upgrades
---

### Post by Virtueofselfishness on 2012-04-13
i am trying to dual boot Ubuntu and Win7 
My question is can i install ubuntu in the same partion as my win7 as you see in the picture 
 and will it overwrite win7? or will i have to make another partion for ubuntu itself

---

### Post by oldfred on 2012-04-13
The only way to install inside Windows is with Wubi. Wubi  is used by those who are Windows users and want an extended test over just booting with liveCD or USB.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Wubi is easy to uninstall as it is just a file inside the Windows NTFS partition and used the Windows boot loader. But that is its disadvantages also. It is not a true dual boot as if Windows does not work, Ubuntu will not work. If installed to a partition then you may be able to boot either system separately unless hard drive has totally failed.

That shows you have a d: drive which is just another partition, but Windows hides other partitions. Do not create partitions with Windows as it will convert to dynamic which does not work with Linux.

Some examples of dual boots with screenshots of the install process.
Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04- side by side auto install
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by Virtueofselfishness on 2012-04-13
thanks for the feedback!

i just shrunk the 334 (D) drive and took out 90 gb from it but when i tried to install wubi on it the installation didnt find the 90 gb i shrunk from the (D) drive

---

### Post by bcbc on 2012-04-13
Wubi can only install on a windows partition (i.e. ntfs or fat32). 

If you made free space, install a normal dual boot by booting from an Ubuntu CD/USB.

---

### Post by Quackers on 2012-04-13
As I understand wubi it uses a virtual disc rather than an actual hard drive.

If you want to install Ubuntu on a separate partition (as a stand alone system) and therefore dual-booting Windows and Ubuntu there are things you need to check first.
The first is that your current Windows system is not using 4 primary partitions. It often does. If that is the case you would need to delete a partition first. 
You can check that in the Windows Disk Management screen.

EDIT see bcbc's post above too :-)

---

### Post by Virtueofselfishness on 2012-04-13
ok cool thanks alot guys :D

---

### Post by Virtueofselfishness on 2012-04-15
i encountered a problem when i tried to install Ubuntu thru a cd. when i try too boot the cd i get this msg (attachment)

i read that you need to configure your boot settings when your using win7 and its my first time using win7 so i have no clue how to do it 

help! :mad:

---

### Post by Virtueofselfishness on 2012-04-15
ignore my last post i fixed that but now when ubuntu is loading up i get this screen

---

### Post by Quackers on 2012-04-15
If your graphics card is Nvidia or ATI you can try the nomodeset boot option as described below
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by jadtech on 2012-04-15
wow I think your on to something there that last thumbnail almost looks like win8 metro in hyper mode ..

---


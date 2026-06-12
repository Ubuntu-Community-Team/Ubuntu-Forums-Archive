---
title: "Installing KDE on Ubuntu 8.04 using the Kubuntu Live CD"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by Niladrish on 2008-06-20
I have Ubuntu 8.04 installed on my laptop and wanted to have KDE installed on it. I don't have an internet connection at present on my laptop, but I have the Kubuntu 8.04 Live CD. How do I go about installing KDE from it? 
I have tried to use the CD as the repository and tried installing kubuntu desktop and kde from it, but still the package manager needs to download 178 MB from the internet archives.

This is what I have tried 

sudo apt-cdrom add
sudo apt-get install kubuntu-desktop  

.. but it doesnot work.

Any ideas how to proceed ?

---

### Post by prabath_fun on 2008-10-05
Hi to all,
     I am also trying to install KDE desktop in Ubuntu 8.04. 

 Is it true that live cd cannot be used for installation purpose? please clear me.

With thanks,
PRABATH :-)

---

### Post by Rebelli0us on 2008-10-05
You're better off installing Kubuntu in a separate partition. I really miss the functionality of the Windows explorer. I read that KDE has an explorer equivalent called Konqueror, so I installed it using the Ubuntu package manager. But you do need internet access.   KDE and Konqueror are not explorer-like and neither impressed me, so I removed them, again using Package manager.

---

### Post by prabath_fun on 2008-10-05
Hi to all,
   Please clear me.

Replica of my doubt:
I am also trying to install KDE desktop in Ubuntu 8.04. 

Is it true that live cd cannot be used for installation purpose? please clear me.

With thanks,
PRABATH

---

### Post by deanjm1963 on 2008-10-05
Yes it is true that you can't install KDE off a "live cd" as the file system is compressed and apt has no easy way to access the files.

If you want to just install KDE just open up synaptic package manager and look for "kubuntu-desktop"

That will install the latest KDE Kubuntu (KDE 3.5.9) for you.

The files on the live/alternate CD are somewhat dated now and there are a large amount of updates so installing thru synaptic is a much easier option.

Just follow the install, you will be prompted for which log-in manager you wish to use, GDM (the Ubuntu default) or KDM (the Kubuntu default), either is fine to use with either gnome or kde.

Hope this helps.

---

### Post by aysiu on 2008-10-05
The live CD cannot be used to *add* Kubuntu to an existing Ubuntu installation. It can be used only to *replace* Ubuntu with Kubuntu entirely (i.e., erase everything you have) or install Kubuntu *next to* Ubuntu as a dual-boot on a separate partition (i.e., two separate installations).

If you want to add Kubuntu or KDE to Ubuntu, you have to use an internet connection or the Kubuntu Alternate CD.

The Desktop CD cannot be used for this purpose.

---

### Post by prabath_fun on 2008-10-06
Hi to all,
   Thanks for all your clarification. 
Prabath

---

### Post by ton_raf on 2009-01-18
so theres no way you can install ubuntu if you don't have internet connection or the alternate cd? where i can find the alternate cd?

---

### Post by prabath_fun on 2009-01-19
You can find at
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

Prabath

---


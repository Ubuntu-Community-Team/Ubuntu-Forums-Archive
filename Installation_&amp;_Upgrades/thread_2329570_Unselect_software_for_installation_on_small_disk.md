---
title: "Unselect software for installation on small disk"
date: 2016-07-03
forum: Installation &amp; Upgrades
---

### Post by rorypond on 2016-07-03
I try to install Lubuntu on a Fujitsu Futro S900 thin client. It has a 4 GB flash drive, which seems a bit small. 

So I have chosen an partition scheme swap partition. But it seems it doesn't work that way. Flash drive is still to small.

It seems, there's a a lot software to be installed on installation. I haven't found an option to unselect it. What can I do to install the system only. I will install useful software afterwards.

Thanks

Rory

Lubuntu 16.04 LTS

---

### Post by kalehrl on 2016-07-03
Install lubuntu-core via minimal Ubuntu ISO:
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Full_install.2C_minimal_install_or_core_install.3F](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Full_install.2C_minimal_install_or_core_install.3F)

---

### Post by rorypond on 2016-07-03
> **kalehrl said:**
> Install lubuntu-core via minimal Ubuntu ISO:
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Full_install.2C_minimal_install_or_core_install.3F](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Full_install.2C_minimal_install_or_core_install.3F)

Tried that. But I couldn't generate a bootable USB drive from that ISO file. I've downloaded the the 64 Bit Xenail Xerus ISO and wrote it to an USB drive with "ISO to USB" on a Windows machine. I can select it in the boot menu, but the machine doesn't boot. It switches to the internal drive where's no system installed. I'm stuck here.

Edit: I just saw, that the mini.iso is not intended to be booted from USB drives. 

Edit: I found Rufus tool to build a bootable USB flash drive. I Could boot and I'm currently running the installer.

Thanks so far

Rory

---

### Post by rorypond on 2016-07-05
Ok. Solved. It wasn't as complicated as it looked on the first sight. The internal 4GB SSD has only one partition, now. No swap space. I've installed lubuntu-core and some extra software like a browser (Firefox, should there be a smaller one), a pdf viewer and LibreOffice, mostly to view documents. There's about half a Gig left on the drive. Not to much for projects, but enough for some text documents. 

Since this is a spare machine, left over on renewal, I've a cheap (zero bucks) additional surf machine. With an DVI-to-HDMI-plug I can connect it to a TV set.

Thanks a lot, again.

CU 

Rory

---

### Post by Rex Bouwense on 2016-07-05
Rory there are other options that are not as resource intensive for your Lubuntu machine.  For instance Abiword for LibreOffice.  It will enable you to create text documents, but it is not as configurable (of course ) as LibreOffice.  Midori instead of Firefox.  Once again it doesn't have all the bells and whistles that Firefox has but it is a simple web browser.  Just a few ideas for your spare machine.

---

### Post by kalehrl on 2016-07-05
WPS Office is also an option for spreadsheets and word documents.
I use it on both Windows and Linux and it's much faster and takes less space than LibreOffice.

---

### Post by sudodus on 2016-07-05
If you want something really small, you can install a text-only system (similar to what you did with the Ubuntu mini.iso). On top of that you can install a window manager (instead of a full des&#7729;top environment), for example ***Fluxbox*** or ***Openbox***, plus ***xterm*** and the application software, that you want, for example the web browser ***Midori*** and in this case I think there will be space enough for ***Libre Office*** (if you don't like the simpler office alternatives).

In other words, cherry-pick what you really need ;-)

See these links, that provide a tarball for the One Button Installer to get a text-only system with menus to install some selected desktop environments or only a window manager and your own selection of program packages.

[Tested and debugged system to install [Ubuntu flavours of Xenial 32-bit alias 16.04 LTS](http://ubuntuforums.org/showthread.php?t=2172971&page=3&p=13511441#post13511441)

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

You can create a partition of the whole available drive and select it as the root partition but no swap (manually at the advanced level of the One Button Installer).

This will create a Xenial 32-bit system and occupies only 1.3 GB on the drive, so you have 2.3 GB free for application programs and data files. You should try to keep 10% of the space in the partition free to avoid problems with defragmentation (and if you reach a 100% full partition a locked system).

-o-

Another alternative is to install the operating system into a fast USB 3 pendrive and boot from there. That way you can easily have enough space for a full Lubuntu installed system with a lot of application programs. See this link and links from it,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---


---
title: "Alternate Install Method???"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by Jeremy07860 on 2007-01-11
Hello,

     Is it possible to create an executable install file for windows.  I would like to install Ubuntu on an old laptop that has no CD-rom.  I already run Ubuntu on my second machine at home, but I would like to be able to have it on a laptop to show others.  There has to be some other way to d/l and install other than burning the ISO image and booting from disc.  Any suggestions or comments feel free to e-mail me at [email]toybox@shitspace.com[/email].

-Jeremy

---

### Post by Jussi Kukkonen on 2007-01-11
I'm not going to mail you anything, hope that's ok. One of the points of a forum is that other people can read and learn too.

Netboot works and it also looks flashy to anyone watching -- the OS just magically starts installing even if you hard disk is totally empty and there are no disk drives!  It does requires PXE-boot or netboot support from your BIOS (might be difficult with older machines), a second machine and a little skill on the command line:  [https://help.ubuntu.com/community/Installation/QuickNetboot](https://help.ubuntu.com/community/Installation/QuickNetboot) (other alternatives in the wiki too, search)

Another alternative, closer to what you asked for is [http://sourceforge.net/projects/instlux](http://sourceforge.net/projects/instlux). I've never tried this.

---

### Post by Jeremy07860 on 2007-01-11
I will try the second method you shared with me.  Thanx alot.  I will post the results here when I get them... I hope this works.

-Jeremy

---

### Post by Jeremy07860 on 2007-01-12
ok... I tried instlux, but it doesn't exactly work like its suppose to.... it took me several attempts and multiple modifications before I got it working (i would post my mods, but there were so many I'm not sure what did it)............. when it finally worked, it will not recognize my network adapter (either my USB to CAT5, or wireless card)... this laptop has no built in wireless or network card.   So this option is out... unless somebody has an idea.       I then tried multiple NetBoot options to no avail... pretty much the same issues.  I then tried an option I found where you copy the ISO to the HDD and d/l and set up Grub and modify your boot.ini.... but the instructions ([https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)) are a bit outdated.   

Oh well..... looks like I have to wait until the Ubuntu people come up with an easy Install from windows executable or something that requires NO removable media or internet connection.   *hint*hint*

-Jeremy

p.s. if anybody has any ideas... PLEASE PLEASE PLEASE let me know

---

### Post by Sef on 2007-01-12
Do you have a floppy drive availble?

---

### Post by Jussi Kukkonen on 2007-01-12
> **Jeremy07860 said:**
> 
Oh well..... looks like I have to wait until the Ubuntu people come up with an easy Install from windows executable or something that requires NO removable media or internet connection.   *hint*hint*


The windows executable is a possibility, but an installation procedure that works without an internet connection or any removable media... that's physically  impossible I believe. :)

---

### Post by Jeremy07860 on 2007-01-12
@Sef - I have no floppy drive available

@Jussi Kukkonen - Why should it be impossible to install without a cd or removable media?  I could d/l this executable file on another system, transfer it to the laptop via thumbdrive and run it. (no, this laptop will NOT boot from thumbdrive... tried that too)

Any other ideas... this is become a mission... I just feel like this has to be possible.

-Jeremy

---

### Post by Jussi Kukkonen on 2007-01-13
Jeremy07860, if your machine has no removable media and no network, it's impossible to transfer data to it. A thumbdrive is definitely "removable media"...

---

### Post by Jeremy07860 on 2007-01-13
I was referring to bootable removable media (cdrom, floppy... or on newer systems, USB)  ](*,)

---

### Post by Jeremy07860 on 2007-01-15
Just an update... I found the docking station for this laptop on ebay for like US$15 and I bought it.  It has a dvd-rom and floppy drive so I can install Ubuntu on it now and show my friends the wonderful world of linux without having them to my house.

-thanx for all help and comments

-Jeremy

---


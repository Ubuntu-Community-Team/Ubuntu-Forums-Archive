---
title: "Installing Ubuntu without CD?"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by W. Irving on 2006-12-11
I have a very old laptop with a CD drive that, I only discovered, won't read CD-R's. I haven't tested yet whether BIOS allows for booting from a CD either, though it's rather unlikely..

So how do I install Ubuntu on this computer? It does have a floppy drive (a 3.5" one! ;)) and a PCMCIA Ethernet card, and currently runs Win95.

The only solution (the simplest anyway, that does not involve installing DOS with Ethernet support.. :p) I can think of is copying the contents of the CD image to a new partition on the drive, booting from this partition, installing Ubuntu on the Windows partition, and then delete the partition containing the installation CD.

Any ideas? Apart from ordering a pressed CD which there is no time for.

---

### Post by budgie9 on 2006-12-11
I anm not sure if this will work, but what about a memory stick. I seem to recall this being memtioned in the forums somewhere.
Can't you get someone to make you a CD?

---

### Post by W. Irving on 2006-12-11
> **budgie9 said:**
> I anm not sure if this will work, but what about a memory stick. I seem to recall this being memtioned in the forums somewhere.
Can't you get someone to make you a CD?

PC is manufactured before USB was even invented. PC does not read CD-R(W)'s.
:(

---

### Post by HoTseChu on 2006-12-11
In this link [http://http.us.debian.org/debian/dists/sarge/main/installer-i386/current//images/floppy/](http://http.us.debian.org/debian/dists/sarge/main/installer-i386/current//images/floppy/)
you can obtain a Debian minimal install in four 1.44 Mb diks. Then edit the sources.list for the ubuntu repositories, and then "apt-get udate" and "apt-get dist-upgrade" trying to complete the installation of Ubuntu from internet using your ethernet conection and a router. But this is only theory, I've never tried. Good luck!

---

### Post by W. Irving on 2006-12-11
> **HoTseChu said:**
> In this link [http://http.us.debian.org/debian/dists/sarge/main/installer-i386/current//images/floppy/](http://http.us.debian.org/debian/dists/sarge/main/installer-i386/current//images/floppy/)
you can obtain a Debian minimal install in four 1.44 Mb diks. Then edit the sources.list for the ubuntu repositories, and then "apt-get udate" and "apt-get dist-upgrade" trying to complete the installation of Ubuntu from internet using your ethernet conection and a router. But this is only theory, I've never tried. Good luck!

Very clever - thank you immensely HoTseChu! I shall try this approach if mine fails.

---

### Post by W. Irving on 2006-12-12
Update, I found this:
[https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies](https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies)

Which worked like a charm up to the point where the installation program looks for a CD to "load installer components" from. Obviously it doesn't find a Ubuntu CD and refuses to continue.

The wiki states that
> you will be prompted with an option to load modules from a disk. Say NO to this option.

which I did and then..

> You will be presented with a second screen to select another device. Say YES

Which it does not!

I suspect this might have something to do with the kernel line I feed grub. Perhaps > kernel /vmlinuz append vga=normal initrd=/initrd.gz ramdisk_size=16384 root=/dev/rd/0 rw --
needs to be something else to allow the installer to give me the option to look on the other partition of the drive?

---

### Post by HoTseChu on 2006-12-13
There is another possibility in:
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

The Smart Boot Manager not always run, but if you can use it to boot from CD, the installation will be easier.

---

### Post by W. Irving on 2006-12-13
> **HoTseChu said:**
> There is another possibility in:
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

The Smart Boot Manager not always run, but if you can use it to boot from CD, the installation will be easier.

Thanks, but as stated, the CD drive does not read any CD-R!

I'm nearly there though. So far, this is what I've done:

I installed Debian over the internet using the 3 floppies (yup, fully installed, not just the installer)
Then dd'ed the Ubuntu iso (which I wget'ed from another PC on my LAN) to a 900MB partition at the beginning of the drive (within first 1024 cylinders.. old BIOS :rolleyes: ).

Now I'm not sure how to proceed. I need to boot from hda1 where the Ubuntu image is located, but I don't know how to. I have GRUB installed on the MBR so I can get into Debian on hda2, so I suppose I could use that to boot the Ubuntu installer. Right? :)

---

### Post by ed_agamemnon on 2006-12-13
i wrote this guide a while back; actually, quite a long while back, for Ubuntu Breezy:

[http://www.ubuntuforums.org/showthread.php?t=28948]("http://www.ubuntuforums.org/showthread.php?t=28948")

this principle'll be the same for whichever version of Ubuntu you decide to install. 

since i wrote that, there have been a number of updated and better guides which achieve similar ends - i hope you can find them: i'm too lazy to look.

---

### Post by MJN on 2006-12-13
How about buying a pressed copy of Edgy from [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/) (Dapper available free)? Your CD-ROM should read one of those...
 
Mathew

---


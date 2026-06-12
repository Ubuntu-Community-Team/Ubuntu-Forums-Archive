---
title: "i have 2 SSDs in raid 0 is it possible to install Ubuntu and windows in dual boot?"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by maTvey on 2010-08-01
i have 2 ssd in raid 0 and 1 hard rive, and i want to know is that possible to install Ubuntu and windows 7 on raid 0? if not can i install windows 7 on my SSDs and Ubuntu on my regular hard rive?

---

### Post by ronparent on 2010-08-02
At this stage, Ubuntu 10.04 is not easily installed to a raid 0. No problem installing to a separate hard drive. Best to set the separate hd as boot if you do so. 

10.04 is installable to a raid with workarounds and possible grub fixing. Not advisable if you are not already well familiar with Ubuntu. The ssd is another potential problem. Mine is not raid but is seen by gparted as an unformatted drive even though win7 is installed and working! It would probably require realignment to use with Ubuntu (which I have no interest in presently. Good luck.

---

### Post by maTvey on 2010-08-02
ok, i will put win7 on one ssd and ubuntu on other ssd. i was usung ubuntu long time ago please can you tell me how i can install them on different SSDs whit dual boot?

---

### Post by oldfred on 2010-08-02
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Besure to use the advanced button to install grub to the same drive you install Ubuntu to. Then set that drive to boot in BIOS.

If you had RAID drives, they save raid metadata. I do not know if SSDs are the same or not.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by ronparent on 2010-08-02
> ok, i will put win7 on one ssd and ubuntu on other ssd. i was usung ubuntu long time ago please can you tell me how i can install them on different SSDs whit dual boot?

If you un-raid you ssd, you will run into another problem - They will retain metadata and be mistaken for raid drives even with raid turned off in bios. You would have to use dmraid to erase the raid metadata from the ssd's before you could proceed. Secondly, as I have already mentioned, you may have to give at least the ubuntu drive some special treatment, of which I'm unfamiliar, for you to be able to use it.

The dual boot is no particular issue if you don't mind overwriting the win7 boot loader and should be handled by the installer automatically if you let it write the grub boot loader to  the default location.

---

### Post by maTvey on 2010-08-02
if you saying that Ubuntu need some special treatment to work on ssd i think the best choice will be to leave the raid 0 with win7 on it and buy 15000 or 10000 RPM hard drive and install on it Ubuntu, what do you think about that?

---

### Post by oldfred on 2010-08-02
I think the link I provided to Herman's site (on Karmic) discusses some of the special settings. Those apply to any system install to SSD as it is different than a standard drive.

---

### Post by maTvey on 2010-08-03
but to install the Ubuntu on SSD i need to buy  Karmic Koala 'Alternate Installation' CD, a can not use downloaded version of Ubuntu from the website right?

---

### Post by oldfred on 2010-08-03
Hermans was Karmic but you now can download the Lucid alternate install from the Ubuntu site. You have to look for the other downloads as they emphasize the standard desktop install. 

[http://www.ubuntulinux.org/desktop/get-ubuntu/alternative-download](http://www.ubuntulinux.org/desktop/get-ubuntu/alternative-download)

---

### Post by maTvey on 2010-08-03
ubuntu-10.04-alternate-i386.iso and ubuntu-10.04-alternate-amd64.iso what the difference between them? is i386 is 86 bit, and amd64 is 64 bit? thank you for your help!

---

### Post by oldfred on 2010-08-03
They offer both 32bit and 64 bit version. The 64 bit is called amd as they created the standard which was an extension of the 32bit (which could run the 32bit binaries) where intel was going totally different. Intel could not sell that version and converted to the amd version so the 64bit is for any 64 bit intel or amd system.

---


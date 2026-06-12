---
title: "Bootsplash and terminal broken"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by scratchr on 2010-04-30
I upgraded to Ubuntu 10.04 from 9.10.
The terminal and boot show nothing but some random colored pixels at the top.
I also saw the old grub menu on boot.

_[COLOR=Red]NOTE: A system reinstall is NOT what I WANT TO DO![/COLOR]_

HELP!

---

### Post by paterijk on 2010-05-02
Exactly the same for me ... Upgraded tonite, and same symptoms as above. Tried configuring via "startup manager", but changed nothing. 

P.

---

### Post by davidmohammed on 2010-05-02
is it just the boot splash the issue or is it that you cannot boot to the desktop?

If you boot to the desktop - open a terminal and dump the contents of lspci here for everyone to see the specs of your pc.

---

### Post by scratchr on 2010-05-02
Never mind, I had to reinstall ubuntu for other reasons.

---

### Post by paterijk on 2010-05-03
In my case, when I start the computer, I won't see anything until the login screen, except some random color spots on a black background during the boot (where I suppose that I should normally see that pink splash screen).

I got a Dell Latitude D830 with an Nvidia graphics card. With 9.10 everything worked fine. 

Starting from the login screen, everything works fine. 

Thanx for any hint.

---

### Post by paterijk on 2010-05-03
Forgot the lspci: 

```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

---

### Post by tonitortosa on 2010-05-03
Hello all

I've upgraded Ubuntu Netbook Remix on an Asus 1000h laptop. The system is working fine, but I've also lost the boot image screen. It's just the boot image that shows "between" grub and login screen, that usually shows a bar with the startup progress. However I can see the shutdown progress screen with the ubuntu logo and the progress spots.

When starting it shows only a cursor at the top left corner. Also tried startup manager, but I can't find where to solve this.

I'll be trying during the morning and I'll tell us something.

Thanks

---

### Post by frodon on 2010-05-03
[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

See part 4, you should have all you need there to fix it.

---

### Post by paterijk on 2010-05-03
Found this on [http://ubuntuforums.org/showthread.php?t=1469475]("http://ubuntuforums.org/showthread.php?t=1469475"):

> Other graphics card users may get a black screen with flashing cursor and then a very short duration plymouth.
[https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801](https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801)
One fix for this is to create this file.

```
gksu gedit /etc/initramfs-tools/conf.d/splash
```

and add this option 

```
FRAMEBUFFER=y
```

save the file. Then

```
sudo update-initramfs -u
```

Plymouth now has a hard dependency on mountall thus trying to remove Plymouth would remove half the OS. The advice is, if you don't want a graphical boot then uninstall any plymouth themes.

I don't know if this is a good idea, but it worked in my case! 

P.

---

### Post by letmein on 2010-05-21
This is exactly my problem, installed 10.04 upgraded from my previous version...upon boot up, black screen with random dots of various colors at the top....any ideas? The solutions above did not help me...i can see my Grub menu (dual boot set up) with windows 7.  I believe im using Nvidia drivers, but dont quote me on that, any help would be much appreciated.

---


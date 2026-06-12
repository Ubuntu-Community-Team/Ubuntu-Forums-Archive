---
title: "Unable to Install Ubuntu - Unable to See Mouse Pointer"
date: 2015-12-01
forum: Installation &amp; Upgrades
---

### Post by GoodGuy98 on 2015-12-01
Our daughter purchased a new PC for herself and gave me her old one to pass along to my wife.  I have been trying to install Ubuntu, Ubuntu MATE and Mint 17.2 MATE without any success.
I have  been attempting to install LTS versions when available.

The mouse pointer does not display. The mouse is a Microsoft Intellimouse Explorer USB connected to the supplied USB-PS2 adapter plugged into the PS2 port on the PC.
I also tried using a Microsoft Intellimouse Optical connected the same way. The second mouse is currently being used on an old AMD T-Bird system running Ubuntu 10.04 LTS
and it works fine.

The PC from our daughter is more modern than the ancient AMD T-Bird, so I was hoping to get it going and upgrade my wife to a supported version of Ubuntu. I am stumped at this point,
so I was hoping someone would have ideas on how I get this going.

This is the PC specs:

HP Media Center PC M1160N
AMD Athlon 64 3400+
200gb Ultra DMA Hard Drive
512mb PC3200 DDR SDRAM
nVidia GeForce FX5200XT AGP with 128mb DDR Video Memory and TV-Out

I have tried both 32 and 64 bit OSes and also tried connecting the mouse via USB without success.

Any help would be appreciated.

---

### Post by oldfred on 2015-12-01
With only 512MB of RAM, Lubuntu is about the only flavor of Ubuntu that may work.

You also need 32bit, just because it is slightly smaller, do not know off hand if cpu is 32 or 64 bit.
But you also need nomodeset with nVidia card and will want to install a legacy driver to support it.

Many BIOS require you to turn on USB support for mouse & keyboard. Check your BIOS settings. Some may not be clear that it applies to mouse, may  just mention USB?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by yancek on 2015-12-01
There are a large number of other Linux systems available and if you go to the site below, you can enter parameters and get different recommendations.  There is also a listing further down the page with about 20 distributions with a brief description  of each.

 [http://distrowatch.com/search.php?category=Old+Computers](http://distrowatch.com/search.php?category=Old+Computers)

---

### Post by GoodGuy98 on 2015-12-03
Thank you for the replies. I was expecting to receive emails if there were any replies and none came. 
When I looked around on this web page, I saw the Thread Tools pulldown menu and subscribed to emails notices.
I will try the Lubuntu suggestion and nomodeset when I can.

---

### Post by GoodGuy98 on 2015-12-04
I downloaded and installed lubuntu-14.04.1-alternate-i386.iso. When I booted it, the mouse pointer appeared.
Now I want to take an image backup before trying to install the Legacy nVidia Driver.

Thank you very much for the help. I marked the thread as [Solved].

---


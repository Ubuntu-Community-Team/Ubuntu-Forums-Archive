---
title: "Help with installing ANY Ubuntu OS please!"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by PepeLapiu on 2007-04-12
So ok, I decided to install Ubuntu on my machine.
My first attempt was with the Ubuntu 7.04 Beta CD found here: [http://ubuntu.cs.utah.edu/releases/feisty/](http://ubuntu.cs.utah.edu/releases/feisty/)
But it didn't work, here are more details on this thread: [http://ubuntuforums.org/showthread.php?p=2434790#post2434790](http://ubuntuforums.org/showthread.php?p=2434790#post2434790)
Then I was informed that I should try the net installer ISO instead so I tried this CD burn instead:
[http://mirror.linux.org.mt/mirror/ub...tboot/mini.iso](http://mirror.linux.org.mt/mirror/ub...tboot/mini.iso)
But that didn't work either, the application installs the core fine but as soon as I try to install the second phase it takes 2-3 hours and a message comes out telling me the software didn't install properly. And it takes a good 3-4 hours of trying to install before announcing the install has failed.
So then I though :Screw the Beta stuff, I'll try a tested version" and enters my try with Kubuntu 6 so I burned the following ISO:
[http://ubuntu.cs.utah.edu/releases/edgy/](http://ubuntu.cs.utah.edu/releases/edgy/)
But hey, turns out that one didn't work either, the software tries to install, I see the starting page and after 20 min it just hangs there, not doing anything, I can't even try the OS from the disk, much less install it.

So what is a dude to do? How can I go about installing Ubuntu or Kubuntu and get it working?
Am I doing something wrong here?

And what is even more strange is that none of them wanted to install on my IDE PATA drives, they don't even see my IDE PATA drives, they only detect my SATA drives and will only install on my SATA drives which forces me to get rid of my nice RAID_0 array.

How can I get the install CD to recognize either of my IDE PATA drives and install on them?

---

### Post by bulldog on 2007-04-12
It depends a little what kind of hardware you're using.
Normally,you can install the live cd or if you have not that much of RAM, you can use the 'alternate cd' which is less resources consuming.
But if none of the ISO's will work,there could be a problem with the hardware.

I presume you did burn the .ISO to an Image,on a low speed,and you did check the cd for errors,before you attempt  to install?

---

### Post by PepeLapiu on 2007-04-12
OK, here's my hardware set-up, I have WAY enough of everything to install Ubuntu:

[COLOR="Blue"]- ATAPI CDRW 52x32 ATA (CD drive)

- ATAPI DVD DD 2x16x4x16 ATA (DVD drive)

- Sapphire Radeon X1950 XTX 512MB PCI-E w/ VIVO, Dual DVI, HDTV-Out, HDCP Graphic Card
[http://www.memoryexpress.com/index.php?PageTag=&page=file&memx_menu=EmbedProductDetail.php&DisplayProductID=9031&SID=](http://www.memoryexpress.com/index.php?PageTag=&page=file&memx_menu=EmbedProductDetail.php&DisplayProductID=9031&SID=)

- P5W-DH Deluxe Motherboard
[http://www.memoryexpress.com/index.php?PageTag=&page=file&memx_menu=EmbedProductDetail.php&DisplayProductID=8557&SID=](http://www.memoryexpress.com/index.php?PageTag=&page=file&memx_menu=EmbedProductDetail.php&DisplayProductID=8557&SID=)

- Intel Core2 E6600 @ 2.40GHz CPU (socket 775)
[http://www.memoryexpress.com/index.php?PageTag=&page=file&memx_menu=EmbedProductDetail.php&DisplayProductID=8655&SID=](http://www.memoryexpress.com/index.php?PageTag=&page=file&memx_menu=EmbedProductDetail.php&DisplayProductID=8655&SID=)

- Logitech G15 USB HID compliant Gaming Keyboard
[http://www.memoryexpress.com/index.php?PageTag=&page=file&memx_menu=EmbedProductDetail.php&DisplayProductID=6480&SID=](http://www.memoryexpress.com/index.php?PageTag=&page=file&memx_menu=EmbedProductDetail.php&DisplayProductID=6480&SID=)

- Logitech MX Revolution HID compliant Cordless Mouse
[http://www.memoryexpress.com/index.php?PageTag=&page=file&memx_menu=EmbedProductDetail.php&DisplayProductID=8967&SID=](http://www.memoryexpress.com/index.php?PageTag=&page=file&memx_menu=EmbedProductDetail.php&DisplayProductID=8967&SID=)

- Sharp LL-191A-B Monitor (19 inch)
[http://oncallcomputersolutions.netfirms.com/store/nfoscomm/catalog/product_info.php?products_id=39&osCsid=51797157c38770d1944e060ebb4cf367](http://oncallcomputersolutions.netfirms.com/store/nfoscomm/catalog/product_info.php?products_id=39&osCsid=51797157c38770d1944e060ebb4cf367)

- Hauppauge WinTV PVR PCI II (Encoder/Decoder) TV Tuner Card
[http://www.memoryexpress.com/index.php?PageTag=&page=file&memx_menu=EmbedProductDetail.php&DisplayProductID=4233&SID=](http://www.memoryexpress.com/index.php?PageTag=&page=file&memx_menu=EmbedProductDetail.php&DisplayProductID=4233&SID=)

- 2x1 GB RAM
[/COLOR]

At the moment I am downloading ubuntu-6.10-desktop.iso and burning it.
I have tried several burning process, all of them seemed to work but this time I will attempt to do it on a different CD brand. 
I did burn the ISO at the lowest possible speed and my NERO burner did re-check the CD after it was burned but on every single install attempt, when I try to check the CD during install, the system freezes and shows me the same error as when I try to install.

I am trying now with ubuntu-6.10-desktop.iso, I'll be back letting  you know how it goes.

---

### Post by PepeLapiu on 2007-04-12
> **bulldog said:**
> 
I presume you did burn the .ISO to an Image,on a low speed,and you did check the cd for errors,before you attempt  to install?

Yup!  I did all that but I can't use the install utility to check the CD because I always end up with the same error as when I try to install. I hope it's not a hardware problem, I built this machine myself and I would have no idea how to correct/diagnose this specific issue.

I used two different drives to burn the various CDs and I also used two different CD brands but always the same error!

I am trying to download Debian right now, I'll try that and if it doesn't work I'll have to live with stoopit windoze a while longer I guess.

---

### Post by rsambuca on 2007-04-12
I think the problem is with the JMicron controller on your motherboard.  Try [[COLOR="Red"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=373662") for workarounds.

---

### Post by PepeLapiu on 2007-04-12
Thanx a zillion!

---

### Post by |Eric| on 2007-10-01
OK here is a hint  your RAID 0 (from onboard "raid" controler) is a FAKERAID means only in windows it is recongnised so it is normal for linux not to install on this first off

---


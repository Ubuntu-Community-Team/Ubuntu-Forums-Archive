---
title: "Unable to instal Ubuntu 7.04 ?????"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by PepeLapiu on 2007-04-10
OK, here;s my hardware set-up:

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

Now I found this CD image and burned it on a CD: 
Ubuntu 7.04 (Feisty Fawn) Beta for PC (Intel x86) desktop

But when I tried to install it, the following screen came up during install (I might have made some typo mistakes here):

[COLOR="RoyalBlue"]udevd-event[2044]: run_program: 1/sbin/modprobe' abnormal exit

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)

Enter 'help' for a ls=ist of built-in commands

/bin/sh: can't access tty:  job control turned off

(initramfs)[/COLOR]

What should I do? I am clueless here, this is my first ever Linux install. How do I install Ubuntu now?

---

### Post by kerry_s on 2007-04-10
Did you check the md5sum or use the disk check? I usually see that error from a bad disk. It's recommended ISO's be burned at 4x for best results.

Here's the net installer ISO if you want to try that, you need a net connection to use-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)

Make sure your burning as a image. The net installer can install any supported ubuntu version, just boot from the cd and hit enter to start the installer.

---

### Post by PepeLapiu on 2007-04-10
OK, when I burned the image to the CD my Nero burning tool checked it for error and it was fine but I tried to boot up from the CD again and check the CD for errors and the very same error message as above came up.
So I am burning my image again to 8X (my slowest speed) and I will try to burn your ISO as well and see how they will both perform.
Be Right Back!

Nota Bene: I have a very nice Radeon x1950 XTX video card, that one is a screamer, it leaves tire burn marks in my case so I would ate to not be able to use it.
Are ATI Vid cards well supported with Linux?

---

### Post by RapMan on 2007-04-11
There can be problem with the motherboard, Herd 5 didn't boot at all.
So maybe not all problems are solved now.
Or is somebody running FF Beta on Asus p5w motherboard?
I mean instalation with default bios configuration and default instalation settings, without disabling any modules ?

---

### Post by blazerte on 2007-04-18
You know my new system is almost identical to yours (Asus P5B mb and core 2 duo, radeon 1950xt, etc) 
sata HD and DVD-RW

And same problem. I gave up until Feisty final. Installing Debian etch now. Seems to work fine.

---

### Post by Rroet on 2007-04-22
Same issue here with me on a P5B-E system.

I haven't found a fix either. I've also tried my old install on an old harddrive, exact same error.

---

### Post by whiteshiel on 2007-04-22
I am hammering out a solution. I will be updating this section: [http://ubuntuforums.org/showthread.php?t=417332](http://ubuntuforums.org/showthread.php?t=417332)

---

### Post by blazerte on 2007-04-28
Got it working on P5B-VM

Necessary to disable the JMicron sata/pata chip in bios. See this:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964)

Since my DVD R/W is SATA and I'm not using RAID, this is OK for me.

---

### Post by Loki-uk on 2007-04-28
I have and Asus P5B and it works flawlessly Feisty installed with no issues at all....

Loki

---

### Post by tuxologe on 2007-04-28
Hi,

I am another "victim" of the JMicron problematic. In my case the Ubuntu 7.04 installation fails because my only CD-ROM is an IDE one attached to the JMicron. I tried the boot options "irqpoll all-generic-ide" with no success. 
Then I tried to install from USB-Stick as described on [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
This did not work either because I did not manage to boot from the prepared USB-Stick. 

Any alternatives I found in this forum require an USB-CD-ROM or SATA-CD-ROM for booting.

But then I accidentally stumbled across a really nice workaround:

I left the USB-Stick plugged in while booting the Ubuntu installation CD in the IDE drive.
From my point of view it looked like the Ubuntu installer did not manage to find the IDE CD-ROM but it managed to find the USB-Stick and thought it would be the CD-ROM.

In conclusion I was finally able to boot and install Ubuntu 7.04 (Feisty Fawn) on my SATA disk attached to an ICH8R in AHCI mode.

Hope this workaround is helpful for other "victims" of the JMicron problem ;-)

---

### Post by blazerte on 2007-04-29
tuxologe:
I take it that once Feisty is installed, the cdrom attached to the Jmicron works ok?

---


---
title: "Startup on USB"
date: 2014-01-01
forum: Installation &amp; Upgrades
---

### Post by RogerDavis on 2014-01-01
I'm trying to create a startup USB, two different ways, but it won't start the machine.

I've tried both   [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)   and   [http://askubuntu.com/questions/191980/how-to-create-a-bootable-usb-stick](http://askubuntu.com/questions/191980/how-to-create-a-bootable-usb-stick)  .

Either way, the USB flashes a few times, and nothing else happens, ends up at a black screen with an "underline", and that's it.

I guess both usb-creator and UNetbootin are supposed to format the drive in a bootable way, as I read the instrustions.  I started both times with a freshly formatted USB drive in the regular FAT32 format.  I'm using a .iso I downloaded, 13.10 64 bit  ( /home/roger/Downloads/ubuntu-13.10-desktop-amd64.iso  ).  This is a 64 bit machine.

I'm thinking that this is something really basic and simple that the instructions don't even bother to cover because it's so basic... but I can't figure it out.

---

### Post by sudodus on 2014-01-01
No, booting from USB is like an inverted lottery. Often it works, but sometimes you have tough luck, and nothing seems to work. Fortunately we are several people at the Ubuntu Forums, that can help :-)

Please describe your hardware: the computer and the USB pendrive, it makes it easier to give relevant advice

- brand name and model of the computer *and* the pendrive
- CPU
- RAM
- graphics chip/card
- wifi chip/card

Have you tried the pendrive in another computer?

I have recently installed Ubuntu flavour programs into my brother's computers, and I had some issues that made me make a USB chainloader according to this tutorial [Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858"). Try it :-)

---

### Post by RogerDavis on 2014-01-01
- brand name and model of the computer - no brand, Desktop, Intel motherboard DZ77BH-55K
- pendrive - SanDisk USB 3.0, 64 gig, in a USB 2.0 port for now, will eventually use 3.0 from back of system
- CPU - Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz
- RAM - 16 gig
- graphics chip/card - Cape Verde PRO [Radeon HD 7750]
- wifi chip/card - None in main system - hardwired to wireless router, Verizon Actiontec MI424WR rev 1

also:
description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f7f37000-f7f373ff

Have you tried the pendrive in another computer? - No, not available right now, but I want to use it on others later

I'm a bit confused by the talk about "other operating systems" (- the same USB pendrive can boot with one operating system, but not another one, in some computers, while it boots happily in other computers with almost any operating system), since as it is supposed to boot from the USB first, the other OS should never come into play?  On this machine I can switch the hard drives off, so the ONLY drive is the USB I'm trying to boot from.  However, it doesn't work either with or without the drives (Ubuntu 12.04 and Windoze 7) turned on.

---

### Post by oldfred on 2014-01-01
Some just do not work.

And at least one motherboard will not boot from a USB installer that is over 4GB. But a UEFI/BIOS update resolves that one.

 Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)
Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

---

### Post by RogerDavis on 2014-01-01
Maybe what I need is a full install?  ]

But what is it I just did, some kind of limited install?

---

### Post by Eugene King on 2014-01-01
I am using a USB as I'm typing and the only way I got a reliable install was to burn the ISO to a DVD and boot up on the DVD and then select the full install and instead of chosing the PC as the device to install it on chose other and select your USB stick..........Have the install format it in E**-4 (cant remember it exactly EST-4 ETF-4 something like that...) and don't forget to select "/" for the boot.

Pendrive worked 80% of the time but was always a test OS system and everytime you booted to it it was like a fresh install.

---

### Post by RogerDavis on 2014-01-01
I tried to do a full install on the USB, but didn't do the E**-4 format, didn't see any option for that either.  Maybe I should format it that way before I install the OS?

I got the following on one time of about 5 tries to boot it:
error:reloc offset is out of the segment
Entering rescue mode
grub rescue

All the other tries got nothing...

The filesystem on that USB drive seems to be ext3/ext4.  Is this correct?

---

### Post by oldfred on 2014-01-01
An Installer created just for installing with persistence optional is normally FAT32.

But if a full install you need a larger flash drive (8GB or more) and then it has to be standard Linux formats, usually ext4 for / (root) and swap which has no format.

If installing to a flash drive or external USB device you generally must install from a different device. There is a option to unmount but I have had trouble using that and it just is easier to install from one device to another.

---

### Post by Eugene King on 2014-01-01
I should shoot a video of me creating a Bootable USB stick. 

I saw that there were videos on YouTube for it but never watched them.  

Did you see any format options at all?

---

### Post by Eugene King on 2014-01-01
Also At work its a Dell PC i'm using as my Linux box......so thats rebooting and hitting F12 until the beep happens. Then selecting the usb boot option.

At home I have a Sony laptop. Thats hitting F11 multiple times while its booting. everytime it reboots when I hit the F11 key it boots off of the next device. 

For me the USB is the third reboot.

---

### Post by Eugene King on 2014-01-01
I am using a cruiser 32g Cruzer Glide. EXT-4 is what I formatted it to.

My 8g stick was slow as dirt and filled up too fast.

---

### Post by RogerDavis on 2014-01-02
I installed from a DVD I made to the SanDisk USB 3.0, 64 gig, in a USB 2.0.  I don't recall any options for formatting, but checking the drive it shows ext3/ext4.

As of yet, no success, except the - error:reloc offset is out of the segment, Entering rescue mode, grub rescue  I got one time.

---

### Post by Eugene King on 2014-01-02
so you used a USB 3.0 as a 2.0? is that possible?

---

### Post by RogerDavis on 2014-01-02
As I understand it, 3.0 is fully backwards compatible with a 2.0 port.  Also, I hear that a 3.0 in a 2.0 port is somewhat faster than a 2.0 in a 2.0 port (unsure about this).

---

### Post by oldfred on 2014-01-02
I only have USB2 ports on old system. And I have a Microcenter too nearby. Every time I go into it I see that flash drives have dropped in price and I can get one cheaper or larger for the same price. I try not to go too often. :)
But last time or two  USB3 flash drives were only a dollar or so more, so I now buy them now. I have had no issues and it seems about 10% faster. But writes are always slow and you want to minimize those as best as you can.

       sudo hdparm -tT /dev/sda
Using this command, I get for Timing buffered disk reads MB/Sec
30.9 USB2 flash on USB2 port
34.4 USB3 flash on USB2 port
69.9 hard drive older
184.9 SSD (cheaper OEM)

      
 With SSD or Flash (trim does not work on flash) drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1

 After installing, change the fstab so that everything gets mounted with noatime.


 tune2fs -o journal_data_writeback /dev/sdxN
 tune2fs -O ^has_journal /dev/sdxN
 e2fsck -f /dev/sdxN

Someone posted this for their SSD, have not yet tried on my flash drive install. Some SSD settings help on flash, others do not matter.
> Mount options in fstab:
defaults,noatime,data=writeback,barrier=0,nobh,errors=remount-ro
The big one is data=writeback

---

### Post by sudodus on 2014-01-02
> **RogerDavis said:**
> - brand name and model of the computer - no brand, Desktop, Intel motherboard DZ77BH-55K
- pendrive - SanDisk USB 3.0, 64 gig, in a USB 2.0 port for now, will eventually use 3.0 from back of system
- CPU - Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz
- RAM - 16 gig
- graphics chip/card - Cape Verde PRO [Radeon HD 7750]
- wifi chip/card - None in main system - hardwired to wireless router, Verizon Actiontec MI424WR rev 1

also:
description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f7f37000-f7f373ff

Have you tried the pendrive in another computer? - No, not available right now, but I want to use it on others later

I'm a bit confused by the talk about "other operating systems" (- [COLOR=#ff0000]the same USB pendrive can boot with one operating system, but not another one, in some computers, while it boots happily in other computers with almost any operating system[/COLOR]), since as it is supposed to boot from the USB first, the other OS should never come into play?  On this machine I can switch the hard drives off, so the ONLY drive is the USB I'm trying to boot from.  However, it doesn't work either with or without the drives (Ubuntu 12.04 and Windoze 7) turned on.

Great description of the hardware :-)

SanDisk USB 3.0, 64 gig might not be the best 'booter'. According to my experience SanDisk Extreme USB 3.0, 16GB and 32GB, are very fast, even writing many small files, but fail to boot some computers (for example HP laptops). Try if it works better in the USB 3 port, or try via a USB chainloader (that might be a slow reader/writer but a good booter).

[COLOR=#ff0000]***I mean the OS in the USB drive***[/COLOR] (not in the computer's HDD). Or maybe I should say the bootloader and associated files, for example grub configuration files in the USB drive. I have tested it myself and seen the difference.

---

### Post by sudodus on 2014-01-02
> **RogerDavis said:**
> As I understand it, 3.0 is fully backwards compatible with a 2.0 port.  Also, I hear that a 3.0 in a 2.0 port is somewhat faster than a 2.0 in a 2.0 port (unsure about this).
Yes, I can confirm this :-)

My Sandisk Extreme USB3 32GB pendrive writes at 28-30 MB/s in a USB2 port, while typical USB 2 pendrives write at 4-10 MB/s. And that's with big files. The difference is even bigger when writing thousands of small files (as you do when installing a linux system).

---

### Post by sudodus on 2014-01-02
> **oldfred said:**
> I only have USB2 ports on old system. And I have a Microcenter too nearby. Every time I go into it I see that flash drives have dropped in price and I can get one cheaper or larger for the same price. I try not to go too often. :)
But last time or two  USB3 flash drives were only a dollar or so more, so I now buy them now. I have had no issues and it seems about 10% faster. But writes are always slow and you want to minimize those as best as you can.

       sudo hdparm -tT /dev/sda
Using this command, I get for Timing buffered disk reads MB/Sec
30.9 USB2 flash on USB2 port
34.4 USB3 flash on USB2 port
69.9 hard drive older
184.9 SSD (cheaper OEM)

      
 With SSD or Flash (trim does not work on flash) drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1

 After installing, change the fstab so that everything gets mounted with noatime.


 tune2fs -o journal_data_writeback /dev/sdxN
 tune2fs -O ^has_journal /dev/sdxN
 e2fsck -f /dev/sdxN

Someone posted this for their SSD, have not yet tried on my flash drive install. Some SSD settings help on flash, others do not matter.

Thanks for this nice write-up, *oldfred* :-)

And I have a question to you: Do you have any idea of what makes some pendrives better booters? [Low] speed, firmware? What about the location of the grub configuration files (and corresponding files for other bootloaders)? Is it an advantage, that they are very near the head of the drive? I'm asking because you are sometimes giving the advice to make a small boot partition near the head end on hugh HDD drives, where a big NTFS partition might push the linux root partition too far away from the head end.

---

### Post by chkneater on 2014-01-02
This is my advice friend, I've been using a WD USB External Drive for a couple years, and AFTER installation DON'T reboot, stay in the live session.  

Download grub-imageboot, and then on your INSTALLED system open your grub.d file (should be in ETC I think) and copy the grub-imageboot there.  That's seems to have worked for me through numerous header updates and upgrades.  I'm using 13.04 now, but it's worked since at least Ubu 10 or 11 for sure.  

Hope that works.

I mentioned copying to /etc/grub.d which shouldn't hurt, but I noticed on my system I just copied grub-imageboot to the root, not /home or anything like that.

Also, another thing I noticed in my particular case is at before startup I have to unplug the USB and right at startup plug it back in while the bios splash is going.  Weird but it works for me?...

I jsut noticed that I just copied grub-imageboot to the root system, not grub.d

Why FAT32?  Should use Ext3 or 4... for the Ubu install

---

### Post by sudodus on 2014-01-02
> **chkneater said:**
> Why FAT32?  Should use Ext3 or 4... for the Ubu install

***Fat32*** is often used in live and persistent live systems. This is what is is used by the [***Ubuntu Startup Disk Creator*** and ***Unetbootin***]("https://help.ubuntu.com/community/Installation/FromUSBStick"). *Edit*: I guess FAT32 is used because such a pendrive can be used for storage/transfer with linux as well as other operating systems (Windows, MacOS ...) at the same time as it is a boot disk.

But installed Ubuntu based systems use ext file systems.

And to make life even more complicated: if you [***clone***]("http://ubuntuforums.org/showthread.php?t=1958073") the iso file to the USB drive, the ISO 9660 file system from the iso file will be used. It is read-only, which can be an advantage as well as a disadvantage.

---

### Post by RogerDavis on 2014-01-12
I finally got it to work, with some quirks still present.  OldFreds suggestions got me started on this

1) This is how I got it to work:
- I used a live DVD just like I was going to install to a hard drive to do the below
- "Manually" format the drive
- I used the first choice of format type, I think it was ext4
- Set that partition for / (root)
- You also need a swap, which has no format.
- This is on a USB 3.0 thumb drive
- I found that the drive will boot from a USB 3.0 port, but NOT from a 2.0 port

NOTE:  It might have worked as an "automatic" install at the very first if I tried it in the 3.0 port at first, which I didn't do.

---

### Post by sudodus on 2014-01-12
I'm glad it works for you. If you have problems in a USB 2 port, it is probably because the USB 3 pendrive is not perfectly backwards compatible with USB 2, at least not concerning booting.

You can also read the following link [Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

---


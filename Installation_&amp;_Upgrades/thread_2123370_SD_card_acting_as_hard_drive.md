---
title: "SD card acting as hard drive"
date: 2013-03-07
forum: Installation &amp; Upgrades
---

### Post by AerodynamicMelon on 2013-03-07
I have a Dell Mini 910 that only has 3.5-4GB of memory, and I want to upgrade the OS from Ubuntu 8.04 to 12.10, but that requires at least 4.8GB, so what I wanted to do was use an SD card as the hard drive so that the new OS would fit and I would be able to download other things. So my two questions are is this possible, and if so how do you get it so that it downloads onto the card? Thanks.

---

### Post by darkod on 2013-03-08
Use the manual install option (Something Else) which allows you to create the / partition where ever you want. If you make it on the SD card, that's where it will be.

I'm not sure if the best option would be to use the internal storage for /boot partition since not all machines can boot from the SD card. You can try it both ways.

---

### Post by sudodus on 2013-03-08
I would like to add, that you can consider downloading the iso files of Lubuntu and Xubuntu, that may run smoother on that computer than standard 'vanilla' Ubuntu. I think it works to boot from a flash card as well as from a USB pendrive.

And it is important that the flash hardware is as fast as possible. And to decrease the wear of the flash hardware, add the [FONT=courier new]**noatime**[/FONT] option (in /etc/fstab)

---

### Post by Mark Phelps on 2013-03-08
From personal experience, I would advise strongly against relying on an SD card.  I've had only a few hard drives fail -- and that is across LOTS of years of computing.  So over all, hard drives are VERY reliable.  But, in much shorter time period, I've gone through over a dozen SD cards -- different brands, different speeds, different sizes.  They just don't hold up very well. And, unlike with hard drives where recovering data from a failing drive generally goes quite well, my experience with SD cards is the opposite -- when they suddenly don't mount anymore, the contents are gone.

---

### Post by darkod on 2013-03-08
> **Mark Phelps said:**
> From personal experience, I would advise strongly against relying on an SD card.  I've had only a few hard drives fail -- and that is across LOTS of years of computing.  So over all, hard drives are VERY reliable.  But, in much shorter time period, I've gone through over a dozen SD cards -- different brands, different speeds, different sizes.  They just don't hold up very well. And, unlike with hard drives where recovering data from a failing drive generally goes quite well, my experience with SD cards is the opposite -- when they suddenly don't mount anymore, the contents are gone.

On a similar topic and slight thread highjacking, have you had any extensive experience with CF cards used as linux boot device? Longetivity of life?

My home server currently boots from the mdadm raid but I am considering moving the OS to a CF card + CF-to-SATA adapter so that I can put the HDDs to sleep when not in use. In my previous job I've seen mini-PCs with CF card and XP on it, but I was there only a year and couldn't note if they die fast or not.

---

### Post by Mark Phelps on 2013-03-09
> **darkod said:**
> On a similar topic and slight thread highjacking, have you had any extensive experience with CF cards used as linux boot device? Longetivity of life?

Sorry, no.

---

### Post by p_code on 2013-03-10
> **Mark Phelps said:**
> From personal experience, I would advise  strongly against relying on an SD card. I've had only a few hard drives  fail -- and that is across LOTS of years of computing. So over all, hard  drives are VERY reliable. But, in much shorter time period, I've gone  through over a dozen SD cards -- different brands, different speeds,  different sizes. They just don't hold up very well. And, unlike with  hard drives where recovering data from a failing drive generally goes  quite well, my experience with SD cards is the opposite -- when they  suddenly don't mount anymore, the contents are gone.


I do fully agree that SD Cards and USB thumb devices CAN be  frustratingly troublesome, but in my experience, the issue isn't that  flash technology is inherently more unreliable than a mechanical drive,  it's that people don't deal with them in the same way.

Would you buy no-name junk hard drive for your PC?  No? I know I won't.   For example having had 4 seagate drives fail the last 4 or 5 years, I  won't touch a PC with a segate HD ... But with SD cards and Thumb Drives  folks routinely buy whatever inexpensive junk SD device that is on sale  (and even when you try to buy a name brand products, many are  counterfeits)

Would you wait till your mechanical hard drive is right in the middle of  doing something really important (like fsck'ing on startup, or  cache-flushing on shutdown -- and JUST YANK IT OUT OF YOUR PC WHILE IT'S  STILL WRITING? - of course not - but I have see generation-z youngsters  (some of whom seem to have the attention span of a fruit fly)  impatiently do EXACTLY this to both thumbdrives and SD cards (and then  act all surprised when the file system is corrupted).

Making matters WORSE is the really sad and STUPID fact that to save  about a penny on production cost 95% of the thumb drives these days, and  more than half the SD/USB readers, don't have read/write LEDs, so you  have no way of knowing for certain whether the drive is still being  accessed before removing it.  This is even more important in Linux, due  to another REALLY STUPID THING, which is that the SSD block device  drivers seem to have a really nasty little BUG that they can't seem to  track down, which causes thumb drive and SD card USB devices to write at  a respectable Gigabyte a Minute one minute, and then suddenly shift to a  few Megabytes a minute the next (so if you are guessing that "it must  be finished with that copy operation by now" you could be horribly  mistaken...

And lastly, along with device-quality, and user-errors, another factor  that is often overlooked, is that sometimes when there are reliability  issues with SD cards, the problem isn't the card, it's the reader  device.  I recently had to reluctantly return a Viewsonic Android Tablet  device that I was otherwise quite happy with, because it would only  read about 1 out of 6 microSD cards, and had reliability problems even  with the cards it would read.

But if you can deal with these issues, I have to respectfully disagree  about the virtues of running Linux from an SSD device. One of my  absolute favorite Linux configurations currently is a Knoppix full DVD  install on a microSD card installed in USB Thumb drives sized USB  reader.  One reason I run this configuration, as opposed to just a  dedicated thumb drive, is that the microSD/USB reader is about the same  size as many thumb drives, but provides that all-important read/write  LED indicator, so you can keep track of Read/Write activity.

These days an 8Gig microSD card is only about 8 bucks, even staying with  name brands like Kinsington or San Disk, and it's trivial to make a  backup by DD'ing the whole device to a second card, or a file on a hard  drive on another computer, so if the card does have a problem, it's not  really that big an issue.

And after a few tweaks, I love the fact that my USB Knoppix boots on  every computer I own, from a 3.5 Ghz quad-core Athlon, to an Old 600MHz  P3 that is so antiquated that lacks USB2 and can't even natively boot  USB1. 

In the interest of full disclosure, to get the Knoppix USB/microSD stick  running on my ancient 10 year old Pentium 3 laptop I did have to make a  couple minor tweaks--

-  Added a $12 Linux compatible PCMCIA dual port USB2 (NEC USB2 chipset) -since this 2000 vintage Laptop lacks USB2.

- I also had to unpack and edit and repack the initramfs from the  Knoppix USB install to add the PCMCIA kernel drivers to the 'Modules'  folder since modern distros like Knoppix and Ubuntu don't seem to bother  with boot-time PCMCIA support anymore. (also had to add  'nofb' to the  kernel boot options in syslinux.cfg to keep from getting corrupted text  consoles)

- My ancient P3 laptop is so old that it also lacks an option to boot  from USB, so I just leave a floppy loaded with the PLOP boot manager  loosely in the floppy drive, and pop it in when needed to chain boot my  USB stick automatically.


I know this sounds like a lot of work for an old machine that you would  think can't work very well anyway, but actually, you would be surprised  just how well it does run under Knoppix 7- I don't get Compiz on that  machine of course, because the 3D support is too weak, but the latest  XORG drivers do handle full 2D accelerated video overlay well enough to  play DVD quality video with VLC quite nicely.   And adding an  inexpensive WiFi USB dongle to the second USB2 port on my PCMCIA USB2  card lets me get on the web just as quickly and conveniently as with my  netbook.

It's too bad that you have to mess around with a custom initramfs to get  this going, because once it's working it does work amazingly well, and  it's really nice to have access to the same exact files and Desktop  configuration on ALL my PC's and Knoppix is smart enough to seemlessly  add in full Compiz support on the machines that will support it (both  for my intel based Atom Netbook, and AMD based Desktop PC).

And, while traveling, I can take my desktop with me in my pocket, with  the confidence that it will now boot on about %99.9 percent of the  available PC's out there.  And security while travling is not an issue,  because if you loose the USB stick, the security of your online accounts  and other info is protected, because Knoppix allows the option to AES  encrypt it's persistence data file.

Sorry to get so long winded, but long-story-short, the bottom line is  that Linux can actually run REALLY WELL from an SSD device like a  microSD card or USB Thumb drive, INCLUDING ON OLDER HARDWARE, if you are  willing to follow a few simple guidelines.

- Use known good quality Flash media (SD, microSD, or Flash Thumb Drive)

- For SD, or MicroSD Flash devices, also use a known good reader device

- Flash memory is fairly inexpensive now - MAKE BACKUPS.

- Use a distro taylored to the Flash Device
(one that doesn't need swap and won't thrash the device with too many write cycles)

- You can increase flexibility by using a ext2 linux style partition on  your Flash device, but NEVER put swap partition on a simple flash based  device like a USB Thumb Drive or SD/microSD card.  It will be horribly  slow and will eat the device with excessive write cycles.  To get around  the need for swap, some modern distros like Knoppix use a compressed  zram swap partition which can make a machine run fairly nicely with only  a few hundred kbytes of RAM and NO disk based swap partition.Eboot option in the BIOS, you can get very good results, but be prepaired to do a little work. [IMG]http://ubuntuforums.org/images/smilies/star.png[/IMG]

[B]Edit:
Sorry,  just realized I got off on a little bit of a tangent talking about  making Knoppix compatible with older hardware, but forgot to mention  that Knoppix 7 should boot  seamlessly on a machine like your mini910,  and that running from a 32Meg flash card or Thumb drive should work very  well right out of the gate. 

Also sorry to push Knoppix as an  alternative without first giving some options that address your request  about how to get Ubuntu 12 going.   The reason I suggested Knoppix, is  that the full DVD install has just about everything under the sun  pre-installed, and will run nicely from one of those micro USB drives  (the kind that only stick out a quarter inch or so) or from the internal  SD reader (assuming Knoppix recognizes it during boot-up).  As I said  above, Knoppix has zram swap, so will run without trashing the flash  memory, which could extend the life of your internal SSD disk on the  910.

But if you are determined to go with Ubuntu, and have a full  Gig of RAM installed, I would just forgo setting up a swap partition,  that way everything should squeeze into the space on your small 4 gig  SSD quite nicely.   If you have a full Gig of Ram Ubuntu shouldn't need  swap anyway, and as I noted for Knoppix above, not thrashing your SSD  with swap activity will extend it's life expectancy greatly.  (from what  I have seen on the web, the 910's internal SSD drive has been know to  crash rendering the device completly dead, and I suspect that this was  probably due to poor slubs who ran Micorsoft XP which trashed the hard  drive with too much virutal memory swapping)

Also, in Ubuntu 12,  even the simple live session installer will let you manually partition  your hard drive installation, and you can even split things over several  different storage devices if desired, as long as they are reccognized  by the installer. That last item, having the SD recognized by the installer, is the only snag I can see, because on my own netbook,  the internal card reader needs special drivers loaded, and if this is  the case,  you would need to install from a USB after editing the initramfs  to include the required kernel driver modules (creating a custom  initramfs is not a task for the faint of  heart). 

An easier  option would be to sqeeze a basic 12.04  installation into your exsisting 4Gigs of space by simply not assigning  any space to swap, then after you have a bootable system, you can move  your user 'home' folder to the SD card in the plugin slot (this will not  run into the problem of needing a custom initramfs mentioned above,  because Ubuntu will be able to boot from the 910's internal SSD disk,  loading all the drivers needed to recognize the internal SD reader, then  mount user home after that mount point is available.  This will work  even if you elect to encrypt your home folder in Ubuntu 12, just move  the whole already encrypted /home folder's contents (your encrypted home  user folder) over to the SD's root folder using a usb live session, and change the base mount  point in  /etc/fstab to point to mount SD root on /home (based on whatever /dev mount point your internal SD  card reader gives for the SD card.)  If you do go with encrypted home  folder option, make sure to write down the master password somewhere,  because if the internal SSD crashes, you will need that password to  recover your SD user home folders contents, even though it's safely on  the SD card.

Still a good idea to create a Knoppix or Ubuntu live  USB though, because it will allow you to boot up and use your 910 even  if the internal drive should completely  fail.

If you have been  happily using Ubuntu 8, I think you will really like Knoppix 7 though  with it's 'Clearlooks' classic style desktop (especially the full DVD  version, which comes with tons of pre-installed stuff).
[/B]

---

### Post by sudodus on 2013-03-10
I have good experiences with Knoppix too. It is often the best distro to boot 'any' computer and co-operate with 'any' hardware.

So we can recommend to try Knoppix as an alternative to an installed linux system or a flash card or USB pendrive. Knoppix can be installed, but it is discouraged. Instead run it 'persistent live' or with Knoppix terminology, poor man's install.

---


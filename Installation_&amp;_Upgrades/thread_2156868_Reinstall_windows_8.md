---
title: "Reinstall windows 8"
date: 2013-06-23
forum: Installation &amp; Upgrades
---

### Post by Heinzelmannchen on 2013-06-23
Well embarrassingly i deleted windows 8 when installing ubuntu. For the most part i don't need windows but would like to still have it. Is there anyway i can reinstall it without buying a new key? I have a lenovo g580 that came installed with windows 8. I just wish i realized what i was doing at the time =/. Oh well, any help is greatly appreciated

---

### Post by Old_Grey_Wolf on 2013-06-23
Look on the bottom of the laptop for a Microsoft Windows sticker. The key should be on the sticker.

---

### Post by oldfred on 2013-06-23
If it is a new UEFI system, you do not have a serial number on the bottom of the drive. It is actually somewhere in the UEFI memory. And if system was UEFI, you cannot reinstall in BIOS mode unless you buy a full new copy. Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

Windows has a lot of partition requirements for UEFI. 

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by Old_Grey_Wolf on 2013-06-23
oldfred is correct. I checked and the Lenovo g580 does appear to be UEFI.

---

### Post by Heinzelmannchen on 2013-06-23
Thank you for the responses. How would i go about installing windows 7 instead if i have an iso usb/disc? Would i basically need to delete everything on my hard drive and reformat it?

---

### Post by oldfred on 2013-06-23
Windows needs a NTFS formatted primary partition with the boot flag. Some have had issues if the primary is after the extended partition, but it does not have to be the first partition.

---

### Post by Mark Phelps on 2013-06-24
> **Heinzelmannchen said:**
> Thank you for the responses. How would i go about installing windows 7 instead if i have an iso usb/disc? Would i basically need to delete everything on my hard drive and reformat it?

You do know that you will need a product key to install Win7, right? And, since this is an OEM PC, and activates Windows using the BIOS, a retail version of Win7 might not activate.

Your best bet would be to contact Lenovo, tell them you accidentally erased the drive, trying to get rid of a Virus, and how do you go about restoring it?  You might have to purchase recovery media from them -- but that would be a lot cheaper than buying a retail license for Win7.

---

### Post by CharlesA on 2013-06-24
> **Mark Phelps said:**
> 
Your best bet would be to contact Lenovo, tell them you accidentally erased the drive, trying to get rid of a Virus, and how do you go about restoring it?  You might have to purchase recovery media from them -- but that would be a lot cheaper than buying a retail license for Win7.

Agreed. Most of the newer laptops I have seen have a recovery partition, but if you installed Ubuntu and wiped the drive, it is unlikely that partition still exists.

As a sidenote, I always clone the drive of a machine with Clonezilla before messing with partitions/dual booting. It has saved me many headaches, especially if I have to send a laptop in for service.

---

### Post by Heinzelmannchen on 2013-06-26
One more question...sorry:P Will this cd work with my situation? I'm not sure if it will recognize the product key in the bios. I messaged the seller and he said he didn't have experience with the product key being tin bios but saw no reason it wouldn&#8217;t work. Or does it require a recovery partion which i don&#8217;t have =/. 

[Reinstall CD ]("http://www.ebay.com/itm/261235523064?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1497.l2649")

---

### Post by oldfred on 2013-06-26
I would never buy Windows from ebay. It probably is not a legal copy.

You can download legal copies, but will have to pay for a new license. Windows 7 from DVD is not UEFI capabable and I doubt even if you convert it to UEFI install that it will accept a Windows 8 license. They are different.
It is the Windows 8 secure boot install that has key in UEFI.

---

### Post by ushpiy on 2013-06-26
I would suggest you to download the legal copy or torrent it and use the key that came with your laptop.

---

### Post by Mark Phelps on 2013-06-26
> **Heinzelmannchen said:**
> One more question...sorry:P Will this cd work with my situation? I'm not sure if it will recognize the product key in the bios. I messaged the seller and he said he didn't have experience with the product key being tin bios but saw no reason it wouldn’t work.
Of course ...the seller saw no reason ... they want your money!!

>  Or does it require a recovery partion which i don’t have =/. This version, most likely a cracked version that will eventually crash on you, does NOT require a recovery partition.

You keep looking for shortcuts to avoid the obvious solution -- contact Lenovo and get installation media from them!

---

### Post by CharlesA on 2013-06-26
> **Mark Phelps said:**
> 
You keep looking for shortcuts to avoid the obvious solution -- contact Lenovo and get installation media from them!

This. There is little reason to go downloading potentially cracked/hacked ISOs while trying to get Win8 back on your machine when you can just talk to the manufacturer.

---

### Post by Heinzelmannchen on 2013-06-27
Stupidity costs too much. $89 dollars to be exact, oh well. I just decided to call, i figured i'd try to get it a little cheaper. I guess it'll be safer and less of a headache to just buy it. I mean they should provide(and i should back up windows first thing:lolflag:)  the disc for free. Thanks again for the help, i can always rely on Ubuntu forums ):P

---


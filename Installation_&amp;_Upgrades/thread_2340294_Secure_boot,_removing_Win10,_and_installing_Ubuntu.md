---
title: "Secure boot, removing Win10, and installing Ubuntu."
date: 2016-10-17
forum: Installation &amp; Upgrades
---

### Post by starbase1 on 2016-10-17
I have a shiny new PC, but I am finding Windows 10 bad to the point of being unusable.

Right now, it only has Win10 as an OS.

I want to get to the point where it has Ubuntu and Win 7. The situation is complicated by the ASUS UEFI BIOS, which is currently stopping me installing anything else.

I seem to recall that it can be important which order you do things - from memory, Windows does not play nice if you try and install it after Linux, but I have no idea if that applies.

So can some kind person please explain what order I should do things in to end up with no Win10, Win7, and Ubuntu? I have found some instructions on turning off the "secure" boot, but I don't want to start changing things until I know where I am going with this!

Thanks in advance,
Nick

---

### Post by oldfred on 2016-10-17
I would still back up Windows 10.
 [http://www.howtogeek.com/239312/how-to-restore-system-image-backups-on-windows-7-8-and-10/](http://www.howtogeek.com/239312/how-to-restore-system-image-backups-on-windows-7-8-and-10/) 


And drive is gpt partitioned as Windows in UEFI mode only boots from gpt partitioned drives.
But Windows 7 DVD is only BIOS boot and will not install to a gpt partitioned drive.
Windows 7 can be installed in UEFI mode, by copying DVD to flash drive and move a few files around so it has the UEFI boot files in correct place for UEFI to find them. /EFI/Boot/bootx64.efi

For both Windows & Ubuntu how you boot install media, UEFI or BIOS is then how it installs.

This user said he need the repair/recovery from his Windows 8 to convert Windows 7
[https://ubuntuforums.org/showthread.php?t=2304736](https://ubuntuforums.org/showthread.php?t=2304736)
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Note that many UEFI call Secure Boot setting "Windows" or "Other" and since Windows 7 does not support Secure Boot, you must use "Other" setting. 

If you really want the 35 year old BIOS/MBR configuration which in UEFI is CSM, you have to erase drive & repartition to MBR. Then install Windows 7 first, then Ubuntu. Secure Boot also must be off to turn on BIOS/CSM/Legacy mode.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

For UEFI install of Ubuntu see link in my signature.
One of most important links:

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by starbase1 on 2016-10-17
Thanks for all thoise links, lots of reading to do.

But...

Whatever happened to the lovely easy installs I remember from when I last installed Linux a few years back? 
This looks serously messy!
:shock::shock::shock:

Nick

PS - No desire to ever see WIn10 again!

---

### Post by ian-weisser on 2016-10-17
> **starbase1 said:**
> Whatever happened to the lovely easy installs I remember from when I last installed Linux a few years back? 
You purchased a device from a manufacturer that deliberately makes Linux installs difficult.

---

### Post by oldfred on 2016-10-17
If you want easy, do not install Windows. It just installs with / & swap. If UEFI then it also has and ESP - efi system partition. But I always partition in advance as I want other partitions for data, ISO, backup, another install or two and leave space for future.

My install takes about 10 min to a prepartitioned drive, and no more than an hour to finalize all my configurations. Most configurations are scripted, but downloading my entire list of installed apps take a bit.

---

### Post by RobGoss on 2016-10-17
The process of installing Ubuntu if fairly easy in my opinion. I can install just about any distributions in about  5 to 10 minutes, it all depends on what brand of machine you're using some make things very hard for Linux users but once you get the hang of it things get much easier

---

### Post by starbase1 on 2016-10-18
> **ian-weisser said:**
> You purchased a device from a manufacturer that deliberately makes Linux installs difficult.

Unfortunately, I can't argue with that!

(I chose on the basis of the most powerful for the money)
Nick

---

### Post by starbase1 on 2016-10-18
> **oldfred said:**
> If you want easy, do not install Windows. It just installs with / & swap. If UEFI then it also has and ESP - efi system partition. But I always partition in advance as I want other partitions for data, ISO, backup, another install or two and leave space for future.

My install takes about 10 min to a prepartitioned drive, and no more than an hour to finalize all my configurations. Most configurations are scripted, but downloading my entire list of installed apps take a bit.

Any pointers to the simplest way of doing this? I'm getting confused by the acronyms!
Happy to wipe everything if it makes life easier...

---

### Post by mörgæs on 2016-10-18
You could just boot up and choose 'use entire drive for Buntu' during the install. It will automagically create the simplest possible partition layout. 

If you some day need a more flexible layout you could always repartition without losing the installed Buntu.

---

### Post by oldfred on 2016-10-18
If you want simple, just follow mörgæs advice. You get the ESP - efi system partiiton, / (root) and swap.
That is all a newer Ubuntu user needs although / will be very large.

But how you boot install media is then how it installs, so be sure to boot in UEFI mode from flash drive. UEFI on system should give two boot options UEFI or CSM/BIOS/legacy, if secure boot is off. Only UEFI with Secure boot on.

---


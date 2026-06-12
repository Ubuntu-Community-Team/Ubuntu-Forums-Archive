---
title: "Creating usb rescue"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by Sylos on 2010-08-10
Hello there.
I have been tasked with installing Lubuntu on an old PC for my dad. He is not very computer savvy and I live 300 miles away so I cant just pop round if it goes wrong.

As a result I am wondering if it is possible to create a backup of the Lubuntu installation on a 1gig flash stick. The idea is to install the Lubuntu system on a dedicated root partition with the /home directory on a separate partition. If all goes wrong he could then insret the flash stick and get the OS back to the state when I made the flash stick (kind of a rescue diisk).

Any ideas if this is possible or how to do it?

Thanks,

---

### Post by Sylos on 2010-08-10
Bump!

---

### Post by phillw on 2010-08-10
Hi, 

Yes, you can **provided** the 'old' machine supports USB boot. If it does not, then just use the installation CD.

You'd have to leave instructions as to which partitions to use at the re-installation however. For example...
[b]/dev/sda1 = /
/dev/sda2 = /home
/dev/sda3 = /swap[/b]
When you re-install, you set it as that again, but ensure that the check-mark to format **/dev/sda2** is not there, else the system will delete the contents of the /home partition.

As a picture is worth a thousand words, I'd suggest printing him off a screen shot of what that critical stage will look like.

It is precisely for being able to re-install a system that a lot of people do, eventually, decide to have a seperate /home partition. So your reasoning is 100% correct :-)

As for breaking it, if he just uses Update Manager; he'd be hard pressed to really break it.

Regards,

Phill.

---

### Post by Sylos on 2010-08-11
Hi there and thanks for the reply.
Im trying to avoid using the basic installation cd as I anticipate that when I install it I will have to do things my poor dad wont understand (downloading additional software, installing codecs etc). 

If I am understanding what you are saying correctly then I can set up an installation on a USB stick that he can use to reinstall (as long as he selects the correct partitions). Could this usb installation be created after I have installed all the extra bits and done the fiddling so as to install the customized setup?

Many thanks,

PS. If the motherboard does not support usb boot then could I make a customized installation cd instead?

---

### Post by Fludizz on 2010-08-11
You could try using a tool like Norton Ghost, create a partition image from the "/" partition. Then create a bootable CDROM with the disk imaging tool, the disk image and a restore script (autoexec.bat for instance) that restores the basic installed system to the "/" partition :)

---

### Post by Sylos on 2010-08-11
Thanks for the post. 

I think I understand what you are saying:
1. Make an image of the finished install with tweaks.
2. Put this on a bootable cd with a script that tells it to wipe the / partition and erplace it with the image from the disc.

Is that correct?

Also, how easy is that gonna be for someone who is only slightly linux literate like me?

Many Thanks

---

### Post by Fludizz on 2010-08-11
That's exactly what I mean yes :)

Only caveat with this method is the kernel. When the kernel is update by automatic updates, your grub will be updated with the new kernel image informatio. When you pop back the old '/' filesystem for recovery, the up-to-date kernel is gone and the bootloader is then unable to boot the system. However, invalid kernel in your grub is relatively easy to fix using a recovery cd but it does require manual intervention.

This above problem can be avoided by using two physical drives rather then partitions. Use one drive for "/home/" and one drive for "/". Then create a disk image rather then a partition image of the "/" drive (you can actually store that image on the second hard drive for easy and fast recovery ;)). With a disk image you usually also get the MBR (containing GRUB) in the image. When using this method, it is important to check for the MBR options in your disk imaging software to make sure it also includes this ;)

---

### Post by Sylos on 2010-08-12
Thanks that sounds like a good plan.

Any recomendations for disk imaging software.

I have heard of Ghost for linux (G4L0. Is that anything you would recomend?

Also, when you image the disk, will the image be as big as the whole drive: eg, if i have a 10gig disk with only 700mb of info on it and I image the whole disk do I get a predominatly blank image 10gig in size.

Sorry if im being a dunce.

---

### Post by Fludizz on 2010-08-13
Depends on the type of backup... it can be a bitmap of the entire drive, it kan be a compressed "smart" image of the drive only containing the actual data ;)

You should check the configurable options for the imaging tool. Regarding those, I've worked with Norton Ghost 2003 and found it to be very good, however it might not support modern filesystems like Ext4... :) No clue about the Linux version.

---

### Post by phillw on 2010-08-13
> **Sylos said:**
> Thanks that sounds like a good plan.

Any recomendations for disk imaging software.

Hi,

I'd go for [ReMasterSys](http://en.wikipedia.org/wiki/Remastersys) That way you can take a 'photocopy' of the installed system with any alterations you have made (e.g. installing CODECS, Drivers etc).

If you'd like more details on its usage, I'd suggest heading over the psychocats area at [http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys) If you have further questions, the author of those HowTo's has an area on this forum where you can ask (and, he's a really nice guy).

Regards,

Phill.
P.S. I still maintain that your Dad would be hard pressed to break it :P

---


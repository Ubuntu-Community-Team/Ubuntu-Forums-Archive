---
title: "Ubuntu Wubi + Live USB fail boot"
date: 2013-02-12
forum: Installation &amp; Upgrades
---

### Post by 2danny9 on 2013-02-12
Hi,

I had windows 8 so I ripped out the hard drive and stuck a new one in and installed Windows 7. 

So I decided to use Wubi to check if Ubuntu even works at all on this machine. 

These are BIOS settings: secure boot [disabled], fast boot [disabled], Launch CSM [enabled - I need this to boot into Windows 7, I had tried many things and this option allowed me to boot from my USB Windows 7 and install, if I disable this I get error: \EFI\Microsoft\Boot\BCD 0xc000000d]

I've install Ubuntu via Wubi check if it works and I get the error:

Windows failed to start:

File: \ubuntu\winboot\wubildr.mbr
Status: 0xc0000098

I tried enabling fast boot and this would not work as I get error thrown up by Windows i.e. 0xc000000d.

So I tried to boot from my USB live CD, and it does not detect my Windows 7 install at all. I got to the stage to my free partition but I'm unsure on creating the home/root/swap partition etc.

Linked here are the two OS throwing errors up, one with Launch CSM enabled and the other CSM disabled (Windows 7 works with CSM enabled but not disabled nor with fast boot, but it seems Wubsi does not like any option):

Attached: 

*Windows Disk Manager
*Wubi boot Error with and without CSM disabled or enabled 
*Windows boot Error with CSM disabled. 

Sorry all and thank you for looking,

Danny

---

### Post by Frogs Hair on 2013-02-12
You may want to check the links below. The Ubuntu volume will not be visible from Windows disk management because it inside The Windows partition.  

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by oldfred on 2013-02-12
You are still showing efi partition, but I cannot tell if you are still gpt partitioned or have converted to MBR(msdos).

Windows only boots from gpt with UEFI and UEFI requires gpt. Windows 7 systems will boot with UEFI/gpt if installed that way.

But wubi does not work with gpt partitions. And if you used Windows to install in MBR mode, Windows does not delete the backup gpt partition table at the end of the drive and still creates issues as Linux tools see both MBR and gpt.

I also thought before Windows 8 came out they were having vendors update things in such a way that Windows 7 would not boot as it would not have the needed new drivers. Or no way to down-grade. Did Windows 7 work ok before installing wubi?

CSM mode is another name for BIOS or legacy in UEFI. So you should have MBR partitions and then wubi should work.

---

### Post by 2danny9 on 2013-02-13
Yep Windows 7 works fine. Took me good few hours spread of a few days trying to partition my W8 HDD and install W7, so I gave up and used my old laptop hard disk. By then I saw that CSM option so I tried it and it works!

The issue with Windows 8 is 99% of my drivers are Windows 7, they think putting the driver in a folder named Windows 8 driver makes it a Windows 8 driver (he-he).

But Wubi won't work. Does this mean if I do a manual install it won't work too?

I will look at Frogs Hair links and will reply soon! 

By the way my laptop is a: ASUS U32VJ.

For now I've resorted to using VirtualBox to use Ubuntu (I must say, since the introduction to it at University and having to use it for a project or two, I'm becoming attached to Ubuntu as well as other flavors and the wonderful terminal Window!)

Thanks all,

Dan

> **oldfred said:**
> You are still showing efi partition, but I cannot tell if you are still gpt partitioned or have converted to MBR(msdos).

Windows only boots from gpt with UEFI and UEFI requires gpt. Windows 7 systems will boot with UEFI/gpt if installed that way.

But wubi does not work with gpt partitions. And if you used Windows to install in MBR mode, Windows does not delete the backup gpt partition table at the end of the drive and still creates issues as Linux tools see both MBR and gpt.

I also thought before Windows 8 came out they were having vendors update things in such a way that Windows 7 would not boot as it would not have the needed new drivers. Or no way to down-grade. Did Windows 7 work ok before installing wubi?

CSM mode is another name for BIOS or legacy in UEFI. So you should have MBR partitions and then wubi should work.

---

### Post by 2danny9 on 2013-02-13
Hi again,

I know it is the wrong thread but you lovely individuals have spoken to me!

Is possible to install it via USB and use the Windows boot loader? What partitons do I need to create, an EXT4 for /Home (i think), a /root and swap? I'll do some search on the internet!

I don't have a EFI disable option. Only secure boot and CMS.

One problem after the other, thanks Microsoft and you OEMs.

Dan

---

### Post by oldfred on 2013-02-13
Microsoft's specifications are that the user be able to turn secure boot off. So there must be a way. 
CSM is just BIOS or legacy, but you still should be able to boot with UEFI but not secure boot. CSM is normally a separate setting that you can only turn on if secure boot is off. 
Some systems just have a secure boot on/off. Others have a UEFI boot on which acutally means secure boot off. 
Perhaps secure boot off and csm off them defaults to UEFI only?

Asus with UEFI, I would think Asus would have one UEFI but customize for each model.

       Asus N56VJ-SH71-CD - shows partitions after install
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus K55n will not boot in UEFI mode. Boot Parameters? Feb 2013
[http://ubuntuforums.org/showthread.php?t=2111720](http://ubuntuforums.org/showthread.php?t=2111720)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)

Older before secure boot issues
       
 [SOLVED] UEFI Boot Problems Asus
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
       [http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)

---


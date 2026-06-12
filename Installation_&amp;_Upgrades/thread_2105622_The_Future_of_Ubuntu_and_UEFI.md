---
title: "The Future of Ubuntu and UEFI"
date: 2013-01-16
forum: Installation &amp; Upgrades
---

### Post by Nesaskewatch on 2013-01-16
Just a quick question if I may... Will 13.04 be more able to deal with dual booting a UEFI type system that has windows 8 pre-installed? Does it make sense to wait for the release if it can? I have found dozens of methods for making a dual boot but all are slightly different and I have been bitten too many times by things like this. However, if I did decide to press on using 12.10 x64, is it wise to select the first answer [here]("http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system") as the best method?

Cheers!

---

### Post by oldfred on 2013-01-16
Some good info in link, but I disagree with some issues. Use Windows to shrink the Windows partition and reboot several times to make sure it runs chkdsk & makes whatever updates it does on resize. But never create partitions with Windows. It still likes to convert to dynamic partitions and you cannot create Linux partitions with Windows anyway.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)


Some systems have keys to enable UEFI which really means use UEFI not secure boot. Others have a secure boot on/off switch. But you do not want legacy/BIOS/AHCI or whatever as then you will not install in UEFI mode. Do not create a new efi partition if you already have one. You can only have one efi partition (that is used for booting). 

    
And because of a bug in os-prober it is easiest to use Boot-Repair to create correct chain load entries.
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Nesaskewatch on 2013-01-23
I am completely lost. I just don't understand what to do. I guess I am going to have to suffer using windows 8 until installing is simplified for idiots like me.

---

### Post by Nesaskewatch on 2013-01-24
I couldn't leave things that way and decided to try again today. I just can't get this laptop to boot off of either a live DVD nor a live usb. I Guess I really do not have the skills needed to install Ubuntu. Thanks for trying.

---

### Post by oldfred on 2013-01-24
Did you go into UEFI/BIOS and turn off secure boot and fast boot?

---

### Post by Nesaskewatch on 2013-01-26
Sorry for the delay Fred. I've been out hunting around for clues and managed to get the machine to boot off of a live dvd. With this Asus N56VJ-SH71-CD I discovered that one has to enable "Lauch CSM" too, then disable fast and secure boot and hold the esc key during restart get the option to select the dvd drive. I will try and follow the remainder of your tips now that I have Ubuntu running. I'll post back how it goes. Thanks for your patience!

---

### Post by grahammechanical on 2013-01-26
> Will 13.04 be more able to deal with dual booting a UEFI type system that has windows 8 pre-installed? 

Ubuntu 13.04 will not doubt have a signed kernel in the same way that 12.10 does. The issues with getting a trouble free install are more to do with the way the hardware makers implement both the UEFI and secure boot specifications. Do not expect miracles.

Regards.

---

### Post by Nesaskewatch on 2013-01-26
> **grahammechanical said:**
> Ubuntu 13.04 will not doubt have a signed kernel in the same way that 12.10 does. The issues with getting a trouble free install are more to do with the way the hardware makers implement both the UEFI and secure boot specifications. Do not expect miracles.

Regards.I have come understand that. I plan on emailing Asus about it, but meantime I'll just keep banging away at getting it done. I am starting to think I just might. Go figger...

---

### Post by oldfred on 2013-01-26
Over time vendors will update UEFI and LInux will find work arounds to improve how it works. We already have seen a lot of improvement in UEFI so far.

Two others with Asus which may have similar UEFI even if different models.

       Asus S46CA Ultrabook Problems with Windows Recovery and grub after dual-boot install with Ubuntu 12.04
[http://ubuntuforums.org/showthread.php?t=2098477](http://ubuntuforums.org/showthread.php?t=2098477)> 
UEFI boot - In order to get into Windows Recovery, I had to hit F9 before GRUB appeared. My mistake was to wait for GRUB to appear, select one of the 2 working Windows options (Windows UEFI loader or Windows Boot UEFI bootx64.efi.bkp) and by that time I was past the possibility to get into Windows recovery system.

    
       Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)

---

### Post by sudodus on 2013-01-26
Is it possible to get around the problems with UEFI, when using two drives, one for Ubuntu and one for Windows? This would be easy in desktops and workstations, and possible with USB3 or eSATA in laptops.

---

### Post by oldfred on 2013-01-26
I always suggest two drives and with UEFI it may be more important to physically disconnect one. But you still have to install in UEFI mode. 

You cannot dual boot if not in same mode, as either UEFI or BIOS write data to drive in different places. Or it is a huge hassle to go into UEFI/BIOS and turn one or the other on to boot a different system.

You can easily chain load from one efi partition to another, somewhat like chain loading from one MBR to another that I do. But you have to specify UUID to find efi partition on other drive. Boot-Repair was updated to fix that as grub2's os-prober just does not work yet with UEFI.

       UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

    
Note that CSM is BIOS/legacy  boot mode.

 *UEFI Compatibility Support Module* (*CSM*)

---

### Post by Nesaskewatch on 2013-01-31
A quick update: I was drawn away for the past few days by business. I will be attempting the install later today and will post back with results in due course.

Edit: I should add that the drive on my new system failed an hour ago, so the install will have to wait until I get a new one. Just one of those things that happens I am told. lol It never rains when it pours.

---

### Post by Nesaskewatch on 2013-01-31
> **oldfred said:**
> Two others with Asus which may have similar UEFI even if different models.

       Asus S46CA Ultrabook Problems with Windows Recovery and grub after dual-boot install with Ubuntu 12.04
[http://ubuntuforums.org/showthread.php?t=2098477](http://ubuntuforums.org/showthread.php?t=2098477)
       Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
Those links were extremely informative Fred, in particular the f9 trick. However, I will be doing the install in the morning -- after a night's rest. I am seeing spots in my peripheral vision and have lost voluntary control of my legs. Time to sleep. The new drive is in and 8 is shrunk down to minimum size. BTW, here is a screenshot of the disk, pre-install.

[IMG]http://i.imgur.com/05tcGzc.png?1[/IMG]

I'm going to format the 97Gb unallocated space as ntfs /share and use the larger (~297 Gb) space for the Ubuntu partitions. I wonder what msftres is there for? Ya think uncle Bill is hiding in there? lol 

Thanks again for the help Fred. I have learned a lot these past few days.

Edit: I should add that this machine is extremely snappy and quick, even running Ubu off the USB drive. USB 3.0 is your friend.

---

### Post by ShaunShaun on 2013-02-01
As someone coming over from Windows I am dismayed that I cannot install Ubuntu after a week to trying on a new Dell machine (one of the most popular PC manufacturers) with W8 pre-installed. I want Linux but don't want to get rid of W8 for Word etc. 
 
Support is terrible. So much on the web is just wrong or out-of-date. An pointing someone like me to Microsoft techie pages showing the layout of a boot sector cannot make any sort of business sense. Is this really supposed to be a replacement for Windows? I've even tried to get someone locally to install it for me but the only one I found wanted £155+ and speaking to him I had no faith he could do the job.
 
Is there an alternative to using this forum? Does anyone know someone in London who can physically help me?

---

### Post by darkod on 2013-02-01
So, it's our fault now that MS again created a well hidden conspiracy to stop easy dual booting with the new UEFI + Secure Boot setups?

Instead of blaming linux you might want to consider talking to the machine manufacturer and MS for making windows-only machines. On top of that, MS doesn't even ship install media for the OS that you paid license for. If you had win8 install media, you could install it in legacy mode for example because legacy dual boot is much easier than uefi dual boot.

See if something here can help you:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The main points are:
1. Go into BIOS and disable Secure Boot.
2. Make sure you shrink windows partitions using windows Disk Management so that you have unallocated space for ubuntu. DO NOT do it with the ubuntu installer.
3. Make sure you boot the ubutnu cd/usb in UEFI mode, not in legacy mode. Only that way it can install uefi dual boot.

Good luck. I build my own machines since ages ago so I don't depend on what MS and manufacturers allow me to use, and what not.

---

### Post by sudodus on 2013-02-01
> **ShaunShaun said:**
> ...
 
Is there an alternative to using this forum? Does anyone know someone in London who can physically help me?

Let us hope so (and that you get hands-on help)!

Many people are helped for free by volunteers at the Ubuntu Forums. I think that you might succeed too after some more trying, so don't give up your own thread here!

---

### Post by Nesaskewatch on 2013-02-01
I am impressed with the help I am getting here. I had no idea what to do and was given everything I needed. Just don't let your frustration take over your reason and you will find it much easier to get the help you want. As is said the problem is down to M$ and the manufacturer, not Ubuntu.

Anyway. I have a quick question... Should I use the default selection for boot loader location? The installer selects sda1 which is listed as efi. I am used to putting grub on sda.

Thanks for any quick answers. (I am in the installer right now)

---

### Post by oldfred on 2013-02-01
With UEFI all systems install boot loaders into separate folders in the efi partition. You only can have one efi partition per drive.  It is somewhat like having multiple MBR's in the old BIOS.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

    
In the old MBR configuration, there were the sectors between the MBR and the first partition. But with gpt that space does not exist. Grub used to hide core.img or old grub had stage 1.5 in that space. But Windows also had software like DRM and virus checkers put serial numbers or other hidden data there. Since gpt does not have tha space the MSR is just some unformated space that must be just before the main NTFS partition for the same use.

---

### Post by Nesaskewatch on 2013-02-01
Thanks Fred. But just to be sure, the answer is yes? I install the boot loader to the default, sda1 (efi). Correct?

---

### Post by oldfred on 2013-02-01
Yes. Install to the efi partition.

I think someone posted that it defaulted to that anyway as it is the only valid choice. There would not even be a reason to install to a partition and chainload like we used to do as the efi partition can have all the boot loaders you want.

---

### Post by Nesaskewatch on 2013-02-01
That's what I figgered. Thanks Fred. I installed Ubuntu then installed/ran Boot-Repair and everything is working perfectly. Here is the result:

[IMG]http://i.imgur.com/a50UI4Z.png?1[/IMG]

I also had to reformat the /share partition as I forgot to specify ntfs. Aside from that the install went without a hitch, thanks to you. I am very grateful for your patience and help. It is a tremendous relief to have Ubuntu again. I did start to get used to 8 and it is definitely an improvement in many respects, but I still prefer Ununtu. It is really snappy on this Asus. I have never had such a quick system. Also, it is a good feeling to have complete control over my computer again. Many thanks to Yann as well. His little program is a real gem.

Cheers Fred!

---

### Post by oldfred on 2013-02-01
Glad you got it working. :)

---

### Post by Nesaskewatch on 2013-02-01
I went to write up a summary and after going back into the bios to get acurate spelling I restarted but Ubuntu will not boot now. Just hangs on a black screen with a cursor at the top left. I have to hold the power button to get it to shutdown. I am now back on the live usb drive. I tried Boot-repair but it only offers to restore the re-written files. Should I do that, then have it rewrite it again?

---

### Post by Nesaskewatch on 2013-02-01
Well, I got it back up again by booting windows, then booting Ubu again and holding the control key. I guess I dare not go into the bios again. Or is it booting the USB? Regardless, the boot loader is rather easily knocked over. I will still come back and post the summary... lol

---

### Post by Nesaskewatch on 2013-02-01
Here is a brief summary of how I installed Ubuntu 12.10 to dual boot with Windows 8 on an Asus N56VJ-SH71-CD with UEFI. (Maybe works on all N56 models?) This assumes you have already used windows partition manager to resize 8 and opened up some unallocated space for Ubuntu. Also assumes you already understand partitioning and have planned out your installation. (sda?, /home or not? etc)

1, Make bootable 12.10 USB drive (Fastest) or CD/DVD.

2, Hold F2 during boot and enter bios. Under "Boot" heading, enable "Launch CSM". That will automatically disable Fast Boot as well. Under "Security" heading, disable "Secure Boot Control". Save and exit bios.

3, On restart, hold esc key and select "UEFI: SMI USB DISK 1100" for usb boot or select the Matsushita optical drive for the cd/dvd. It will then boot the live usb/cd/dvd. You can now install Ubuntu.

4, Go [here]("https://help.ubuntu.com/community/Boot-Repair") and run Boot-Repair. (Use advanced options)

You should have a windows 8/Unutu 12.10 dual boot now.

---

### Post by sudodus on 2013-02-01
Thanks for sharing your solution with the Ubuntu Forum :-)

I'm reading and learning (and I think many other people do the same)

---


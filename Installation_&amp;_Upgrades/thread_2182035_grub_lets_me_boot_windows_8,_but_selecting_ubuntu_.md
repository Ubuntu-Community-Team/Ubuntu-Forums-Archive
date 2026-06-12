---
title: "grub lets me boot windows 8, but selecting ubuntu hangs"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by bBAzhnk on 2013-10-19
I purchased a new sony viao pro with windows 8 pre installed.  I tried to install ubuntu 13.10 to dual boot with windows 8.

I added a 300MB partition as /boot and a 4gb partition as swap and a primary partition as /.  That is along with the existing windows partitions which I left.
The installation didn't set up grub correctly, so I followed the boot repair steps here [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) using my bootable usb thumb drive - booting into Ubuntu from the thumb drive worked fine.  Boot repair suggested that I disabled secure boot in the bios and try again so I did.  This is my latest attempt:

[http://paste.ubuntu.com/6267255/](http://paste.ubuntu.com/6267255/)

I can boot into windows 8 from grub by selecting "Windows Boot UEFI loader". Selecting "Ubuntu" however, just seems to hang with a purple screen.
I'm not sure what to try next.

Many thanks in advance for the advice :)

---

### Post by rihikz on 2013-10-19
There is a  big possibility that it is a problem with Ubuntu itself. Is the hardware compatible? Was It installed successfully?

---

### Post by bBAzhnk on 2013-10-20
> **rihikz said:**
> There is a  big possibility that it is a problem with Ubuntu itself. Is the hardware compatible? Was It installed successfully?

Thanks for the reply.  The install ran through normally.  There are other people online that have installed ubuntu on the same sony vaio pro that I bought so I assume the hardware is compatible. And besides, when I boot from the live cd, well technically the usb stick, I can use use ubuntu just fine, the trackpad, wireless, screen, everything works fine.  My very vague theory is that grub hasn't configured booting to linux correctly (when I used the 'recommended repair option' in boot repair) whereas it has successfully done it for windows, but I don't know the details of how that works.  I am hoping just fiddling with some settings in the advanced options of boot repair will fix this but I'm not sure where to start.

Cheers :)

---

### Post by fantab on 2013-10-20
Did you install Ubuntu in UEFI mode? To install Ubuntu in UEFI mode you have to boot Ubuntu Live USB in UEFI mode. If you boot in UEFI mode then you will see black screen with options otherwise you will see regular Ubuntu color.

Here's your problem:
[QUOTE= from bootinfo summary]Windows is hibernated, refused to mount.
Failed to mount '/dev/sda5': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda5 /mnt/boot-sav/sda5
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda5': Operation not permitted[/QUOTE]

In Windows 8 there is a 'Fast Startup' feature which does not let the Windows to 'shutdown' instead it keeps it in a state of Hibernation for fast startups. Technically windows is not shutdown even though you have shut it down.
You need to [DISABLE FASTSTARTUP]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"). And try again. If possible re-install ubuntu in UEFI mode.

Also that 300MB /boot partition is a waste with UEFI booting... remove it.

---

### Post by bBAzhnk on 2013-10-20
> **fantab said:**
> Did you install Ubuntu in UEFI mode? 

I have never change the UEFI setting in the bios if that is what you mean.  I did disable secure boot in the bios because I read that that could be a problem.

> **fantab said:**
> 
You need to [DISABLE FASTSTARTUP]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"). And try again. If possible re-install ubuntu in UEFI mode.

Also that 300MB /boot partition is a waste with UEFI booting... remove it.

Ok, thanks.

I disabled faststartup as per the link and reinstalled ubuntu.  However, it booted straight into Ubuntu.  So I booted from the live cd, and ran boot repair - I got this:

[http://paste.ubuntu.com/6270525/](http://paste.ubuntu.com/6270525/)

Which didn't have the same "Windows is hibernated" error that you pointed out earlier, so I was hopeful...

It gave me grub, but with no option to boot to windows :(.  So I selected Ubuntu, but it then said "Gave up waiting for root device" and gave me an initramfs prompt.  I couldn't even shutdown with 'shutdown', so I physically restarted, and when I choose Ubuntu in grub now, I just get a purple screen...

Given that I couldn't boot into windows 8 or ubuntu, I thought I would try the windows recovery usb.  However, that can't do a 'refresh' because it says 'The drive where windows is installed is locked'.  I can still boot from the linux usb though...

Not that I am sure what to do next.  Maybe I can get windows 8 back by doing a full recover instead of the refresh option?  Any advice would be appreciated, thanks.

---

### Post by oldfred on 2013-10-20
When you reinstalled, it looks like you used the erase Windows and just have Ubuntu option. That also eraes the recovery partition, so your backup is all you have. You did make a backup of Windows and backup of the vendor recovery?
If you do not have backups you can contact vendor. Some may send recovery DVD set (not full Windows installer) that was recovery or may just charge a nominal shipping fee. Otherwise you have to purchase a full Windows install.

What video chip do you have? You proably need boot options to get video correct.

       Sony Vaio T13 
[http://ubuntuforums.org/showthread.php?t=2127699](http://ubuntuforums.org/showthread.php?t=2127699)
Sony T & Intel SRT ubuntu 12.10 & Windows 8 oem 
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Sony Vaio [SOLVED] dual boot ubuntu 12.10 & windows 8 problem 
[http://ubuntuforums.org/showthread.php?t=2094761](http://ubuntuforums.org/showthread.php?t=2094761)
 Sony SVE15125CXS Notebook  Only could Install in BIOS mode, Boot-Repair to UEFI dual boot works
[http://ubuntuforums.org/showthread.php?t=2126389&p=12562570#post12562570](http://ubuntuforums.org/showthread.php?t=2126389&p=12562570#post12562570)
Sony VAIO E Series Windows 8/Ubuntu 12.10 Dual Boot, EFI help UEFI screens shown
[http://ubuntuforums.org/showthread.php?t=2087991](http://ubuntuforums.org/showthread.php?t=2087991)

---

### Post by bBAzhnk on 2013-10-21
> **oldfred said:**
> When you reinstalled, it looks like you used the erase Windows and just have Ubuntu option. That also eraes the recovery partition, so your backup is all you have. You did make a backup of Windows and backup of the vendor recovery?


Thanks oldfred.  However, I specifically didn't select anything that said 'erase', it said 'reinstall', the option fantab advised me to use.

As I mentioned earlier, I had tried the windows recovery USB that I created - so I don't think I should need to buy windows again or anything.  It [COLOR=#000000]said it can't do a 'refresh' because it says 'The drive where windows is installed is locked'.  So I booted with the windows 8 USB and I tried doing the full reset - however it says 'Unable to reset your PC.  A required drive partition is missing'.  I presume that refers to the recovery partition you referred to.

I tried a system restore and it says 'To use System Restore, you must specify which Windows installation to restore.'  And I saw no clear way to proceed, so I eventually used the full vaio care restore option to get windows back.

I've tried installing several more times in a few different ways after reading the links, with no success.  Boy they have really made this tricky.  I dual booted linux the first time in 1999 when I was a kid no problem....this UEFI stuff is killing me.  I suppose that wasn't on a laptop though.  I haven't even managed to get grub back since I reinstalled windows/disabled fastboot. I will continue trying this evening/tomorrow.

Thanks for trying to help guys.[/COLOR]

---

### Post by fantab on 2013-10-21
You probably used the option 'Replace Windows' or something of that sort, when you re-installed. You should use the option, "Install Alongside Windows" to automatically install Ubuntu and letting its installer doing the partitions or 'Something Else' to manually guide the install to whatever partitions you want to install to.

If you want to use the installer then the installer needs to see some 'Unallocated Spcae' to work with. 

UEFI is not difficult, its just new.
You might want to [**Read Here**]("http://ubuntuforums.org/showthread.php?t=2147295"), about UEFI and dual-booting.

---

### Post by oldfred on 2013-10-21
Windows needs unallocated space or the set of partitions that it needs for UEFI. Since a new install probably easiest just to delete the Linux partitions. Install Windows, turn off secure boot & fast boot, shrink Windows with Windows tools, reboot Windows so it can make repairs and then reinstall Ubuntu into the free unallocated space you created. 

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by bBAzhnk on 2013-10-21
> **fantab said:**
> You probably used the option 'Replace Windows' or something of that sort, when you re-installed. You should use the option, "Install Alongside Windows" to automatically install Ubuntu and letting its installer doing the partitions or 'Something Else' to manually guide the install to whatever partitions you want to install to.

If you want to use the installer then the installer needs to see some 'Unallocated Spcae' to work with. 

UEFI is not difficult, its just new.
You might want to [**Read Here**]("http://ubuntuforums.org/showthread.php?t=2147295"), about UEFI and dual-booting.

No fantab.  As I explained, I used the option 'reinstall' because you suggested I do so.  The options were:


a) reinstall ubuntu
b) install ubuntu alongside ubuntu
c) erase ubuntu and reinstall
d) something else


When installing the first time, I used 'something else', and set up the partitions - I got to the stage of having grub but with fast startup enabled as you pointed out.  You suggested I reinstall, so I chose option a). That left my laptop in a state where the only thing I could do was use the vaio recovery to get windows back.


I have read the suggested links so far but haven't had any success.  Fantab - you posted the same link that I already read from oldfred, I don't believe I have missed any steps out, but I haven't had any success.  Since I reinstalled windows, I haven't even been able to get back to the point that I was originally at when I posted this thread i.e. booting into grub.


I will continue to read and to experiment...

---

### Post by bBAzhnk on 2013-10-21
> **oldfred said:**
> Windows needs unallocated space or the set of partitions that it needs for UEFI. Since a new install probably easiest just to delete the Linux partitions. Install Windows, turn off secure boot & fast boot, shrink Windows with Windows tools, reboot Windows so it can make repairs and then reinstall Ubuntu into the free unallocated space you created. 

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Thanks oldfred.  I tried all of that - pretty good summary of the article.  The step I had missed out yesterday was the restarting of windows after the resize.  I tried that today though, but it didn't seem to make a difference.  I am giving up for tonight, thanks guys.

---

### Post by bBAzhnk on 2013-10-23
> **fantab said:**
> UEFI is not difficult, its just new.
You might want to [**Read Here**]("http://ubuntuforums.org/showthread.php?t=2147295"), about UEFI and dual-booting.

I don't think it is fair to say that it is not difficult.  If it was easy, there wouldn't be so many people asking questions about it.

I had to disable native command queuing and swap out the microsoft sony vaio efi binary because it is hardcoded to use the windows one.

I fixed my issue using this tutorial:
[http://www.slideshare.net/Tinydile/vaio-pro13-win8ubuntu1310uefi](http://www.slideshare.net/Tinydile/vaio-pro13-win8ubuntu1310uefi)

If somebody asks about a dual booting a sony vaio pro, I recommend that - it is full of references as well.

---

### Post by fantab on 2013-10-23
I am glad you fixed your issue.

There are so many posts regarding UEFI not because its complicated, but because people don't understand it, and to top it pre-installed Windows 8 has complicated if further with its useless 'Secure Boot' feature.

---


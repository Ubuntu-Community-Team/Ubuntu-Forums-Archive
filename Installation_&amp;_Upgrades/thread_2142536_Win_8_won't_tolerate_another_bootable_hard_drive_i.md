---
title: "Win 8 won't tolerate another bootable hard drive in system"
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by arrowcatcher on 2013-05-06
Have recent H8-1420t i7 "ENVY" desktop.  Once I got v. 13.04-64 running on a second installed HD, I ran into a new problem I've never seen before.

Evidently, at least in this machine, if you have any other bootable HDs connected to no matter what order of mobo SATA sockets, Win 8 will try to start and fail giving a "Preparing Automatic Repair" message.  This is effectively the new BSOD message!  Win 8 will not tolerate any other bootable HDs in the machine.

If I have only my Ubuntu drive plugged, then that's what boots in Legacy boot mode.  If I have only the Win 8 HD plugged, then it boots fine in Legacy mode.  But if I have both drives plugged and simply turn the machine on, then the failure above happens no matter how the drives are plugged in the SATA sockets.  This really startled me at first.  Windows 8 locks down the machine.

To get a dual-boot machine then, I leave both drives plugged and simply tell the F10 BIOS that the Ubuntu drive is "hidden" in order to successfully boot Win 8, or else I can unhide the W8 drive and start the Ubuntu HD with the F9 boot menu to get Linux.  That way I can see the W8 file system in Ubuntu.  Whew!

I don't see any neater workaround for this incredible new problem.

It makes me very unhappy that Windows 8 behaves this way.  I'm afraid to install Ubuntu on my W8 Lenovo G780 laptop which only has 1 HD.  I worry about having to spend a lot of time getting the machine to run again.  It's safer when there are separate HDs.

No wonder the Hispalinux group in Spain has petitioned the EU re: MS monopoly.

---

### Post by carl4926 on 2013-05-06
Is there a boot flag on the windows boot partition ?

---

### Post by arrowcatcher on 2013-05-06
> **carl4926 said:**
> Is there a boot flag on the windows boot partition ?

I know about boot flags as a concept but have not delved into it.  I tried to keep the Windows 8 HD untouched and separate from my Ubuntu install, but somehow in the process the W8 HD's boot structure may have gotten modified.  The W8 HD boots as normal when it is the only drive in the machine.  When the other bootable (Ubuntu) HD is present, then W8 fails to boot.  I have to hide the Ubuntu HD in the BIOS.

---

### Post by haqking on 2013-05-06
> **arrowcatcher said:**
> I know about boot flags as a concept but have not delved into it.  I tried to keep the Windows 8 HD untouched and separate from my Ubuntu install, but somehow in the process the W8 HD's boot structure may have gotten modified.  The W8 HD boots as normal when it is the only drive in the machine.  When the other bootable (Ubuntu) HD is present, then W8 fails to boot.  I have to hide the Ubuntu HD in the BIOS.

cant you use your BIOS boot menu to choose.

Uusally something like F8 or similar and choose what you want to boot, it is what I do for a Win 7, Win 8 and multiple Linux machine with seperate SSD

---

### Post by pqwoerituytrueiwoq on 2013-05-06
sata order does not mean boot order, on my laptop i set the sata 2 port as 1st boot instead of sata 1, some BIOSes will remember the drive name instead of the port number
i was not aware you could hide a hdd in the bios, you could use a hot swap rack with a power button as a workaround, the cheapest one at newegg will work for that (snt-125 is the model)
could this be a secure boot issue?

---

### Post by oldfred on 2013-05-06
Is your Envy booting with UEFI and is the second drive with Ubuntu also UEFI or BIOS? Best if both are either UEFI or both BIOS.
 Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

      
 UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

Is your Lenovo a UltraBook as that adds complications of Intel SRT using RAID and dual video.

 Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)

---

### Post by arrowcatcher on 2013-05-07
> **pqwoerituytrueiwoq said:**
> sata order does not mean boot order, on my laptop i set the sata 2 port as 1st boot instead of sata 1, some BIOSes will remember the drive name instead of the port number
i was not aware you could hide a hdd in the bios, you could use a hot swap rack with a power button as a workaround, the cheapest one at newegg will work for that (snt-125 is the model)
could this be a secure boot issue?

Using the F9 Boot Menu and F10 BIOS I can boot either W8 or Ubuntu and as well see my W8 file system in Ubuntu.  It's just not very elegant the way I have to do it, and I had to do a lot of screwing around on my own to discover the solution.

In my HP H8-1420t I can - fortunately - hide drives in the BIOS.  Otherwise I'd be screwed.  I have to hide the Ubuntu drive in order to boot W8.  Geez!  W8 can't read the Ext4 file system anyway.

---

### Post by oldfred on 2013-05-07
Post BootInfo report. But it sounds like you have Windows in UEFI and Ubuntu in BIOS. Each writes system data to drive for booting differently so the only way to dual boot is the way you are, or cold boot.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by arrowcatcher on 2013-05-07
> **oldfred said:**
> Post BootInfo report. But it sounds like you have Windows in UEFI and Ubuntu in BIOS. Each writes system data to drive for booting differently so the only way to dual boot is the way you are, or cold boot.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

The machine is set up to boot both Windows and Ubuntu in "Legacy" BIOS mode.

Thanks I took a look at that, but at least for this desktop I'm going to take a break since it will successfully boot either W8 or Ubuntu as it is.  The process is just very clunky using the BIOS and Boot Menu.  I spent many hours getting this to work and don't feel like triggering another event requiring more hours now that I'm out of the weekend.  Again, W8 and Ubuntu are on 2 separate HDs, and both boot in BIOS mode, or at least that's the way it's set up to do.  On top of the boot hassle, I also describe in another thread how it was first necessary to install 12.10, update it, and then upgrade to 13.04.  The 13.04 couldn't be directly installed, either 32 or 64 bit versions, since it would not support any networking.  Installing 12.10 first did the trick since it did support the Raling WiFi which 13.04 would not.  This was more hours of effort, but now both OS's work well once booted up.  Whew.

I also wish to install Ubuntu on my newish Lenovo G780 W8 notebook, but now I'm gun shy since it only has one HD.  I can't get tied up for hours again trying to get it working.  This is all disappointing considering my past experience for some years dual booting Linux and Windows.

---


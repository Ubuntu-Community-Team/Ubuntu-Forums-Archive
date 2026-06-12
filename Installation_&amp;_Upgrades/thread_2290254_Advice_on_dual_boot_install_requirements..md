---
title: "Advice on dual boot install requirements."
date: 2015-08-10
forum: Installation &amp; Upgrades
---

### Post by makem2 on 2015-08-10
The computer in question is an HP 15-209na with Win 8.1 in UEFI mode and 12GB of memory. It has CSM but a warning that if enabled the system may not boot.

It has the following partitions:

1. 650mb Recovery
2. 260mb EFI
3. 147GB Win 8.1 0f which 46% is spare
4. 670GB Data of which 29% is spare
5. 73GB of unallocated space for Kubuntu
6. 24GB Recovery

I am the only user of this machine and my profile is totally on the Data partition. I don't use it for gaming.

Does the 73GB seem reasonable as linux can use the Data partition? Or, as linux can use the data partition where I would like to store my linux 'profile',  does the 73GB seem to much?

Bear in mind that as soon as I am happy that I can transfer totally to linux, I will wipe the win 8.1 off. I may also need to change flavours.

I have a some concern about drivers. I have not investigated yet but I think HP will not have any suitable for this model.

---

### Post by TheFu on 2015-08-10
Linux required 2 partitions - these cannot be NTFS or fat-anything.
My primary desktop is 15G, so whether 73G is "enough" is really a question about how much crap you will load.  25G is HUGE for the OS and applications.  Your HOME can be 1MB to 25TB ... just depends on what you store there.
Plus you need a swap partition - sizing of that has rules of thumb based on what you do - encryption, hibernation, standby, and the total amount of RAM. The old swap size rules are mostly useless for most people.  Oh and if you use encryption, you'll need at least 1 more partition.

Before you load anything, make a liveCD/flash-drive and boot off that. Try it out - test networking, wifi, touchpad, audio, and external monitor resolutions .... any issues?

I suspect that you won't ever want to wipe Win8 if this is your only machine. There are a few things that I still need windows for and I'm not a gamer and run Linux almost full time for the last 8 yrs and have been a Linux and Unix admin since 1993.  It is just a few things, but I still need Windows7 for now.

---

### Post by oldfred on 2015-08-10
HP is not UEFI friendly.
They have modified UEFI to also use description in Booting. And only valid description is "Windows". 
That is not per UEFI standard and Ubuntu has a policy statement against it.
But there are several work arounds depending on your configuration.

UEFI systems also have a fallback or hard drive boot entry. Originally it was just for external drives, but updates included internal drives. The hard drive entry is /EFI/Boot/bootx64.efi. So we copy shimx64.efi into  /EFI/Boot and rename to bootx64.efi.
Another work around is to add an ubuntu entry to Windows BCD.
Some like graphical boot managers and use rEFInd which originally was more for Macs but works with all UEFI systems.
Details in link in my signature below or if you need help post back.
       HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[URL="http://ubuntuforums.org/showthread.php?t=2218154"]http://ubuntuforums.org/showthread.php?t=2218154
[/URL]
 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

[URL="http://ubuntuforums.org/showthread.php?t=2218154"]
[/URL]

---

### Post by makem2 on 2015-08-11
It would appear that HP are working hand in glove with MS.

At this stage I just need to know that if I enable legacy boot support and attempt a dual boot install of buntu I will be able to get back to win 8.1. I think it best to consult the suppliers and HP diretly for support.

I had to have 3 computers from HP before I received one which did not have some problem so I think the suppliers known me well ;) This is not my only machine and I also have a dual boot ubuntu on one with win 7 but it is an asus netbook I use when travelling.

There is little point in trying a live buntu to check driver support if I cannot install the whole thing.

[edit]
**Dual booting**

 But what about dual booting Windows and Linux? Considering  Windows makes use of Secure Boot, won&#8217;t that hamper your ability to boot  both platforms? Not if you&#8217;re using Windows 8 or 8.1. With these  particular iterations of Windows, you can actually disable Secure Boot  and still boot the OS.[URL="https://www.linux.com/learn/tutorials/821007-how-to-install-linux-on-a-windows-machine-with-uefi-secure-boot"]

[https://www.linux.com/learn/tutorials/821007-how-to-install-linux-on-a-windows-machine-with-uefi-secure-boot](https://www.linux.com/learn/tutorials/821007-how-to-install-linux-on-a-windows-machine-with-uefi-secure-boot)

[/URL]This link has all the necessary information:

[http://support.hp.com/us-en/document/c03653226](http://support.hp.com/us-en/document/c03653226)

---

### Post by grahammechanical on 2015-08-11
> Considering  Windows makes use of Secure Boot, won&#8217;t that hamper your ability to boot  both platforms?

Actually, Ubuntu was the first Linux distribution to give users the ability to install and load Ubuntu with secure boot enabled. Ubuntu did this as far back as the release of Ubuntu 12.10. Some motherboards do cause problems and so some of us recommend turning Secure Boot off as a policy.

Complications come when manufacturers, for whatever reason, do not follow the agreed upon specifications for both Secure Boot and UEFI. The rule is this:

If Windows 8.1 is installed in EFI mode then Linux has to be installed in EFI mode. Think of it as a law of the Universe. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by makem2 on 2015-08-11
> **grahammechanical said:**
> Actually, Ubuntu was the first Linux distribution to give users the ability to install and load Ubuntu with secure boot enabled. Ubuntu did this as far back as the release of Ubuntu 12.10. Some motherboards do cause problems and so some of us recommend turning Secure Boot off as a policy.

Complications come when manufacturers, for whatever reason, do not follow the agreed upon specifications for both Secure Boot and UEFI. The rule is this:

If Windows 8.1 is installed in EFI mode then Linux has to be installed in EFI mode. Think of it as a _**law of the Universe**_. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

MS LAW?

By using the option to turn off secure booting and enabling legacy does this mean install will be in EUFI mode?

---


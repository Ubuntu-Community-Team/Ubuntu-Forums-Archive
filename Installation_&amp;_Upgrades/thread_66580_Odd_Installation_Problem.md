---
title: "Odd Installation Problem"
date: 2005-09-17
forum: Installation &amp; Upgrades
---

### Post by zoob on 2005-09-17
Hi,

I am new to Linux and wonder if someone can point me in the right direction to trouble shoot my problem.

System

Intel D845BG motherboard
Intel 2.5GHz Processor
512MB RAM
Maxtor 6Y080L0 -
Partitioned and formatted NTFS. Windows XP Pro SP2
C: = System D: = Data jumpered as Master

Maxtor 6Y080L0 - ubuntu Linux with grub
jumpered as Slave

Lite-On JMS XJ-166S DVD-ROM drive
jumpered as Master

Lite-On DVDRW SOHW-1633S DVD-RW
jumpered as Slave

PCI USB 2.0 Card
IEE1394 FireWire Card
Hauppage WinTV Card
SB Live! Value Edition
External SimpleTech 160GB USB HDD
Apple Ipod 15GB
HP 990c Printer
HP 3400c Scanner
Motorola USB Cell phone cradle

This setup was working flawlessly under Hoary & Breezy dual booting with grub. It was acting in Windows like the first Maxtor drive was heading south so I replaced it with a Seagate ST380011A HDD. I also replaced the DVD-ROM as it was not occasionally not reporting itself in BIOS or Windows XP. I ghosted the data from the Maxtor to the Seagate knowing I would have to reinstall ubuntu to fix the grub.

I installed Breezy and all went well until shut down when Breezy scrolled text after the shutdown command. Then on reboot it would hang at Creating hotswap. If I let it go 5 minutes it text scrolled again. I installed and reinstalled at least 4 times.

I grabbed my Hoary CD. Installed okay it hung at a different spot on installation. Finally installed it but it blows up in the very same now too. I think the text that I can see is saying something about clearing interrupts. Every time I installed I repartitioned, formatted and reinstalled grub.

Windows works better than it has in a long time but I miss my ubuntu. I was just starting to get familiar with Linux as ubuntu was the most friendliest version I have ever run. Does anyone have an idea of where I should start short of wiping out my XP drive which I need so dearly? Any suggestions would be helpful. Thanks.

zoob


 ](*,)

---

### Post by nic2 on 2005-09-18
Try using the failsafe (default) settings in the BIOS.

Hope this works for you (resolved a similar problem for me a while ago).

---

### Post by zoob on 2005-09-18
Thanks for the tip but still no go.  :(

zoob

---

### Post by mlomker on 2005-09-18
> I ghosted the data from the Maxtor to the Seagate knowing I would have to reinstall ubuntu to fix the grub.


Not that it helps right now, but that isn't correct.  There are two grub commands that would have fixed that up--you simply reconfigure grub by booting up to a livecd (knoppix or whatever).

Do you mean that it hangs while trying to load hotplug or when creating swap?  Have you tried booting into the 'rescue' option.  Have you tried booting a livecd to see if it can see your drive?

Was the old drive the same type or did you switch from IDE to SATA or something like that?

---

### Post by zoob on 2005-09-18
I wasn't sure how to fix grub, so I thought I would clean install Breezy thinking it would configure the grub correctly again.  And grub gives me the menu just fine.  It is hanging currently with Breezy at "loading hotswap subsystem" or something similar.  

I just tried booting with with XP CD and did a fixboot c: .  It said it transfered okay.  I thought this may overwrite grub and I would try a fresh install again, but grub reappeared like before.  I am really confused now!  %)

zoob

---

### Post by mlomker on 2005-09-18
> XP CD and did a fixboot c: .  

fdisk /mbr

---

### Post by zoob on 2005-09-18
With NTFS?  I thought FDSIK was dead in NTFS?

zoob

---

### Post by mlomker on 2005-09-18
Nope.  I'm actually an MCSE at my day job, fwiw.

---

### Post by zoob on 2005-09-18
[QUOTE=mlomker]fdisk /mbr[/Q]

I could not find FDISK but FIXMBR did the trick!  I gonna try another clean Breezy install.  

Thanks,

zoob

---

### Post by zoob on 2005-09-18
[QUOTE=mlomker]fdisk /mbr[/QUOTE]

I could not find FDISK but FIXMBR did the trick! I gonna try another clean Breezy install. 

Thanks,

zoob

---

### Post by zoob on 2005-09-18
[QUOTE=mlomker]Not that it helps right now, but that isn't correct.  There are two grub commands that would have fixed that up--you simply reconfigure grub by booting up to a livecd (knoppix or whatever).

Do you mean that it hangs while trying to load hotplug or when creating swap?  Have you tried booting into the 'rescue' option.  Have you tried booting a livecd to see if it can see your drive?

Was the old drive the same type or did you switch from IDE to SATA or something like that?[/QUOTE]

Darn!  Still stuck at "loading hotplug".  Every thing gets partitioned, formatted loaded, rebooted starts to load a hangs.  I really don't understand.  This is a stable system and just because I swapped out a HD I lose my ubuntu.  Any other suggestions?  The system is back to straight XP with the Maxtor with trmnants of ubuntu.  Try another distro?

zoob

 ](*,)  ](*,)  ](*,)

---

### Post by mlomker on 2005-09-18
It's probably hanging on loading one particular device driver.  You could try temporarily disabling hotplug to see if it'll boot.

What you'll want to do is boot up on a Knoppix cd (my preference, but use whatever you have).  Then mount your Ubuntu drive and **chmod 600 /etc/init.d/hotplug**.  That'll make it so hotplug can't run.

When you reboot try to go into 'rescue' mode and see if you can get to a prompt.  From there I'm not really sure how you'd go about troubleshooting which driver is the problem.   I'd assume it's IDE-related but not sure.

To be honest, I'd probably be downloading a copy of MEPIS if I were you...so many distros out there.  I dig Kubuntu a lot but linux is linux.

---

### Post by zoob on 2005-09-19
[QUOTE=mlomker]It's probably hanging on loading one particular device driver.  You could try temporarily disabling hotplug to see if it'll boot.

What you'll want to do is boot up on a Knoppix cd (my preference, but use whatever you have).  Then mount your Ubuntu drive and **chmod 600 /etc/init.d/hotplug**.  That'll make it so hotplug can't run.

When you reboot try to go into 'rescue' mode and see if you can get to a prompt.  From there I'm not really sure how you'd go about troubleshooting which driver is the problem.   I'd assume it's IDE-related but not sure.

To be honest, I'd probably be downloading a copy of MEPIS if I were you...so many distros out there.  I dig Kubuntu a lot but linux is linux.[/QUOTE]
 I think I may have found something.  Right after ubuntu loads the kernel where it says audit the very next line shoots a super quick error message.  It took me many tries to catch it but here it is:

/ INT: 63 : cannot open /sys/bus/scsi/devices/*/type: no such dev

I do not have any SCSI devices on my system except I used to see my firewire card for my Ipod.

Does this ring any bells?

Thanks,

zoob

P.S.  I cannot boot rescue.  And both HDD drives are ATA 133.  No SATA on this mobo.

---

### Post by mlomker on 2005-09-19
> / INT: 63 : cannot open /sys/bus/scsi/devices/*/type: no such dev

I've seen similar errors posted in other threads.  That error shows up on some systems running Breezy.  SATA drives are considered to be 'scsi' by linux, so that could be a problem.

Perhaps you should try Hoary again and see if that does something different?

---

### Post by zoob on 2005-09-19
[QUOTE=mlomker]I've seen similar errors posted in other threads.  That error shows up on some systems running Breezy.  SATA drives are considered to be 'scsi' by linux, so that could be a problem.

Perhaps you should try Hoary again and see if that does something different?[/QUOTE]

I have no SATA capabilities on this mobo.   ](*,)  ](*,)  ](*,) 

Thanks,

zoob

---

### Post by mlomker on 2005-09-19
[QUOTE=zoob]I have no SATA capabilities on this mobo. [/quote]

Try booting Knoppix?  I wonder if another distro would work for you?  I'm a KDE-guy, so MEPIS looks pretty nice to me and it's still debian.

---

### Post by mlomker on 2005-09-19
[QUOTE=zoob]I could not find FDISK but FIXMBR did the trick! I gonna try another clean Breezy install. 
[/quote]

Right-o.  My memory operates on fuzzy-logic.  LOL.

---

### Post by zoob on 2005-09-19
[QUOTE=mlomker]Try booting Knoppix?  I wonder if another distro would work for you?  I'm a KDE-guy, so MEPIS looks pretty nice to me and it's still debian.[/QUOTE]
 Success!!!  With both Hoary & Breezy!  I noticed when ubuntu blew up into a raster i could make out it was complaining about intrrupts blocked, mask, vtty0 something and decided to pull my Hauppauge WinTV capture card.  Bada bing!

Thank you for all the help and suggestions.

zoob

---


---
title: "Not giving up yet!"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by BillZog on 2007-01-07
Studied and studied before trying to load Ubuntu: many threads of this forum, web in general, Herman's sites, O'reillly's Nutshell, etc. Finally bit the bullet. Failed first time with regular 6.10 burn (ubuntu-6.10. desktop.i386.iso, then downloaded and burned images of GParted (gparted.livedcd.d.33-0iso) would not work on my system ( used PM to reduce partititons on my old HDD) downloaded alternate Ubuntu load (alternate-i386.iso) and downloaded supergrub-i386.iso (luckily).

Note: my system is an Intel 2Gz, 1024 Memory, an old SATA HDD with a buggy windowsxp installed, a new SATA HDD with a clean install of WXP, and lots of free space (see below).

I finally bit the bullet and tried to install Ubuntu on the free space at the end of the old SATA drive and all went well until I screwed up at the last stage. 

The Ubuntu install brought up a screen that said that all looked good, identified the two HDD's that I had, and said it should be okay to proceed to put Grub on the MBR. (Despite all that I had read, I went along with this advice and, of course, on reboot the first message was something to the order that there was "no operating system present." 

So, like many other nooby I tried everyting I knew about: rescue Windows boot disk, Partition Magic recue disks, and finally supergrub (and that eventually got me back on my new Windows). (Used supergrub to repair my original MBR.) Are we having fun yet??? (Still, I was feeling confident since all my important data was on an external HDD).

So, I used access to my working version of XP to do all the accumulated workIn the process -  Surpise, surprise! -  my external HDD was "unformatted"! But, I was on Windows and was able to backup all my important files to the external drive again. Then, turned it off! (There is a warning here to anyone else reading this and thinking about making the same plunge.)

When I tried to reboot I think I  ended up in grub (which as well as NTLDR and boot.ini are apparently on root of my original drive.) What I got for each alternative in the grub menu, Ubuntu and Windows was - Error 18: Selected cylinder exceeds maximum supported by BIOS, press any key.

So, I went back to supergob again and it eventually got me back to the new windows installation, thus this message. Being a gambler, I have rebooted several times again and grub seems to be referring me to the NT Loader that takes me to the two Windows installations. Ubuntu is there but not available so far. 

Unless I hear other ideas, my next step will be to boot by supergrub again and not only repair the Windows MBR, but Dx the grub boot loader. But, after all this work, I really, really would like to be able to boot Ubuntu. (One thing I am suspicious of is that there seems to be an inconsistency in labeling of the HDD's.  Old drive is consistently listed by BIOS general, PM and elsewhere, as Drive 2 and the new drive as Drive 1 (adjusting for the different ways Windows, Grub, and LInux deal with this) - except that in the BIOS HDD menu this is reversed.)

Any ideas?

OK to DX grub?
Without acccess to Linux, how do I rewrite bios.ini or whatever to address Ubuntu?
Anything I can do to get GParted working?

Or, do I just hang in there with the idea, "If it ain't broke don't fix it"? (Boring.)

BZ

PS Jeex am I glad to see that there is going to be a major Linux conf in Berlin to work on Linux installation issues. No way this is going to hit the real mainstream with a "gate" like this to keep the noobies out. Hope one or more of the advisors on this forum get an invite.


SYSTEM:
3Ghz Pentium built locally, 800MHz Bus, and 1024 memory. According to BIOS.  

HDD (0) = new SATA HDD Western Digital 250G. Partition Magic and Windows list HDD (0) as the &#8220;D&#8221; drive and Boot Drive, (but also listed as &#8220;2nd Drive&#8221; by BIOS)

HDD (1) = the original system SATA HDD  Seagate 80G. Partition Magic and XP list HDD (1) as the &#8220;C&#8221; drive and System Drive, (It is also listed by BIOS as the 1st Drive.) 


Current &#8220;boot.ini&#8221; is:
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect

---

### Post by sdowney717 on 2007-01-07
Fedora Core 6 from Redhat works well.
I have been playing with both Ubunuts and Fedora and Ubunuts keeps on having Xwindows problems on boot up (blank screen). I have yet to see this on fedora.

---


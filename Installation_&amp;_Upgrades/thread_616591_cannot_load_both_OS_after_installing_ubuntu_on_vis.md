---
title: "cannot load both OS after installing ubuntu on vista"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by mohim85 on 2007-11-18
I  have a lenovo laptop with latest config that can help me run vista. I was bugged with all the vista driver problems and tried installing UBUNTU 7.10 in a seperate partition.. After installing Vista on the hard disk...I inserted the Live CD of Ubuntu and did a manual install of ubuntu by allocation 518 mb as SWAP and around 12gb for UBUNTU itself.. After removing the live cd and doing the reboot...i am not able to boot into either vista nor ubuntu.. A screen with F2 and F10 options are only displayed after the reboot, the first option to enter the BIOS and the latter to choose the booting drive.. The worst part is that i am not able to load neither the Live cd nor the LENOVO rescue and recovery disc which allows me to get back the factory settings, which includes vista.

To be simple, now i have access only to the BIOS.. Niether can i access my vista or UBUNTU OS from the hard drive  nor can i use the DVD drive to load the live cd nor the rescue and recovery CD..

I have tried all possible ways on the BIOS to either load the LIVE cd from te DVD drive or the OS from the Harddisk..Nothing seems to work... Any help from the community would be of great help..

Thanks,

---

### Post by kyphi on 2007-11-19
As long as your BIOS boot sequence is set to 'Hard Drive last' your system must boot from either a floppy or a CD.

Go into the BIOS and first of all restore the factory defaults.
Then check your boot sequence so that floppy (if present) is first, CD-ROM is second and third (if you have two) and Hard Drive last.

Then with either an Ubuntu or a Vista disc in the tray, reboot.

If you want to reinstall both systems, you must install Vista first and then Ubuntu.

---

### Post by mohim85 on 2007-11-19
I tried going into the BIOS and changing the setting... But it niether loads the OS from hard disk nor the live cd... not even my recovery cd..thats the worst part... After doing a search on google, i assume that the problem got something to do with the boot loader allocation... i read on other post on google search, something like Both windows and Ubuntu need boot loader to run and each one tries to keep the boot loader, but couldnt find a solution that i can work on..  

and As mentioned earlier i only have access to BIOS... It does seem to read the disc from the drive too... Y is that...Now what do i do.. 

I would be happy to get back my factory settings using my rescue disks...

Thanks

---

### Post by kyphi on 2007-11-19
After changing the boot sequence in the BIOS did you save your changes before exiting?

As I said before, > As long as your BIOS boot sequence is set to 'Hard Drive last' your system must boot from either a floppy or a CD. I stress 'MUST'.

Re > Y is that..I assume that the 'Y' actually means 'why' - if I am correct, could we agree to communicate in English please; it would take the guesswork out of the equation.

---

### Post by Craigus on 2007-11-19
> ...I inserted the Live CD of Ubuntu and did a manual install of ubuntu

So, just to clarify matters, did you actually boot the system from the Live CD ?

---

### Post by TheLeeDynasty on 2007-11-19
O lord, I had this problem. Thank god I had a PS3 with linux on it and able to google a fix.

This is what happened. you ****** the master boot record up. Probably because you decided not to install the boot loader when you installed Ubuntu. Either way, its screwed up. (you might not see it, but the error comes up "Missing Operating System")

Vista uses a totally different boot loader then previous versions. Uses three different files.

What you have to do is what they have already told you. Get it to where your CD Rom/DVD Rom is boot device before your hard disks. (your gonna have to press a key or something when it says booting for CD/DVD in order for it to boot from this device)

I was able to save all my partitions and data by placing my Vista DVD into the drive and booting into the vista install from CD.

When you go into the vista install there will be a link at the bottom left corner to go to the repair section. You "may not find" any windows partitions. That is ok. That are a series of commands that you gotta try from the command prompt in this repair area to fix the MBR. I can not remember the exact combination but here are the commands.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

That should be able to point you in the right direction. I am not a linux guru, I am learning myself and I got very scared that I almost lost all my data on my partitions.

Once I got my MBR fixed, I was able to load into vista finally. I then got a program called EasyBCD which will **safely** modify windows vista bootloader to allow you to dual boot. You will probably want to use "NeoGrub" that comes with this program when you create the linux entry for windows vista bootloader.

I hope this helps.

---


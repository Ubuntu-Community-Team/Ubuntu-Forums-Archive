---
title: "[SOLVED] Ubuntu Server 8.04 on Netfinity 5000 - no cdrom"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by billbrasky66 on 2008-06-04
Hi All,

I'm trying to install Ubuntu Server 8.04 on my IBM Netfinity 5000.  I boot from the CD and after keyboard selection it says it can't find the CDROM.

The machine has SCSI disks (that are found), but the CDROM is IDE (primary master).  I've run Linux on this machine before (Gentoo) without problems.

Looking through the bootlog, I noticed that it wasn't initializing ACPI since the bios < 1999, so I added acpi=force to the kernel parameters, but that didn't help.

In fact, I don't see anything about IDE/ATA at all in the boot log.  Does 8.04 not support some of the older IDE controllers?

I also found the latest firmware on IBM's website and flashed my BIOS, but that didn't help either.

---

### Post by dstew on 2008-06-04
If you know that the CD-ROM is hda, you can try the kernel parameter **hda=cdrom**. Another parameter is **all_generic_ide**. Sometimes there is a BIOS setting that makes the IDE interface hard for the kernel to see. Look for that also.

---

### Post by billbrasky66 on 2008-06-04
Thanks, all_generic_ide sounds like what I need since /dev/hda doesn't even exist.  I'll try it tonight.

---

### Post by billbrasky66 on 2008-06-05
OK, all_generic_ide did not seem to help.  Still no /dev/hda.  Is there any other options I can try?  Is there a way to force the kernel to load the correct IDE chipset driver?

---

### Post by dstew on 2008-06-05
Sometimes the last error in the log is not the one that is really causing the problem. Maybe it is ACPI that is the cuprit. You can use alt-PageUp to page upward through the boot log to see when the first error occurred. If the first error is an ACPI error, then the kernel parameter would be acpi=off. If you disable this system, and if this allows the kernel to boot, then you should be able to install the system.

---

### Post by billbrasky66 on 2008-06-05
Actually, there aren't any errors in the log that I can see.  I noticed that for ubuntu 7 there are threads on all_generic_ide that reference a modprobe failure, but I'm not seeing that.  It just doesn't seem to see any IDE devices at all.

---

### Post by dstew on 2008-06-05
One more thought. The PATA module is called piix, I think. (PATA=IDE). You can try this. Add the kernel parameter **break=top**. That will force a break in the kernel loading after it gets the initrd image loaded. You get a command line. On the command line, enter:```
modprobe piix
exit
```Just a guess...

---

### Post by billbrasky66 on 2008-06-05
Solved!

There's no piix driver, but 

```
modprobe ide_generic 
```

worked!  Not sure why it's not loading that module by default...

Thanks!

---

### Post by ColOneill on 2008-06-10
> **billbrasky66 said:**
> Solved!

There's no piix driver, but 

```
modprobe ide_generic 
```

worked!  Not sure why it's not loading that module by default...

Thanks!

believe it or not, i am in the exact same boat! Netfinity 5000, and cannot get past the cd-rom discovery phase. i see your fix... how exactly do I program it?

---

### Post by billbrasky66 on 2008-06-10
> **ColOneill said:**
> believe it or not, i am in the exact same boat! Netfinity 5000, and cannot get past the cd-rom discovery phase. i see your fix... how exactly do I program it?

After the kernel boots and you get the keyboard type select screen, press ALT-F1 and it will say, "press enter to activate this terminal".  Press enter, then type "modprobe ide_generic" and it should load the driver.  Then type "ls -l /dev/hda" and you should see that the hda device now exists.

Press ALT-F7 (it's one of the F-keys) to get back to the install process and when you get to the CDROM select screen it should now find it properly.

---

### Post by dstew on 2008-06-10
bill, this particular problem occurs on the Live CD before the kernel boots. For ColOneill, see my post #7. To enter a kernel parameter, press F6 at the startup menu. Type the parameter (in this case **break=top**) at the end of the kernel line. The press return, and continue the boot. It will stop with a command line. On that line enter```
modprobe ide_generic
exit
```If you really have the same problem as the original poster, it should go OK.

---

### Post by billbrasky66 on 2008-06-10
> **dstew said:**
> bill, this particular problem occurs on the Live CD before the kernel boots. For ColOneill, see my post #7. To enter a kernel parameter, press F6 at the startup menu. Type the parameter (in this case **break=top**) at the end of the kernel line. The press return, and continue the boot. It will stop with a command line. On that line enter```
modprobe ide_generic
exit
```If you really have the same problem as the original poster, it should go OK.

For some reason, adding the break=top to kernel parameters didn't stop the boot process for me, but doing the modprobe after boot (but before install CD detection) worked.

---

### Post by ColOneill on 2008-06-10
> **billbrasky66 said:**
> After the kernel boots and you get the keyboard type select screen, press ALT-F1 and it will say, "press enter to activate this terminal".  Press enter, then type "modprobe ide_generic" and it should load the driver.  Then type "ls -l /dev/hda" and you should see that the hda device now exists.

Press ALT-F7 (it's one of the F-keys) to get back to the install process and when you get to the CDROM select screen it should now find it properly.

thnx looks like that was enough to point me in the right direction. i hope i do not need to post more netfinity install problems. i still have 2 questions tho. Can this be installed on an AS/400, and what are you going to do with your netfinity? i am still unsure on mine

---

### Post by billbrasky66 on 2008-06-10
> **ColOneill said:**
> thnx looks like that was enough to point me in the right direction. i hope i do not need to post more netfinity install problems. i still have 2 questions tho. Can this be installed on an AS/400, and what are you going to do with your netfinity? i am still unsure on mine

Well, I'm using mine for running a subversion server with trac, and for hosting a SAMBA server for some storage space on my network.  It works great for this purpose.

As for the AS/400, keep in mind that it is not an Intel box, it's a IBM Power [2,3,4,5] box.  You'll probably have to find another distro since the recent releases of ubuntu only appear to support Intel and Sparc chips.  I think that SuSE might have a release for your box.
[http://www.novell.com/products/server/techspecs.html](http://www.novell.com/products/server/techspecs.html)

---

### Post by ColOneill on 2008-06-10
> **billbrasky66 said:**
> Well, I'm using mine for running a subversion server with trac, and for hosting a SAMBA server for some storage space on my network.  It works great for this purpose.

As for the AS/400, keep in mind that it is not an Intel box, it's a IBM Power [2,3,4,5] box.  You'll probably have to find another distro since the recent releases of ubuntu only appear to support Intel and Sparc chips.  I think that SuSE might have a release for your box.
[http://www.novell.com/products/server/techspecs.html](http://www.novell.com/products/server/techspecs.html)

i was gonna use mine as a file server, but all i have is 4.2 gig drives. a printer server would be best, but that is rather dull. i was thinking of using it as a subspace/continuum server... that is not what your subversion is doing is it?

do you have both cpu's installed. i have 2 pent 2 cpu's, but i think they are different types, and i am almost positive they need to be identical.
 thnx for the link. i found the 400 sitting all alone in a surplus wharehouse (alone with the netfinity's and a dell poweredge) i administer a as/400, but as for setting up one from scratch looks like i am going to haf to do some serious research. I already lack a twinax console, but i may be able to bypass that with a modded laptop. gotta get the interface squared away before i can fool with the OS.... even then i do not think my version of the as/400 software will run on this older server, but i will cross that when i get to it

---

### Post by billbrasky66 on 2008-06-10
> **ColOneill said:**
> i was gonna use mine as a file server, but all i have is 4.2 gig drives. a printer server would be best, but that is rather dull. i was thinking of using it as a subspace/continuum server... that is not what your subversion is doing is it?

do you have both cpu's installed. i have 2 pent 2 cpu's, but i think they are different types, and i am almost positive they need to be identical.
 thnx for the link. i found the 400 sitting all alone in a surplus wharehouse (alone with the netfinity's and a dell poweredge) i administer a as/400, but as for setting up one from scratch looks like i am going to haf to do some serious research. I already lack a twinax console, but i may be able to bypass that with a modded laptop. gotta get the interface squared away before i can fool with the OS.... even then i do not think my version of the as/400 software will run on this older server, but i will cross that when i get to it

Yeah, I've actually got the box pretty decked out compliments of some dumpster diving. 2xP3-500s, 2GB RAM, 2x18GB and 3x80GB drives, and a Differential SCSI card with an 8-bay DLT changer.  Unfortunately, yes, the CPUs need to be identical down to the stepping number, but if you can find two old identical desktops you can rip the CPUs out of them; that's what I did, the original processor was a single P2-450.

You should be able to find the 80-pin SCSI drives off eBay for pretty cheap, that's where I got my 80GB drives from.  Then you can RAID-5 them or something.  You should be able to find the drive sleds too if you have blanks in the other bays.

---

### Post by ColOneill on 2008-06-10
> **billbrasky66 said:**
> Yeah, I've actually got the box pretty decked out compliments of some dumpster diving. 2xP3-500s, 2GB RAM, 2x18GB and 3x80GB drives, and a Differential SCSI card with an 8-bay DLT changer.  Unfortunately, yes, the CPUs need to be identical down to the stepping number, but if you can find two old identical desktops you can rip the CPUs out of them; that's what I did, the original processor was a single P2-450.

You should be able to find the 80-pin SCSI drives off eBay for pretty cheap, that's where I got my 80GB drives from.  Then you can RAID-5 them or something.  You should be able to find the drive sleds too if you have blanks in the other bays.

i may be going back to the surplus place tommorow and do some serious digging. on a side note. I am used to ubuntu's GUI, but the ubuntu server loaded nothing. I am stuck at a cmmd prompt ~$ i have been through the help menu and the man root somthing... i am stuck on loading a gui

---

### Post by billbrasky66 on 2008-06-10
> **ColOneill said:**
> i may be going back to the surplus place tommorow and do some serious digging. on a side note. I am used to ubuntu's GUI, but the ubuntu server loaded nothing. I am stuck at a cmmd prompt ~$ i have been through the help menu and the man root somthing... i am stuck on loading a gui

Ubuntu server has no GUI!  The theory is that you shouldn't load down your server with X-Windows.  If you want the GUI you'll need to load Ubuntu desktop on the system.

---

### Post by ColOneill on 2008-06-10
> **billbrasky66 said:**
> Ubuntu server has no GUI!  The theory is that you shouldn't load down your server with X-Windows.  If you want the GUI you'll need to load Ubuntu desktop on the system.

i have no problem running everyting from cmmd line, just gotta start learning cmmds... wait how would i dl updates from the internet without a gui?

---

### Post by billbrasky66 on 2008-06-10
> **ColOneill said:**
> i have no problem running everyting from cmmd line, just gotta start learning cmmds... wait how would i dl updates from the internet without a gui?

You'll have to use apt-get update && apt-get upgrade.
[https://help.ubuntu.com/8.04/serverguide/C/apt-get.html](https://help.ubuntu.com/8.04/serverguide/C/apt-get.html)

---

### Post by Wuu on 2008-12-12
:guitar: Yeh its works for my Netfinity 5000 to :)

---

### Post by Orochium on 2009-02-22
**Sorry, I forgot to mention, my problem is with the newer 8.10 ubuntu installer.  I might move this to a new thread because of it, working with one of the folks on IRC we exhausted the fact that the module ide_generic didn't exist in the module directory.  We weren't able to find a module that would work with the Netfinity there.  Downloading Ubuntu Server 8.04 now**

I am unable to make this solution work so far...

Booting the Netfinity, I let it load from the CDrom, I come to the screen that says "Ubuntu" that has the options 
"Install Ubuntu Server" 
"Check CD for Defect"
"Test Memory"
etc..

I hilighted "Install Ubuntu Server" then hit F6 (other options) and added break=top at the end of the line, like so:

Boot Options files=/cdrom/pressed/ubuntu-server.seed initrd=/install/initrd.gz quiet -- break=top

And pressed enter

the very next thing that happens, is a flashing cursor at the top left corner, for a while, I've tried entering Modprobe ide_generic or modprobe all_generic_ide here, and then exit...which does nothing, its ignoring input at this point, it seems.

It continues on and boots to the gray and blue install screen.

Select USA/everything for keyboard/layout...

It fails to detect the IDE drive, I escape out of that to the installer menu, and hit ALT+F2

And then "Press Enter to activate this console"

from here...typing Modprobe ide_generic I get the error:
FATAL: Module ide_generic not found.

and modprobe all_generic_ide gets the same:
FATAL: Module all_generic_ide not found

Then typing exit gets me stuck in a forever loop of "Please press enter to activate this console"



Anyone know what the heck is going on here, I'm totally confused now.

---


---
title: "Cannot boot"
date: 2013-08-21
forum: Installation &amp; Upgrades
---

### Post by john62 on 2013-08-21
I'm using an old Dell Optiplex gx270 (p4).  I followed the install for ubuntu server, and all (seemingly went well).  When it was time to reboot, I unplugged the USB from which I was making the install, and the computer restarted.  However, the computer will not boot from the HD.  When I go into BIOS it shows Hard drive (not installed).  I'm running BIOS version A06.  When I installed grub, I installed to dev/sdb.  

The harddrive is working properly and is connected, as the install went fine and I heard the HD working.

I have my BIOS set-up to boot from HD...but I still get the message:

SATA Primary drive 0 not found
Primary Drive 0 not found
    Strike the F1 key to continue, F2 to run the setup utility

Any suggestions?

---

### Post by carl4926 on 2013-08-22
> [COLOR=#000000]I installed to dev/sdb. [/COLOR]
sdb would be your USB?

Grub should go to sda
[https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/5.png](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/5.png)

---

### Post by Bucky Ball on 2013-08-22
*Thread moved to **Installation & Upgrades**.*

Welcome to the forums.

Grub *should* go to sda, as mentioned (unless you have setup something exotic) but sounds like you might also have made a persistent install on the USB and not on the hard drive (especially if the hard drive shows no sign of the install). Is this a possibility?

You could boot from the USB, get to a desktop and launch Gparted. Any sign of the Ubuntu / partition? If / and /swap partitions are on the hard drive, we need to change the grub. If they're on the USB, you have made a persistent install to the USB stick. 

Attach a screenshot here if you like. If you boot, with the USB stick in, get into the BIOS and change the boot device to the USB stick, does it boot to a Ubuntu install? If you change the boot device with F12 at boot to the USB does it boot to a Ubuntu install?

---

### Post by john62 on 2013-08-22
> **Bucky Ball said:**
> *Thread moved to **Installation & Upgrades**.*

Welcome to the forums.

Grub *should* go to sda, as mentioned (unless you have setup something exotic) but sounds like you might also have made a persistent install on the USB and not on the hard drive (especially if the hard drive shows no sign of the install). Is this a possibility?

You could boot from the USB, get to a desktop and launch Gparted. Any sign of the Ubuntu / partition? If / and /swap partitions are on the hard drive, we need to change the grub. If they're on the USB, you have made a persistent install to the USB stick. 

Attach a screenshot here if you like. If you boot, with the USB stick in, get into the BIOS and change the boot device to the USB stick, does it boot to a Ubuntu install? If you change the boot device with F12 at boot to the USB does it boot to a Ubuntu install?

Computer boots without issue to USB and I am able to get the install going.  When it comes time to partition during install, I use GUID (full) and all goes well.  The install recognizes the "Install Media" as dev/sda" and shows 4.0GB as total size--this is my USB.  It also shows my Hitachi 80GB HD as dev/sdb @ partition #1 and the swap on dev/sdb partition #5.  The HD is doing work during the install (it sounds normal and I can hear it working fine).

When it comes time to install GRUB I run into issues.  I did a clean install and installed GRUB to dev/sdb, this was without issue and the install completed.  Then I removed USB, told BIOS to boot from HD and I got the errors about SATA Primary not found.  I decided to try the install again, and went through the entire install.  Again, I carefully noted down which dev/ my USB and HD were located at--they were listed as the same as I had mentioned sda=USB with image || sdb=HD.  On the second install, GRUB would not let me install to sdb; giving me a "Fatal Error," saying that "GRUB cannot be installed on the selected medium dev/sdb".  

Not sure what's going on here...

fyi: I'm running a ubuntu_server install....not sure if I can run it live from USB..I don't believe it gives me that option.

---

### Post by carl4926 on 2013-08-23
Can you use CD to install?
This may solve the issue with the USB being seen as sda

---

### Post by john62 on 2013-08-28
I booted from CD. This time the HD showed up as dev/sda.  Install went perfectly.....until it was time to boot.  AGAIN, same issue: on boot I get: SATA primary drive 0 not found.  I tried another new SATA hard drive and still same error. So, I live booted into DOS and updated the bios hoping this would resolve..it didn't.  Anyone have any suggestions? I'm about to toss my computer since nothing I do seems to fix the issue.

---

### Post by carl4926 on 2013-08-28
It seems like it might be a common issue
[http://en.community.dell.com/support-forums/desktop/f/3514/t/19244870.aspx](http://en.community.dell.com/support-forums/desktop/f/3514/t/19244870.aspx)

[http://www.geekstogo.com/forum/topic/288257-sata-primary-drive-0-not-found/](http://www.geekstogo.com/forum/topic/288257-sata-primary-drive-0-not-found/)
This one reported setting the [COLOR=#191A1B][FONT=arial]resetting the drive detection to Auto worked[/FONT][/COLOR]

---

### Post by john62 on 2013-08-28
Drive SATA Primary has been set to AUTO throughout this process...unfortunately is has yielding no resolve to the issue.  I tried resetting CMOS several times..checked all connections..I havn't replaced the battery on the motherboard but I really doubt this is causing all of this.  Any other advice?  It's not a driver issue, is it?  At this basic a level in terms of process of a computer I'm a bit unfamiliar.  But my understanding dictates that BIOS is the most basic of operating systems...binary input output system which is responsible for keeping track of physical hardware..So is this some type of BIOS bug?  Not sure what else to do here.  The computer is old but it's in perfectly good condition, aside from this.  Would make a great U-box server...just wish I could get it to work...any help is appreciatd

---

### Post by carl4926 on 2013-08-28
Booting Ubuntu from a CD doesn't require a HD to even be present and obviously Ubuntu has no problem detecting the HD, but clearly there is some issue at the BIOS level. Quite what, I don't know.

What happened if you did: > [COLOR=#000000]Strike the F1 key to continue[/COLOR]as you quoted earlier?

---

### Post by john62 on 2013-08-28
I get the same error message: Press f1 to retry, press f2 to enter set-up.  Nothing seems to work.  just the recurring message about SATA primary 0 not found.  What else can I do?

---

### Post by carl4926 on 2013-08-28
> **john62 said:**
> I get the same error message: Press f1 to retry, press f2 to enter set-up.  Nothing seems to work.  just the recurring message about SATA primary 0 not found.  What else can I do?

You could try a different distro
But I don't think it's a distro related issue....

---

### Post by Bucky Ball on 2013-08-28
> **carl4926 said:**
> You could try a different distro
But I don't think it's a distro related issue....

It might be interesting to do a comparison though, particularly for devs. Is it possible to burn another flavour and give that a spin to see if you get the same? If you do, it's probably a kernel bug, if not, then it must have something to do with the flavour.

Apologies if you've done so, but have you tried installing from the Alternate disk rather than the straight Desktop? Give it a go. Identical but text based rather than disco and can overcome some issues which prevent install (particularly graphics related). Good luck.

---


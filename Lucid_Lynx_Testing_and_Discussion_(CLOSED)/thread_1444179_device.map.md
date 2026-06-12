---
title: "device.map"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by petteriIII on 2010-03-31
I have always believed that /boot/grub/device.map tries to operate between BIOS and Ubuntu. Earlier, when you made a fresh grub.cfg with command: sudo update-grub2 device.map was displayed and asked if it is right and if not to correct it and redo command. But today device.map was no more printed in my machine (Lucid is in it) and device.map was empty - but machine operates OK.

What is status of device.map ?

---

### Post by seeker5528 on 2010-04-01
> **petteriIII said:**
> What is status of device.map ?

Device.map still exists on my system and indicates it should not be edited because it is automatically generated. I did see some stuff indicating the devs want to get rid of it completely.

Don't know what they expect you to do on the odd times that it gets things wrong and you need to specify a mapping.

The last time I had to mess with the mapping was only to get the order situated between Debian and Ubuntu and since a recent update gave me the option to update the way drives are recognized resulting in the PATA stuff switching from hdX to sdX, I don't expect that will be an issue any more.

Later, Seeker

---

### Post by wkulecz on 2010-04-01
> Don't know what they expect you to do on the odd times that it gets things wrong and you need to specify a mapping.


On 9.10 it got it wrong on my system.  On 10.04Beta1 it still got it wrong, but I noticed, since I was looking for it, and used the "Advanced" button on the step 8 of 8 installer page to make the boot loader be written to the device my BIOS is set to boot from.

I predicet even more dual boot Windows disasters for 10.04 than have been had with 9.10, since most serious users wait for the LTS upgrades instead of installing a new system every six months and thus the universe of 9.10 users is likely smaller than 10.04 will have initially.

For example I skiped 8.10 entirely, only used 9.04 as a test on a box testing Win7RC1, which by the way was also a dual boot disaster forcing a re-install of Win7RC1 (different box from the two mentioned above, with only a single drive).

My wife runs 8.04 (single boot, and so far, has only missed Windows for a few Internet Explorer only "webinars" and the lack of good fonts in Open Office, solved by giving here a user login on my old XP notebook), but I will not update her until the slow dns lookup issues in 10.04Beta1 are solved, at least.

--wally.

---

### Post by seeker5528 on 2010-04-01
> **wkulecz said:**
> On 9.10 it got it wrong on my system.  On 10.04Beta1 it still got it wrong, but I noticed, since I was looking for it, and used the "Advanced" button on the step 8 of 8 installer page to make the boot loader be written to the device my BIOS is set to boot from.

By default the assumption is to install grub to the MBR of your first drive, if you need it to go somewhere else you need to click the advanced button on the last page during the install process and specify where it should be installed.

If you have given boot priority to some HDD other than your first drive and the bios doesn't present that to the OS as your first drive, making it sda, then, IMHO, that isn't grub's fault.

In this first case, if you get grub installed in the right place things should be good after that. That's not to say it shouldn't be considered a bug, but I view that as more of an issue for the installer to recognize and set the installation location correctly as opposed to being a situation where the grub stuff is at fault.

If you are mixing SATA and PATA HDDs, booting from a PATA optical drive for installation but booting from a SATA drive in the installed system or vice-versa the PATA and SATA subsystems may not be recognized in the same order when booting from the CD as when booting into the installed system, again not grubs fault.

If the first SATA drive is sda when booting from the CD, but the first PATA drive is sda in the installed system or vice-versa there are potentially 3 problems, getting grub installed to the correct place, getting booted on the first boot because the device mapping is all different, and making sure things are set correctly in the installed system so that when something is installed that triggers a run of update-grub the correct thing is done. Some of this may be handled already between the use of os-prober and UUIDs.

It's just a guess on my part, but I suspect that efforts to update device management in grub and get rid of grub.cfg are, at least in part, being done to help deal with this second type of situation so that at least if you get grub installed in the right place you shouldn't have to worry about anything else after that. If things play out the way I suspect, then as in the first situation it would still be the job of the installer to correctly set up the grub stuff with the correct location to install grub.

And just so there is no confusion, by installer I don't mean the person doing the installation. :p

Later, Seeker

---

### Post by wkulecz on 2010-04-02
> By default the assumption is to install grub to the MBR of your first drive

That is exactly what is going wrong!  The BIOS defines what is the "first" hard drive in my system.  Not some grub developer!

The installer is not honoring the BIOS setting.  By definition this is incorrect behavior.

Fixing these issues with arcane knowledge (like I have) is fine if Ubuntu is happy to remain a "geek" OS, but the average Windows user who has been hyped in to "trying Linux" probably wouldn't know how to change the BIOS boot order even if the BIOS allows it.

--wally.

---

### Post by seeker5528 on 2010-04-02
> **wkulecz said:**
> That is exactly what is going wrong!  The BIOS defines what is the "first" hard drive in my system.  Not some grub developer!

Grub developers don't define the order, it is just assumed you will be booting from the MBR on the first hard drive and that if you took the trouble to learn how to change that it shouldn't be too much trouble to learn how to tell grub where to install.

The order of the PATA drives will always be in the same order as the connection they are plugged in to. 

The order of the SATA drives will always be in the same order as the connections they are plugged in to.

Changing the boot order does not change this. 

Typically I would expect if you boot from a PATA CD-ROM drive the first PATA drive would be sda, if you boot from a SATA CD-ROM the first SATA drive to be SDA, but I don't know if this is defined behavior that happens by design or just the way it usually works. 

> The installer is not honoring the BIOS setting.  By definition this is incorrect behavior.

I don't know what kind of mechanisms there are for probing the BIOS to find out what the boot order is, and thinking about it more, I'm not convinced the BIOS boot order should really be a consideration.

> but the average Windows user who has been hyped in to "trying Linux" probably wouldn't know how to change the BIOS boot order even if the BIOS allows it.

If you can't change the boot order it's not really so much of a problem, it's less likely for unexpected things to happen. 

With the newer stuff it seems to increasingly be a problem that because you select the hard drive boot priority by the way the drive is identified instead of where it is connected the BIOS people seem to now want to do this clever thing where if the first drive in the boot order is not detected it will automatically move all your other hard drives up in the boot order. So if you just had an intermittent glitch or had the drive disconnected for some reason, it will be last in the boot order when it is recognized again. If the hard drive stopped being detected and had to be replaced, then the new drive would be last in the boot order.

Assuming all the GRUB issues are fixed, the installer modified to set things so grub-install will install grub in the MBR of the first boot drive as set in the BIOS, and something caused the boot order to change, then you install/re-install Ubuntu, causing GRUB to be written to the MBR on the wrong HDD.

So maybe the stuff shouldn't be changed, because the more technically inclined can poke around and figure what is going on.

The not so technically inclined won't even know where to begin if the installed system can't do the first boot as a result or fails later when they remove this other drive that automatically got shifted to be first in the HDD boot order without them knowing.

Later, Seeker

---


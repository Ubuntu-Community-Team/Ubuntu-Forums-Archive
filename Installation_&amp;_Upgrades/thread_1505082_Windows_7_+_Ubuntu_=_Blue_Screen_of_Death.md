---
title: "Windows 7 + Ubuntu = Blue Screen of Death"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by ActiveLad on 2010-06-08
I first tried a foray into the world of Ubuntu with v9.X and tried to install dual boot with Windows 7 but experienced such Windows boot instability afterwards that I gave up, thinking perhaps that Win 7 was a bit too new for v9.X (it concerned me at the time that the Grub version with the ISO was a Beta). I have therefore now tried again with v10.04

Hardware Environment
Compaq Presario CQ60 (AMD Turion Dual Core RM-72 2.1Ghz, 4Gb Memory, 250Gb HD)

Software Environment
Windows 7 Home Premium 64-Bit Version

Although Win 7 was initially configured to use the entire 250Gb available, and having read about issues with using the Ubuntu installer to resize partitions, I used the Windows Management Console to reduce the partition size and leave 100Gb of Free Space for Ubuntu (the Windows Partition being reduced to 150Gb but still having 120Gb Free). I ran Chkdsk several times to check Win 7 was happy and rebotted each time to check there were no issues. All good so far.

I then booted from the Ubuntu 10.04 CD (having downloaded the 32-Bit ISO (following recommendations not to use the 64-Bit version for regular use) and burned to CD) and ran Ubuntu in "CD-only" mode to check there were no issues. Although slow (obviously), Ubuntu was happy, all the hardware appeared to be functioning correctly and I could connect to the Internet via Wireless fine. As a final check I then shut down Ubuntu, rebooted to Win 7 and Win 7 booted without a problem.

I rebooted from the Ubuntu CD again and ran a straightforward install, allowing Ubuntu to install itself in the available free space (100Gb) and accepting all the defaults. After completion, I rebooted and got the Grub Menu. I chose the default (Ubuntu) and Ubuntu started fine. I then shutdown and rebooted, this time selecting Win 7. After some hesitation, Win 7 started, got as far as "Welcome" and then blue screened with a Fatal System Error. I tried numerous times to restart Win 7 in normal model, safe mode and last known good menu and all Blue Screened.

I then ran the Win 7 Rescue Disk which identified that Win 7 had not started properly but could not suggest a fix. Having experienced with previously with Ubuntu 9.X, I dropped to a command prompt and used Bootrec to rebuld the MBR. I obviously lost Grub, but Win 7 now boots perfectly again.

So my question is why is Ubuntu apparently still unable to install itself properly in a dual boot situation without trashing Win 7? I actually quite like Ubuntu and would like to give it an extended try, but since Win 7 is currently my default OS I can't afford to lose access to it, nor do I have the luxury of an alternative PC to install it on standalone. As far as I can see, it's well known that Windows is "sensitive" to having its MBR messed with, so would have thought the Ubuntu community would have fixed this issue by now? I don't want to knock you guys, but if the install falls at the first hurdle, you'll understand when it doesn't build confidence.

Pete

---

### Post by darkod on 2010-06-08
I can only speculate, but unfortunately it's not only the linux community involved here. Microsoft and how Compaq set up the machine also plays a role.

Personally, I am dual booting Win7 Ult 64bit and Lucid 64bit without any issues but I always build my own PC and install my OSs. No Dell/HP/Compaq software running in the background that they don't even tell you about.

On my netbook I am also dual booting Win7 Ult 32bit and Lucid 32bit without any issues.

The same was true when dual booting with Karmic 64bit and 32bit respectively.

I can only assume it is something to do with your particular win7 setup since you had issues with both Karmic and Lucid.

---

### Post by ActiveLad on 2010-06-09
It's not an HP/Compaq flavour of Win7 that I'm running as the machine originally came with Vista. When Win 7 was released, I installed a generic Win 7 that I bought separately having removed the restore partition and starting from scratch i.e. a clean install. I've not added any HP/Compaq specific software on top, so I can be pretty sure that it's clean.

Does installing Ubuntu "inside" Windows do anything different that might help as I've previously installed direct from CD rather than using the Windows installer?

---

### Post by wilee-nilee on 2010-06-09
> **ActiveLad said:**
> It's not an HP/Compaq flavour of Win7 that I'm running as the machine originally came with Vista. When Win 7 was released, I installed a generic Win 7 that I bought separately having removed the restore partition and starting from scratch i.e. a clean install. I've not added any HP/Compaq specific software on top, so I can be pretty sure that it's clean.

Does installing Ubuntu "inside" Windows do anything different that might help as I've previously installed direct from CD rather than using the Windows installer?

If you had done a chkdsk /r instead of reinstalling the bootloader it might have fixed it. I think this is a anomaly, did you reboot windows after resizing to make sure it was working? I have run XP/W7/Lucid altogether and never had a problem.

---

### Post by ActiveLad on 2010-06-09
Yes I did run Chkdsk after the resize to make sure the disk was OK and again after I had installed Ubuntu to see if that would fix the problem (Sorry, missed that bit out).

---

### Post by wilee-nilee on 2010-06-09
> **ActiveLad said:**
> Yes I did run Chkdsk after the resize to make sure the disk was OK and again after I had installed Ubuntu to see if that would fix the problem (Sorry, missed that bit out).

Strange Ubuntu is on a different partition grub took you to the welcome screen. If you do a wubi install, which I wouldn't suggest you lose some speed and any sudden shutdown can bork Ubuntu possibly. It is a pseudo virtual with everything in a file system inside a ntfs partition.

You may have gotten a grub install in windows, but this usually just gets a blinking cursor or a loop back to grub. If this was the case the rebuild of the bcd would have you booting in okay, so it is a strange event. 

darkod really would know more about all of this though. I notice that when I look at my HD partitions that there is a 1mb space between W7 and Lucid, I don't know if this has to do with the partitions being sized to the exact 512 block.

If Ubuntu is still on the HD you could try to reload grub2 again.
[grub2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by ActiveLad on 2010-06-09
> **wilee-nilee said:**
> Strange Ubuntu is on a different partition grub took you to the welcome screen. 
I might not have been clear there. When the PC booted, I got the Grub Loader. I chose the Win 7 option (bottom of the list) and Win 7 started. Got the "Starting Windows" screen and then got as far as the Win 7 Welcome screen when the BSoD appeared with a Fatal System Error.

Just as a thought, could there be any issue with having Win 7 64-bit and Ubuntu 32-Bit? Since they're booting independently, I can't see there's an issue, but just wonder if Grub is operating in a 32-Bit environment and then hands over to Win 7 in 64-bit mode that might cause an issue?

---

### Post by wilee-nilee on 2010-06-09
> **ActiveLad said:**
> I might not have been clear there. When the PC booted, I got the Grub Loader. I chose the Win 7 option (bottom of the list) and Win 7 started. Got the "Starting Windows" screen and then got as far as the Win 7 Welcome screen when the BSoD appeared with a Fatal System Error.

Just as a thought, could there be any issue with having Win 7 64-bit and Ubuntu 32-Bit? Since they're booting independently, I can't see there's an issue, but just wonder if Grub is operating in a 32-Bit environment and then hands over to Win 7 in 64-bit mode that might cause an issue?

I don't know about the 32-64 bit handover. I would look on the web about that I guess if you get no answers. I didn't find any problems in general in Ubuntu about your computer in general having any more then graphic driver issues that were fixable, and a few other basic tweaks.

---

### Post by Mark Phelps on 2010-06-09
In my experience, it typically takes all three passes of the repair activities to get full functionality back.

From what you said, you only repaired the MBR, not the Win7 boot loader.  Unless you've already done that, I would suggest you boot again from the Win7 Repair CD and repair the boot loader.

---


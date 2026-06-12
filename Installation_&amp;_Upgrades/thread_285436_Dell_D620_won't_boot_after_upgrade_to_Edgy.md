---
title: "Dell D620 won't boot after upgrade to Edgy"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by dro0g on 2006-10-26
Hey all,

After seeing the announcement on /. this afternoon, I figured I'd give upgrading from 6.06 to 6.10 on my D620 laptop a shot. I opted for doing the graphical upgrade (gksu "update-manager -c" ) and kicked it off and left it alone for a couple hours. When I came back it was at a "Can't start X" screen. I could get to other VTYs though, so I rebooted thinking that might be a good first step (bad mistake :) )

Now when I try to boot and select a normal kernel at the grub menu, I get as far as "Mounting root file system" on the splash screen and "Uncompressing Linux... OK, booting the kernel." on the console. 

If I select a recovery kernel (booting with the kernel option single) it gets as far as loading some USB devices and hangs. I've tried both disabling everything I could in the BIOS and passing the 'nousb' kernel option at boot, but it still hangs after loading a USB device. 

Any suggestions? I'm torrenting the ISO right now in the hopes that it can do something for me. I've booted to a knoppix CD, so at least I can copy my home dir off if it comes to that.

---

### Post by dro0g on 2006-10-27
Got it solved! First I downloaded the regular desktop ISO. While that would boot, I didn't really see any way to recover the borked upgrade from there (I didn't want to do a new Install because I figured that would nuke my current install)

I then downloaded the alternate CD. I booted to recovery mode and selected the partition that mounts to / . At the shell, I ran dpkg configure -a (I think!) which then started reinstalling the downloaded upgrade packages, but with tons of errors. 

Once that finished I shutdown and tested rebooting off the HDD again. It booted, but came up with drive errors and I had to fsck the drive. Once that was finished, rebooted again and it booted to a shell prompt! I ran an apt-get install (I at this point had no network and no X) and it installed a bunch more of the upgrade packages. 

Once that was finished, I rebooted again and it booted into X. I was able to login, though I got a few errors from various packages. I ran another cycle of apt-get update, upgrade, dist-upgrade, install, and rebooted one last time. This time it came up without errors, aside from tilda crashing.

---


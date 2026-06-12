---
title: "Ubuntu will not boot"
date: 2006-05-31
forum: Installation &amp; Upgrades
---

### Post by icefaerie on 2006-05-31
After reading about the automatic LAMP installation in 6.06, I decided to switch from Gentoo to Ubuntu on my server.

I put the 6.06 RC CD I burned in and followed the installation procedures for a LAMP server.  There were no problems during the installation.

However, I went I go to actually boot, the following happens.  The computer turns on, and GRUB is able to load just fine, but whichever of the 2 kernels I try to boot (either the regular server one or the recovery mode one), the same thing happens.  It detects the ext2 filesystem properly.  Then I see initrd [kernel location], followed by Linux [something, too fast to read it], saveddefault, and boot.

Then the computer reboots itself. It's been sitting there looping in this manner for several minutes.

In the past, the computer has had some power supply issues, so I decided to change the power supply, but replacing the power supply with a correctly functioning one makes no difference in the aforementioned behavior.

I really have no idea what to do, since there were no apparent problems during installation.  Any help would be greatly appreciated.  Thanks.

---

### Post by confused57 on 2006-05-31
I think there may be a problem with the kernel on the Dapper 6.06-rc-server install CD.  I downloaded the iso, MD5 checksum OK, CD verified OK at install; but after installing the basic server, I had the same problem...the server kernel showed in grub, but when it went to boot into Linux it just rebooted the computer instead.  First, I tried to dual-boot with Xubuntu, thinking grub may have installed on the server install; then I just did a clean install of the server as the only OS on my hd...same problem.

   Ended up just downloading the Dapper 6.06-rc-alternate CD and doing a server install, worked perfectly.
   I think there may be a problem with the server iso...?

---

### Post by kraz on 2006-06-01
Same problem here.


Downloading the alternate to get my system running now.

---

### Post by Tasu on 2006-06-13
Check for which kernel is installed, the alternate (normal behaviour), not finding a 686 compatible processor (epia's aren't, they lack some features that make it unbootable with a stock kernel from ubuntu, must be recompiled without those 686 specific extensions, namely cmov extension, default on 686 kernel, but unsupported by epia's processors), installs a 386 and with that there ain't no problem.

Via people say it's a major issue of ubuntu since the specification for kernel tells that if the processor isn't capable of cmov, the kernel must understand it and not activate cmov... don't know if this spec is right...

---

### Post by wallyhall on 2007-03-29
Yeah, I've got precisely the same problem on an older AMD-K6 I'm using as a fileserver.  For the reference of anyone else who trips across this problem, the most elegant solution I could come up with (without using the alternative CD)

 - Install the system using the server CD
 - "Rescue" the system using the server CD
 - Ensure you enter a proper chroot'ed environment, i.e. select "run a shell from the rescued system" when prompted
 - Run "apt-get remove linux-server" - check [this link]("http://packages.ubuntu.com/dapper/base/linux-server") to see what it removes, as of writing it simply gets rid of the server kernel.
 - Run "apt-get install linux-386" - this will effectively replace the specific server kernel with the more vanilla 386 kernel (and let Ubuntu keep you upto date with patches, which is important!)
 - Check grub's been updated properly and reboot
 - Boot off the HD to (hopefully) see your new server install.

It's a bit of a shame the LTS Ubuntu server disk doesn't have an option to "install legacy kernel".  It'd make the few (and I do mean the very few) of us who have this problem's lives that much easier!

For the interest of anyone who's wondering what it is that makes the server kernel not boot, I have absolutely no idea, but there might be a clue in the differences between the config files of the two kernels (which if you follow my instructions above, running "diff /boot/config-2.6.15-28-386 /boot/config-2.6.15-28-server" should tell you).

Cheers, hope it helps (email me if not)

   wally

---

### Post by Eternal-student on 2007-04-06
This is still a problem with server version 6.10

but Wallyhall's fantastic work around worked brilliantly for me.  Many thanks for posting it.

---

### Post by wallyhall on 2007-04-06
> **Eternal-student said:**
> This is still a problem with server version 6.10

but Wallyhall's fantastic work around worked brilliantly for me.  Many thanks for posting it.

No problem, glad it helped :)

wally

---

### Post by joshp on 2007-05-24
I had this problem with 6.06 LTS on a Pentium 266 mmx, the work around posted above worked perfectly.

I feel a note should be added to the Ubuntu Server Guide's Minimum requirements page.  The page states that the server works with x86 with > 64mb ram.  It's not obvious that the server kernel is an i686 kernel.  It would save the few of us that are trying to install ubuntu server on non-i686 compatible processors a whole lot of frustration.
Thanks,
-Josh

---


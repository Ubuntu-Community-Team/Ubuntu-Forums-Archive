---
title: "Video unusable w/ desktop and alternate CDs"
date: 2006-12-13
forum: Installation &amp; Upgrades
---

### Post by secdroid on 2006-12-13
[Copied, modified, and updated from kubuntuforums.net]

I have a test computer that is unable to get a stable graphical login screen from  Kubuntu Edgy X86 (desktop or alternate install CDs) or from Ubuntu Edgy desktop.  

The same hardware will boot and run the Ubuntu Dapper desktop CD, albeit in frame buffer 80x25 mode.  If I then update the Dapper X config, Ubuntu runs a fully featured 1024x768 desktop.  Edgy (live or installed) flashes the login screen on,off,on,off...

I've even specified the config via the F4 VGA options as 640x480 16 bit at Ubuntu Edgy live CD boot.  Same result.

Hardware, as reported by Knoppix 5.0 Kinfo: VGA compatible controller, Diamond... Monster Fusion AGP, 3Dfx Voodoo Banshee..., X.Org 11.0, (automatically set) 1024x768, 75x75, Depths(7) 16,...

Workarounds for (K)Ubuntu?

FWIW, (K)Ubuntu seems to be much less able to do video hardware detection than other Linuxes.  In particular, it is the only Linux that cares that I have a Belkin KVM switch and that this box is the second computer booted on the switch.  Knoppix, DSL, Fedora, etc. do automatic configuration without difficulty.

---

### Post by wpshooter on 2006-12-13
Have you tried wiping the hard drive completely clean with KILLDISK on this computer and then try to install from the ALTERNATE CD ?

---

### Post by secdroid on 2006-12-14
> **wpshooter said:**
> Have you tried wiping the hard drive completely clean with KILLDISK on this computer and then try to install from the ALTERNATE CD ?

Did not wipe disk before doing Kubuntu install, but did reformat with EXT3 as part of alternate CD install process.

Besides, I don't follow how both Kubuntu Edgy (live) desktop and Ubuntu Edgy (live) desktop would fail while Ubuntu Dapper (live) desktop would succeed.  In addition, Knoppix 5.01 and DSL 3.1 live CDs boot beautifully.  

This would seem to indicate a defect in Edgy hardware detection and/or X configuration.  The inability to run a (K)Ubuntu Live CD is a significant defect, IMHO, when numerous other Linuxes have no problem with this hardware and Dapper runs fine on the same hardware.

Is there any way to work around this short of doing a Server install and manual X installation and configuration?  (As I said, boot time F4 VGA config doesn't seem to solve this.)

---

### Post by taurus on 2006-12-14
Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```

---

### Post by secdroid on 2006-12-14
> **taurus said:**
> Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```

OK, did it.  Allowed autodection of chipset and it came up with "tdfx," which appears to be correct.  It showed ID as "3Dfx... Voodoo Banshee," which is correct.  Accepted BusID, left memory blank, left Framebuffer as default-no, specified Generic 1024x768 "Simple" 17" monitor, color depth 16.  Did a startx and only top half of screen drawn.  Did a reboot and got the login screen flash on,off,on,off...

Repeated process, selecting framebuffer.  Same result.

This suggested that there is a driver issue, rather than a detection issue.  So, I googled and came up with 
[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/68291](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/68291)

Appears that this is a known driver issue.  Thanks for helping me sort this out, taurus.

---

### Post by taurus on 2006-12-14
Or maybe use

```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by secdroid on 2006-12-14
> **taurus said:**
> Or maybe use

```
dpkg-reconfigure -phigh xserver-xorg
```

No joy.  Same as before.

However, I did download the patched driver recommended in the googled discussions cited previously.  Applied the driver patch and rebooted.  The driver fixed the problem for the installed version.  Patching live CDs is beyond me.

Thanks again for the pointers, taurus.

---

### Post by kingcharles1666 on 2006-12-25
Hi,

Noob question here:
how do I apply this patch? I tried the .deb file that was [_posted_]("https://launchpad.net/distros/ubuntu/+source/xorg/+bug/68291") but I have an AMD64 system and the i386 does not work.
I downloaded the script _[here]("https://bugs.freedesktop.org/show_bug.cgi?id=7149")_ but it gives errors:

```
mico@home:~$ sudo ./tdfxpatch.cgi
./tdfxpatch.cgi: line 1: ---: command not found
./tdfxpatch.cgi: line 2: +++: command not found
./tdfxpatch.cgi: line 3: @@: command not found
./tdfxpatch.cgi: line 4: /bin: is a directory
./tdfxpatch.cgi: line 5: syntax error near unexpected token `('
./tdfxpatch.cgi: line 5: `   oldValue=TDFXReadLongMMIO(pTDFX, MISCINIT0);'
```

then nothing.

What am I doing wrong???

thanks Charles

---


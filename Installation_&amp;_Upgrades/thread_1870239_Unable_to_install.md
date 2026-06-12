---
title: "Unable to install"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by daveh56 on 2011-10-26
Hello

 I have in the past installed Ubuntu with no problems. Now if I try to install Ubuntu 11.04 (32bit) or 11.10(64 bit) A splash screen comes up for a few seconds then I get  a lot of messages saying: timeout killing '/sbin/modprobe -bv pci:v0001002d0000xxxxxx blah blah blah.

Pretty much stock HP Pavillion a1210n with Adaptec 29160N scsi card.

Any ideas what to do now?? A Google search came up w/similar issue but with no resolution that's helpful for a new installation.

Thanks,

Dave

---

### Post by b00n on 2012-02-11
> **daveh56 said:**
> Hello

 I have in the past installed Ubuntu with no problems. Now if I try to install Ubuntu 11.04 (32bit) or 11.10(64 bit) A splash screen comes up for a few seconds then I get  a lot of messages saying: timeout killing '/sbin/modprobe -bv pci:v0001002d0000xxxxxx blah blah blah.

Dave

Same problem here.  I can install from a 64-bit 10.04 CD, but update to 10.10 fails with the somewhat mysterious

```
E: linux-image-2.6.32-38-generic: subprocess installed post-installation script returned error exit status 2
```What I really wanted to do was a clean install of 11.10 (64-bit).  That fails with the "killing /sbin/modprobe" failure.

There's various related threads

[http://ubuntuforums.org/showthread.php?t=1880625]("http://http://ubuntuforums.org/showthread.php?t=1880625") Getting rid of EVGA GTX 550 Ti video card and using an old one worked.  Somebody said try hit F6 at first menu and select "select nomodeset".  Somebody says UEFI ("new BIOS") sometimes gives problems with grub2.  More on nomodeset [http://wiki.sugarlabs.org/go/Nomodeset]("http://http://wiki.sugarlabs.org/go/Nomodeset")

I have a new motherboard and EVGA GTX 550 Ti cards and (surprise!) am here because I was having the same problems.  I did as suggested in that thread to select "nomodeset" and am now installing 11.10, dunno if there are further problems.  Bascially, when first booting the screen shows a purple background with a little icon at the bottom, I hit F6 which took me to a menu, then arrow down to "install", then F6 to bring up another menu, then arrow down to "nomodeset", ESC, to return to "install", then enter/return to proceed.

Another thread is [http://http://ubuntuforums.org/showthread.php?t=1912454]("http://http//ubuntuforums.org/showthread.php?t=1912454") which "fixed" it by switching to a different video card.

Another thread is [http://http://ubuntuforums.org/showthread.php?t=1898373]("http://http//ubuntuforums.org/showthread.php?t=1898373") which several people report the same problem.  Using "--acpi=off" is a workaround for at least one person, but is also a heavy hammer in that you lose functionaity.  Somebody said using a newer BIOS worked for them.  Somebody said nomodeset worked for them.  Somebody said disabling the nvidia-nouveau module and using the built-in graphics worked for them.

---


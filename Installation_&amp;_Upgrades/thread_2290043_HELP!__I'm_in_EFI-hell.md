---
title: "HELP!  I'm in EFI-hell"
date: 2015-08-08
forum: Installation &amp; Upgrades
---

### Post by stevecoh1 on 2015-08-08
I bought this Lenovo Thinkpad 540-T (64-bit) a little over a year ago.  Had I known all the obstacles EFI was going to throw in my face, I never would have.  I didn't want Windows, I wanted Ubuntu and installed 14.04.  Somehow back then, I made a mistake, I don't evwanten remember what it was, and wiped out the Windows boot.  I didn't mind that too much, I hated Windows 8.1 and never wanted to use it.  I could still boot Ubuntu and things were ok.  They stayed okay until kernel 3.13.0-48 came out.  With this kernel, my USB and WiFi were broken.  I then made the mistake of installing grub (v1) and this at least allowed me to boot up the previous kernel 3.13.0-46 which worked fine.

I wanted to get beyond this state today, and a helpful fellow on X-Chat Ubuntu told me to reinstall grub2-EFI, which I did.  Probably I should have told him about my screwed up EFI configuration, but I didn't.  The result now is that whenever I reboot from the hard drive EFI comes up with a nasty "Secure Boot" message telling me that my disk image is unrecognized.  I was able to boot from a CDROM, which is how I'm here now, but I don't have access to my hard drive.  I've also made a bootable startup stick from that CD using "Startup Disk Creator", but I want access to my hard drive.  Will there be a way to configure this USB stick as a boot device that will allow me access to my system as it was.  Or am I going to have to pull all my data off and get the hard drive reloaded with Windows and start all over?

---

### Post by stevecoh1 on 2015-08-08
Never mind! Just turned off Secure Boot in the BIOS and everything is fine!

---


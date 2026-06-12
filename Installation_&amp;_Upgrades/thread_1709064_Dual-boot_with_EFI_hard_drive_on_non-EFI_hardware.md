---
title: "Dual-boot with EFI hard drive on non-EFI hardware"
date: 2011-03-17
forum: Installation &amp; Upgrades
---

### Post by jayands on 2011-03-17
I myself am tri-booting on my MBP beautifully (albeit a LITTLE awkward with two boot menus: rEFIt and GRUB/BURG, but that's another story), but my good friend has a Dell Inspiron 1760 that he got rid of Win7 completely on about 6 months ago. Well, he wanted to put it Back on for the sole purpose of gaming. Only his DVD drive's been burnt out.

I performed the required surgery, installing his hard drive into my MBP. After much wrestling, I did two clean installs: Windows ran beautifully, I installed BURG, the whole nine yards. Well, when the hard drive was replaced in the Dell, Ubuntu runs fine (I'm using it right now, in fact), however Windows does not: it gets about a quarter of the way through the Windows 7 animation and auto-restarts. Every time.

My question is this: is there a way to tell Windows, "Hey! You're no longer on EFI hardware! Now get to work."? Or do I have to find a way to do yet ANOTHER Windows 7 install?

---

### Post by srs5694 on 2011-03-17
Windows never thought it was on an EFI-based machine. When you install Windows on a Mac, the Mac uses a BIOS emulation mode that's built into its EFI to make Windows happy. Thus, it's not the change from EFI to BIOS per se that's causing problems.

Overall, getting the current Windows installation working on that Dell is likely to be very difficult, since Windows does *not* like to see its hardware changed once it's installed. Chances are it's hanging because of those hardware changes. I won't say it's impossible to get it working, but personally, I wouldn't bother; I'd put in a new DVD drive and re-install Windows that way. If this isn't possible, then I recommend you take your question to a Windows forum, since this is a Windows boot issue; you're more likely to get good advice where the Windows gurus hang out than you are here.

That said, it's possible the hard disk now has a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) which is an ugly hack that Apple uses to get Windows and OS X to coexist. I recommend you ascertain whether or not this is the case and, if it is, convert the disk to use a plain MBR configuration, at least if that conversion is possible without losing important data. (GPT-to-MBR conversions aren't always possible, depending on the number of partitions and details of their placement.) You can convert from a GPT or hybrid MBR setup to a pure MBR setup with my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) utility.

---

### Post by jayands on 2011-03-17
Thanks; I'm taking your advice. I also checked out the resources listed, and the gdisk reports a status of "MBR only". If the windows people can't come up with anything, I'll try  burg-ing a win 7 iso, and then we'll see about getting the new cd drive (only $42.99 on amazon, so it's not too much trouble).

---

### Post by srs5694 on 2011-03-18
If gdisk says "MBR only," then you don't need to worry about GPT or hybrid MBRs; just treat it like a normal PC disk.

---


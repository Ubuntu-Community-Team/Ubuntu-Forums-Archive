---
title: "Installing 7.10 into an existing Fedora/XP multiboot system"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by epo001 on 2007-10-21
First post, be kind. I have RTFM'd and some things were left a bit vague, if I have missed anything please point me at it.

I have an existing XP/Fedora system and would like to add Ubuntu as a 3rd system. I have a /tmp  and swap partition it can use and there is a GRUB-based /boot for it to place boot files in. I intend to give Ubuntu a single (primary) partition for all other filesystems

I believe I can nominate spare partitions for Ubuntu to use after reformatting (for /) as well existing partitions for it to use without reformatting (/boot, /tmp).

I believe the Ubuntu installer will recognise my existing /boot/grub.menu.lst and add its own selections to that. OR do I need to back up my /boot and reinstate after installation?.

Fedora is intelligent about updating menu.lst across package upgrades and removals, i.e. it only affects relevant entries leaving all others as was. I take it Ubuntu is the same?

Are Fedora (RHEL) menu.lst files compatible with Ubuntu and vice versa?

---

### Post by rsambuca on 2007-10-21
Yeah, basically grub is grub, whether you want to let the fedora or ubuntu one control everything.  I have a number of distros installed, and I prefer to chainload the grub loaders so that I do not have to manually edit the menu.lst with every kernel change.  If you want to keep everything as is, when you install Ubuntu make sure you direct the installer to put grub onto the ubuntu partition, as opposed to the mbr or the /boot partition you have set up.  Then you can chainload to the ubuntu menu from your existing fedora grub.  The benefit of this is that if Ubuntu updates is kernel, you don't have to worry about updating grub, since it will all be done automatically.  To your existing fedora menu.lst, you would just add a chainloader to the end:

title  Ubuntu
root (hd0,3)
chainloader +1

You will have to replace (hd0,3) with the correct Ubuntu partition in your case.

Also, due to the specific way in which Ubuntu handles its temp files, you are definitely better off NOT using a separate partition for this.

---

### Post by epo001 on 2007-10-21
> **rsambuca said:**
> Also, due to the specific way in which Ubuntu handles its temp files, you are definitely better off NOT using a separate partition for this.
Thank you very much, this sounds like /tmp is cleared before/after booting? Is there anything I could read which might bridge the cultural gulf from someone more used to other distributions?

---

### Post by rsambuca on 2007-10-21
> **epo001 said:**
> Thank you very much, this sounds like /tmp is cleared before/after booting? Is there anything I could read which might bridge the cultural gulf from someone more used to other distributions?

To be honest, I can't remember the exact details of why, just that when I read it initially it was quite clear as to the reasons.

I am not sure of any place to read the differences, but honestly, I think most distros are basically the same other than the package management system, and that Ubuntu disables the root account and uses sudo.  I have five different distros running, and at the end of the day, they all can be configured to do the same thing!  Some, like Ubuntu, are just easier out-of-the-box, but as a result are not as highly configured for your specific system.  I still use Ubuntu as my main distro, though.

---


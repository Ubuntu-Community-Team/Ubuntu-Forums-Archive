---
title: "Dual boot Vista and Ubuntustudio with Vista installed first"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by jsmanness on 2007-06-21
Has anyone attempted to dual-boot Vista and a Ubuntu 7.04 alternate such as Ubuntustudio with Vista installed first? Since Ubuntustudio doesn't have a Live CD, I'm not sure how well the text-based installation works with Vista.

I found this link for dual-booting Vista and Ubuntu 7.04 with Vista installed first but they just talk about the Live CD method:

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

Thanks,

Jon

---

### Post by cwgpress on 2007-06-21
I just did this with Edgy. Try this procedure:
[LIST=1]
[*]In Vista use Disk Manager to create empty space on the disk. You'll need to reduce the size of the Vista partition if you're on a new pc with Vista pre-installed.
[*]Boot from your Ubuntu install CD. You may have to go into bios setup in order to put the CD in front of the hard drive for booting. I did, on my Dell E521.
[*]Do a normal installation, being sure that you select the free space as the location of the new system. You can use all of it, or manually partition it during the install.
[*]Make sure that Grub recognizes your Vista loader before you allow it to rewrite the MBR.
[*]With luck everything will work after this. If not, just take things one at a time. Ubuntu seems remarkably resilient. My failed installations have just about always started working after a while, and sometimes I even knew how I fixed them.
[/LIST]
Good luck!

---


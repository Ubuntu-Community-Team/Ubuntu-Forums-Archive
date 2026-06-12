---
title: "LiveDVD install does not see Windows 8"
date: 2013-06-23
forum: Installation &amp; Upgrades
---

### Post by kenandeva on 2013-06-23
Hi.  I have a DELL XPS 8500.  It has Windows 8 installed.  When I try to install Ubuntu 12.04.2 with a LiveDVD (I burned it from an iso file I got at the Ubuntu download site), after editing the Grub command to include nomodeset, the install GUI starts up.  However, after I click through to the step that is supposed to ask me if I want to install Ubuntu along side Windows 8, I do not get Windows 8 dual boot as an option.  I only have the option to install Ubuntu by itself because the install program says it does not see any other operating system already installed.  

I saw some posts about UEFI being an issue--and it seems my Windows 8 is installed under UEFI.  I saw [a link about this]("http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system") saying that I needed to turn off secure boot--but some comments under that link say that should not be necessary.  I'd be willing to install a newer version of Ubuntu if necessary, but I would prefer to use the LTS version if possible--unless a more recent version fixes this problem.

So I guess I just want to know why the LiveDVD install program does not see Windows 8 and what I could/should do about this.

Thanks,

Ken

---

### Post by Mark Phelps on 2013-06-24
Sorry, don't deal with UEFI -- but BEFORE you charge into this, do yourself a favor and use the Win8 option to make a Recovery Drive (it's actually a disk, not a drive).  That will give you something you can use to make boot loader repairs later, should you need it.

---

### Post by oldfred on 2013-06-24
Generally it is better with secure boot off, and you must turn off fast boot. Some cannot get back into UEFI/BIOS if fast boot it on and Windows does not boot.

Ubuntu does have the secure boot files and will install with that. Some systems only boot Windows with secure boot on. Does yours boot Windows with secure boot off?

Another user with Dell 8500
 Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)

---


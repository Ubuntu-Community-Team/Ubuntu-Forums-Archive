---
title: "Installing Xubuntu - Where to install boot loader?"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by floydlove on 2007-11-09
Okay, trying to install Xubuntu on a separate hard drive as I have Windows XP on the other hard drive.

Windows XP is my master (hda) and Xubuntu my slave (hdb). 

I manually partitioned my hard drive and everything was fine until the last step. Under 'Advance' there's an option to install a boot loader. It was going to install to 'hd0'.

I wasn't confident and changed this to 'hdb' as I wanted it to install to Xubuntu. Seems this was wrong as it had a fatal error at about 97% installation.

Just want confirmation of when I install again, that 'hd0' will be okay to install the boot loader to or what do I change it to? And will this make sure I can boot both Windows XP and Xubuntu?

BIOS is set to boot my CD-Rom drive than my Floppy than my C-Drive (Windows XP).

Thanks.

---

### Post by floydlove on 2007-11-10
Nevermind. I just installed GRUB to the MBR (hd0).

Currently running Xubuntu, with Windows XP and Xubuntu dual booting fine.

---


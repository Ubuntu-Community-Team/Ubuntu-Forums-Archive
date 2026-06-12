---
title: "MBR problems Vista &amp; Ubuntu 8.04 (EasyBCD)"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by project6 on 2008-08-04
Hi all.

I finally decided to install Ubuntu to fresh up my old Linux syntax a bit.

I successfully installed Ubuntu 8.04 on unallocated space using Guided mode (largest space available thing). After this, GRUB appeared on boot and I tried Ubuntu once. I fetched the menu.lst file cause I read I need this in order to re-add Ubuntu to the boot list after reinstalling Vista boot. I put this file so I can get it from Vista.

So I restarted, loaded up Vista and installed EasyBCD. I navigated to Add/Remove Entries, chose to install NeoGrub and opened the configuration. I replaced all the text in the almost empty menu file with the one from Ubuntu's menu.lst.

Now when I restarted I had two options - Vista and NeoGrub Bootloader. I tried NeoGrub Bootloader and was hoping to see the list I previosly had (with Ubuntu, Ubuntu safe mode etc) but all I see is a screen saying "loading MS-dos" and some text before that, then a couple of blinks (text appears too fast to be read) and then I'm back to my options again - Vista or NeoGrub.

I also tried removing the NeoGrub, adding a Linux entry (GRUB) on the Linux partition and checking "GRUB is not installed to bootsector", but the exact same thing happens.

Vista loads fine everytime, luckily enough.

Please help me to get this boot issues sorted.

best regards,
project6

---

### Post by jonnymccullagh on 2008-08-04
shot in the dark here (as I do not use Windows) but have you tried the LiveCD [SuperGrubDisk]("http://www.supergrubdisk.org/") which can help fix booting problems.

---

### Post by Pumalite on 2008-08-04
Check this:
[http://www.thorsten-lux.de/files/wiki.html](http://www.thorsten-lux.de/files/wiki.html)

---

### Post by project6 on 2008-08-04
Thanks for your replies.

I solved it. The guide I followed shrunk C: and therefore placed the NeoGrub files on C: (that's where I had my files as well)

I shrunk another drive letter, so I simply moved my NeoGrub files there and reconfigured the drive letter in EasyBCD and the boot menu showed up fine.

---


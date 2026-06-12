---
title: "how to fix bug 1159016 (can't make 13.10 Live USB persistent)"
date: 2013-11-05
forum: Installation &amp; Upgrades
---

### Post by LinuxVirgin2000 on 2013-11-05
Hi, there is a bug that when making Live USB with 12.10 onwards files and settings are not saved when booting on a UEFI computer.


there is a way to fix this bug as discussed here:
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1159016](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1159016)

quote from the above link:
"[COLOR=#333333][FONT=Ubuntu Mono]Thanks Fred. Yes the fix is simple enough, add the word "persistent" to the /boot/grub/grub.cfg vmlinuz kernel lines."


Can someone please explain to me in baby terms how to actually do this! I typed "[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]/boot/grub/grub.cfg" into nautilus but nothing was found.

thanks in advance![/FONT][/COLOR]

---

### Post by ubfan1 on 2013-11-05
On the live media itself, there should be a /boot directory, with a single grub directory in it.  You should be able to see this from any other running computer.  If you are running the live media, I think the stick will be mounted under /cdrom (not sure about this).  So try looking under /cdrom/boot/grub/grub.cfg.
The lines to change look like this (with some slight alterations):
linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
Add the word "persistent" just after "casper"
All this assumes that you actually created the stick with persistence (which still works on non-uefi machines.)

---

### Post by LinuxVirgin2000 on 2013-11-07
Hi, thank you very much for replying to my question.

I have tried your suggestion, I tried typing persistent after casper with no space, them with a space, then with a . and then with a /, each time a error message came up after selecting "try ubuntu without installing" when trying to boot.

how exactly am i supposed to write persistent? does it need any symbol between itself and the word casper?

would it help if i find out what the error message is that comes up and tell you it?


thanks again for you help :)

---

### Post by ubfan1 on 2013-11-07
Hmmm, don't have one to look at anymore, but maybe the location is more critical than I thought.  An older 10.04 example I have puts the word persistent right before the file=, like:
linux    /casper/vmlinuz.efi persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash

---

### Post by LinuxVirgin2000 on 2013-11-10
thanks that last one works perfectly! :)

---


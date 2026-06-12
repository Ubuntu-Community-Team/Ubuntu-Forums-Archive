---
title: "Installed Windos 7 and can't get Ubuntu back"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by cwdurand on 2011-02-04
I don't get a grub load.
I tried a new live cd on a cdrom and USB but I get errors and initramfs prompt.
-initial error was something about not finding fstab
-current error is:
stdin: error 0
/init: line 7: can't open/ dev/sdb: No medium found
--repeat of above--
mount: mounting /dev/loop0 (/cdrom/casper/filesystem.squashfs) on/ /filesystem.squashfs
The computer is dell inspiron 64 bit archetecture.
I managed to mount the root of my original install and can navigate the directories but there is little functionality. Which means sfdisk, and other slibs do not work.
Help me get my 10.10 ubuntu back and dual boot windows 7 please.

---

### Post by Quackers on 2011-02-04
elcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by cwdurand on 2011-02-04
will not boot.
I only get the error and the prompt

---

### Post by cwdurand on 2011-02-04
I'm downloading the image again. The file is much larger so far than it was before. Maybe I wasn't getting the whole thing. I'll post the results.

---

### Post by cwdurand on 2011-02-04
In fact 3 downloaded images were corrupt. Final image saved at about 711 MB
still got a boot error with prompt boot: repeating
I typed: live, thenhit enter. This booted directly to the live desktop. From there I followed the grub recovery at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
 
My volumes UUID was "Mut" but that didn't stop the grub from installing and discovering all the partitions on the sda.
 
Sorry if someone blew a fuse about this. I recommend anyone with an image issue first check the MD5 checksum.
 
now processing.............

---


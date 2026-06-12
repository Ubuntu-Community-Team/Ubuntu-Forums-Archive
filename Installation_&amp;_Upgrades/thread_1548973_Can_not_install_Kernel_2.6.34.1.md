---
title: "Can not install Kernel_2.6.34.1"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by deficit7 on 2010-08-09
I recently installed ubuntu 10.04 on my netbook and have been experiencing few glitches.  I was led to believe that some of this could be solved by updating the kernel from 2.6.32 to 2.6.34.1.  I downloaded the kernel blackjack and i have no problem installing the headers package and the source package, but when i try to install the image package i get an error that reads "Failed to install package 'linux-image-2.6.34.1-blackjack_2.6.34.1-1_i386.deb'"

By the way, the glitches I was hoping to fix were...
1) The screen brightness flickers back and forth between two levels when i boot the operating system and continue to do so until i click on something like a drop-down menu and scroll over the words.  If I adjust the screen brightness it starts doing the same thing again.
2) The internet doesn't work on a wired connection.  Only wireless.  The connection shows on the menu but it doesn't connect when i select it.  This is a more recent problem as it was working fine originally.
3) Occasionally when i boot ubuntu, none of the windows i open have the top menu bar with the exit, minimize and maximize buttons.  It stays this way until i restart my computer.

If anyone can help me with the kernel, or if anyone knows of a better way to fix these problems, your input would be greatly appreciated.  Thanks.

---

### Post by Bachstelze on 2010-08-09
Is that all the error message says?  Normally, you'd have a bit more information, try to install it from a terminal

```
sudo dpkg -i linux-image-2.6.34.1-blackjack_2.6.34.1-1_i386.deb
```

Alternatively, you can get a working 2.6.34 for Lucid from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)

---

### Post by deficit7 on 2010-08-11
When I use the terminal it won't let me install any of the packages.  It reads...

dpkg: error processing *"name of package"* (--intall):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *"name of package"*

However if I use GDebi Package Installer I have no problem installing any of them aside from the image file.  And you're right, it has a terminal button I didn't notice before that shows a longer error message:

(Reading database ... 134924 files and directories currently installed.)
Unpacking linux-image-2.6.34.1-blackjack (from .../linux-image-2.6.34.1-blackjack_2.6.34.1-1_i386.deb) ...
Done.
dpkg: error processing /home/aaron/Desktop/aaron/Blackjack/Kernel_2.6.34.1/linux-image-2.6.34.1-blackjack_2.6.34.1-1_i386.deb (--install):
trying to overwrite '/lib/firware/yamaha/dsl_dsp.fw', which is also in package linux-firmware 0:1.34.1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-34-generic
Found initrd image: /boot/initrd.img-2.6.32-34-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 9.04 (9.04) on /dev/sdal
done
Errors were encountered while processing:
/home/aaron/Desktop/aaron/Blackjack/Kernel_2.6.34.1/linux-image-2.6.34.1-blackjack_2.6.34.1-1_i386.deb

I'll try your alternative and see if I have better luck with that.

---

### Post by deficit7 on 2010-08-11
Ok, I downloaded the 2.6.34 kernel for Lucid.  If I try installing through the terminal I still get the "cannot access archive: No such file or directory" message.  And if I use Gdebi to open the following files
linux-headers-2.6.34-020634_amd64.deb
linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb
then the status reads
Error: Wrong architecture 'amd64'
The other files were installed successfully.  Are the amd64 packages just alternatives of the other headers and image files, or is it necessary to install these as well?

---

### Post by deficit7 on 2010-08-25
Ok I got it installed and now my internet and windows work just fine.  :)  The brightness settings still flicker when i adjust it and on startup but that's not a big deal.  I'll look for something else to fix that.

---

### Post by techxcell on 2010-08-25
> **deficit7 said:**
> Ok I got it installed and now my internet and windows work just fine.  :)  The brightness settings still flicker when i adjust it and on startup but that's not a big deal.  I'll look for something else to fix that.

Well... its just the setting in power manager. Un-check the dim display when idle. :)

---


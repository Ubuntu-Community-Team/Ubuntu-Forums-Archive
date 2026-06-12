---
title: "Breezy to Dapper, upgrade running kernel???!!!"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by bwiese on 2007-03-22
I have been going through the instructions for a breezy 5.10 to dapper 6.10 LTS dist-upgrade, but came across a serious warning about upgrading the kernel and wanted to see if anyone else received this warning and got through it alive?!  My server is about 1,000 miles away, so I can't take any risks on messing this up...

I updated my /etc/apt/sources.list for dapper, and ran the following command with output below:

---
bw@1u:apt $ sudo apt-get update && sudo apt-get dist-upgrade 
... (snip) ...
Preparing to replace locales 2.3.5-1ubuntu12.5.10.1 (using .../locales_2.3.18.2_all.deb) ...
Unpacking replacement locales ...
Replacing files in old package libc6 ...
(Reading database ... 36442 files and directories currently installed.)
Removing linux-restricted-modules-2.6.10-6-386 ...
Removing linux-image-2.6.10-6-386 ...

  You are running a kernel (version 2.6.10-6-386) and attempting to remove
  the same version. This is a potentially disastrous action. Not only
  will /boot/vmlinuz-2.6.10-6-386 be removed, making it impossible to boot
  it, (you will have to take action to change your boot loader to boot
  a new kernel), it will also remove all modules under the directory 
  /lib/modules/2.6.10-6-386. Just having a copy of the kernel image is not
  enough, you will have to replace the modules too.

    I repeat, this is very dangerous. If at all in doubt, answer
    no. If you know exactly what you are doing, and are prepared to
    hose your system, then answer Yes.
[COLOR="Red"]Remove the running kernel image[/COLOR] (not recommended) [COLOR="Red"][No]? No[/COLOR]
dpkg: error processing linux-image-2.6.10-6-386 (--remove):
 subprocess pre-removal script returned error exit status 1
Removing linux-restricted-modules-2.6.8.1-3-386 ...
Removing linux-image-2.6.8.1-3-386 ...
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.12-10-386
Found kernel: /boot/vmlinuz-2.6.10-6-386
Found kernel: /boot/vmlinuz-2.6.8.1-5-686-smp
Found kernel: /boot/vmlinuz-2.6.8.1-5-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Removing linux-image-2.6.8.1-5-686-smp ...
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.12-10-386
Found kernel: /boot/vmlinuz-2.6.10-6-386
Found kernel: /boot/vmlinuz-2.6.8.1-5-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Removing linux-restricted-modules-2.6-386 ...
Removing linux-restricted-modules-2.6.8.1-5-386 ...
Removing linux-image-2.6-386 ...
Removing linux-image-2.6.8.1-5-386 ...
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.12-10-386
Found kernel: /boot/vmlinuz-2.6.10-6-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

dpkg: initrd-tools: dependency problems, but [COLOR="Red"]removing anyway[/COLOR] as you request:
 linux-image-2.6.10-6-386 depends on initrd-tools (>= 0.1.75ubuntu2).
Removing initrd-tools ...
Errors were encountered while processing:
 linux-image-2.6.10-6-386
E: Sub-process /usr/bin/dpkg returned an error code (1)
bw@1u:apt $ 
bw@1u:apt $ uname -a
Linux 1u 2.6.10-6-386 #1 Fri Sep 15 12:41:20 UTC 2006 i686 GNU/Linux
---

So, should I have said "YES" to the 'potentially disastrous action'?  I think I have good sense about me, but I've been running this server on Ubuntu since warty and I'm just not sure how much I should trust a dist-upgrade process... especially when dealing with my only running kernel image!

Please advise! Thanks! =)
Brian

---

### Post by bwiese on 2007-03-22
answering my own post...

Ok, please disregard.... I had not rebooted since my last kernel upgrade, and so I was running 2.6.10 but already had 2.6.12 installed after I looked it /boot/grub/menu.lst.  So I just did a 'sudo reboot', verified that I was running in 2.6.12 with a 'uname -a' and then proceeded to continue with the Dapper upgrade by issuing 'sudo apt-get -f install' and that completed fine without any errors.

so, reboot first, start running the latest kernel - then do the dist-upgrade makes sense. =)

---


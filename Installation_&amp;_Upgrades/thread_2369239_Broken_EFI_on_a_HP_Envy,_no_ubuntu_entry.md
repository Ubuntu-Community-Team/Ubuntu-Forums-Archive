---
title: "Broken EFI on a HP Envy, no ubuntu entry"
date: 2017-08-20
forum: Installation &amp; Upgrades
---

### Post by Martin_Kellner on 2017-08-20
Tried to install 16.04 32 bit on a computer which previously had 14.04 64 bit on it, in a dual boot with win 10. The computer uses UEFI. Now, as before, if booting is left alone it boots into win 10. If I click f9 to choose boot option the old 64 bit EFI entry is still there but no word about the new 32 bit installation. I can find no way to boot the new 32 bit system. I have tried setting up a chroot (and succeeded with that part) and fixing it from there but have not really managed. I suspect the fault may be something about ubuntu not being installed in EFI mode or something like that but I don't know how to fix that. To boot from a live USB stick, the computer has to boot in legacy mode or it won't see the USB stick. Can anybody help me? If you need additional information just ask.

---

### Post by oldfred on 2017-08-20
If a 64 bit system, only 64 bit install is supported.
There are a few 64 bit systems with 32 bit UEFI, but they will not boot at all with 64 bit UEFI.

What model HP?

Most HP need a work around. HP (and others) violate UEFI spec that says NOT to use description as part of UEFI boot. And only valid description is "Windows Boot Manager". Depending on you configuration one or two of the various work arounds should be suitable. 

You may be able to install 32 bit Ubuntu in BIOS boot mode, only. But then cannot easily dual boot Windows as grub only boots other installs in same UEFI or BIOS boot mode as grub/Ubuntu is installed in & boots in.

Why 32 bit? There is almost no software now that needs that. Several years ago there were just a few apps that users wanted, so they still installed 32 bit even though 64 bit would otherwise be a better choice.

       Developer's discussion of deemphasis of 32 bit Ubuntu - Nov 2014 
[http://www.phoronix.com/scan.php?page=news_item&px=MTgzODE](http://www.phoronix.com/scan.php?page=news_item&px=MTgzODE)
[http://summit.ubuntu.com/uos-1411/meeting/22353/when-should-we-stop-making-32-bit-images/](http://summit.ubuntu.com/uos-1411/meeting/22353/when-should-we-stop-making-32-bit-images/)
Assuming your hardware is x86_64 capable (basically any modern Intel/AMD CPU) and have at least 2GB of RAM, you really should be running the 64-bit version.
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

---

### Post by Martin_Kellner on 2017-08-21
I was under the (perhaps antique) impression that 64-bit systems were more error prone and that there was no real point in going 64 bit anyway. Now that you have informed me of the opposite, I will try downloading and installing a 64-bit version. Might take a day or two though.

---


---
title: "Ralink 2860 drivers?"
date: 2008-11-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2008-11-21
Anyone know if the ralink 2860 drivers are currently in or working? I'm getting a card given to me that uses that driver & would like to know---pointing me to the diffs would be enough.......

---

### Post by plun on 2008-11-21
Fwiw....

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

2.6.28 kernel ?

---

### Post by autocrosser on 2008-11-21
Thanks plun---been there---done that already--I had heard that the .28 kernel was going to have "support" & was wondering about that--I know we are in line for the kernel real soon......do you know the link (I'm sure you do) to the diffs on the cooking kernels?

---

### Post by plun on 2008-11-21
> **autocrosser said:**
> Thanks plun---been there---done that already--I had heard that the .28 kernel was going to have "support" & was wondering about that--I know we are in line for the kernel real soon......do you know the link (I'm sure you do) to the diffs on the cooking kernels?

I came from this page and I didnt find any info about 2860

[http://linuxwireless.org/en/users/Drivers/rt61pci](http://linuxwireless.org/en/users/Drivers/rt61pci)

But also found this

> A driver for the 2860 has been added to Greg Kroah-Hartman's staging
tree. You can obtain this tree, a set of Quilt patches, here:
[http://kernel.org/pub/scm/linux/kernel/git/gregkh/patches.git/](http://kernel.org/pub/scm/linux/kernel/git/gregkh/patches.git/) (If
you need help getting the patchset, email me personally and I'll walk
you though it)

Now there do appear to be several other drivers on the webpage you
mentioned, and I'm not sure if all of those others are supported. Greg
could probably clear that up. But the 2860 support is coming.

[http://www.gossamer-threads.com/lists/linux/kernel/991850?page=last](http://www.gossamer-threads.com/lists/linux/kernel/991850?page=last)




Next step kernel.orgs labyrinths   :lolflag:    (I stay away..:))

---

### Post by autocrosser on 2008-11-21
Thank you for the information!! I'm inclined to wait until "official" drivers appear so I can test them--I can run my D-link G card until then--also have a Linksys 300 N router coming, so I think my speed will be increased anyway.....

---

### Post by fut21 on 2008-11-22
Maybe try this:
[https://launchpad.net/%7Estgraber/+archive/+files/rt2860-source_1.8.0.0-0ubuntu1~ppa2_all.deb](https://launchpad.net/%7Estgraber/+archive/+files/rt2860-source_1.8.0.0-0ubuntu1~ppa2_all.deb)

---

### Post by autocrosser on 2008-11-22
Thanks fut--I have that one bookmarked--If I can't wait I'll use it......

---

### Post by flyguy97 on 2008-11-22
Here is a walkthrough I posted after finally getting my 2860 based pci card up and running, most people that have tried the walkthrough are having success. Give it a try, if you have questions I am willing to support you. However, please post any questions or concerns on my thread. I am trying to help a lot of people and it would be easier to check just one thread instead of many, thanks.

[http://http://ubuntuforums.org/showthread.php?p=6135670]("http://http://ubuntuforums.org/showthread.php?p=6135670")
> **autocrosser said:**
> Anyone know if the ralink 2860 drivers are currently in or working? I'm getting a card given to me that uses that driver & would like to know---pointing me to the diffs would be enough.......

---

### Post by autocrosser on 2008-11-22
Thanks for the info flyguy--I want a option that is upgraded with the kernel & testable--we "try" to maintain stock stuff  (at least I do) so testing is not thrown off by custom-module additions--from what I'm hearing--it "should" be in the .28 kernel, so it should "just work"

I have looked at your solution already (couple of days ago) & applaud your handling--I really want NM in my system for testing use, so I thank you for the offer, but I will pass.

---

### Post by SonicSteve on 2009-01-19
This worked perfectly, 
I'm running 8.04 and a friend of mine had this card and couldn't make it work. Now I can give him the good news that this card will work. I would thank you for this post but I don't see the option to do it anymore.



> **fut21 said:**
> Maybe try this:
[https://launchpad.net/%7Estgraber/+archive/+files/rt2860-source_1.8.0.0-0ubuntu1~ppa2_all.deb]("https://launchpad.net/%7Estgraber/+archive/+files/rt2860-source_1.8.0.0-0ubuntu1%7Eppa2_all.deb")

---

### Post by autocrosser on 2009-01-19
Here's the one I've been using (nice to have it in sources.lst)

#Ralink wireless drivers
deb [http://ppa.launchpad.net/stgraber/ubuntu](http://ppa.launchpad.net/stgraber/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/stgraber/ubuntu](http://ppa.launchpad.net/stgraber/ubuntu) intrepid main

Cheers!!!

Hoping that it will be included in the .29 kernel........

---

### Post by autocrosser on 2009-01-22
OK!!!!!! Now it's official!!!!!

As of firmware 1.4, the sources for the Ralink Rt 2860/2870 are available to the kernel--no need to "roll-your-own" any more!!!!


:guitar:

Message: 5
Date: Wed, 21 Jan 2009 21:25:13 -0000
From: Tim Gardner [EMAIL="tim.gardner@canonical.com"]<tim.gardner@canonical.com>[/EMAIL]
Subject: [ubuntu/jaunty] linux-firmware 1.4 (Accepted)
To: [EMAIL="jaunty-changes@lists.ubuntu.com"]jaunty-changes@lists.ubuntu.com[/EMAIL]
Message-ID:
	[EMAIL="20090121212513.8720.77731.launchpad@cocoplum.canonical.com"]<20090121212513.8720.77731.launchpad@cocoplum.canonical.com>[/EMAIL]
Content-Type: text/plain; charset="utf-8"

linux-firmware (1.4) jaunty; urgency=low

  * Added firmware for RT 2860/2870
  * Copy license files.

Date: Wed, 21 Jan 2009 20:19:28 +0000
Changed-By: Tim Gardner [EMAIL="tim.gardner@canonical.com"]<tim.gardner@canonical.com>[/EMAIL]
Maintainer: Ubuntu Kernel Team [EMAIL="kernel-team@lists.ubuntu.com"]<kernel-team@lists.ubuntu.com>[/EMAIL]
[https://launchpad.net/ubuntu/jaunty/+source/linux-firmware/1.4](https://launchpad.net/ubuntu/jaunty/+source/linux-firmware/1.4)
-------------- next part --------------
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

Format: 1.8
Date: Wed, 21 Jan 2009 20:19:28 +0000
Source: linux-firmware
Binary: linux-firmware nic-firmware scsi-firmware
Architecture: source
Version: 1.4
Distribution: jaunty
Urgency: low
Maintainer: Ubuntu Kernel Team [EMAIL="kernel-team@lists.ubuntu.com"]<kernel-team@lists.ubuntu.com>[/EMAIL]
Changed-By: Tim Gardner [EMAIL="tim.gardner@canonical.com"]<tim.gardner@canonical.com>[/EMAIL]
Description: 
 linux-firmware - Firmware for Linux kernel drivers
 nic-firmware - Firmware for NICs (udeb)
 scsi-firmware - Firmware for SCSI controllers (udeb)
Changes: 
 linux-firmware (1.4) jaunty; urgency=low
 .
   * Added firmware for RT 2860/2870
   * Copy license files.
Checksums-Sha1: 
 3bb54c9796a2d045495274bd51f3c9689722b54d 774 linux-firmware_1.4.dsc
 1b8add1e886cf7289da873cd44871cf28bf812b1 3720037 linux-firmware_1.4.tar.gz
Checksums-Sha256: 
 4fe8ddf6e031c8c14156055f0db503357d37a59a52f04b09db2554b1c3172432 774 linux-firmware_1.4.dsc
 deba61d9d4d2aeb7e3e19f91ca30691ff6f0e1bc67903fc45b0006ec58e13751 3720037 linux-firmware_1.4.tar.gz
Files: 
 b8bf4673b6ac989da8ec5b079e1e19c9 774 misc optional linux-firmware_1.4.dsc
 be4680c49ab43bee013faa4ff412f2d2 3720037 misc optional linux-firmware_1.4.tar.gz

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEARECAAYFAkl3kh0ACgkQ/VwK2Iv57+YElwCfZb/4OKwfiOorrXs4h5ScvXFF
Uv8AoJTsU0BkqrgSZge4fNQEFjcwzvxm
=+XP2
-----END PGP SIGNATURE-----

------------------------------

---

### Post by gspat on 2009-01-22
Now that is great news!

---


---
title: "Installing Ubuntu 12.04 on an external HDD&#8213;problem"
date: 2012-06-03
forum: Installation &amp; Upgrades
---

### Post by LDJ95 on 2012-06-03
Hi all.

First off,  I apologise if this is in the wrong section of the forums, or if I'm otherwise breaking any rules. Please correct me if I am  :redface:

So, I'll try to keep this as brief as I can.
I've been trying to install Ubuntu 12.04 to my portable external HDD (USB-powered), and have run in to a few issues. The drive is ~931GB, (marketed as 1TB), and I've separated it into five partitions: a 750GB storage partition & a 60GB backup partition, a 110GB Ubuntu partition, a 10GB swap partition, and there's also about 1.5GB of unused, unformatted space.

I went about the installation from a LiveCD, and I seemingly successfully installed Ubuntu to the external HDD. Under the 'Something Else' option during the installation, I made sure to select my external HDD as the location to install GRUB (/dev/sdb), selected my Ubuntu partition (/dev/sdb3) as the location to install Ubuntu itself, and selected my swap partition as well (/dev/sdb4).

After, I tried booting off the external HDD, and was taken to the GRUB rescue menu:
   [I]error: unknown filesystem.
   grub rescue > _
[/I]
So, I booted back into my LiveCD and searched around for a bit, and on the way noticed that GRUB had been installed to */dev/sdb3* (my Ubuntu partition), under the folder */boot/grub*. From what I understand, this is because GRUB automatically installs where ever Ubuntu does? Maybe not.

Anyway, after going through the Fixing a Broken System and Troubleshooting guides on the Ubuntu website ([https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing), [https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)), I am still stuck with the same problem, and I'm clueless as to how to fix it.

I wouldn't call myself a Linux/Ubuntu newbie&#8213;I've been using it on and off for a few years now&#8213;but apart from knowing the basic way around a command line, my knowledge is very limited.

The only thing I can possibly think of is that the partitions need to be at the 'front' of the drive, if that even makes any sense? I've also attached a screenshot from GParted to illustrate the way my HDD is set out.

[IMG]http://s14.postimage.org/wqkwqonvl/Screenshot_from_2012_06_04_03_39_29.png[/IMG]

Any advice/help at all would be greatly appreciated.
Thanks for your time, and sorry for the essay :biggrin:

Liam.

---


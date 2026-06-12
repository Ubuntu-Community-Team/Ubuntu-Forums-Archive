---
title: "Triple Booting Failure"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by topnotchvariable on 2007-04-16
Alrighty lets get started from the top. I'm running an Intel Core Duo 2GHz Laptop (IBM Thinkpad R60 to be exact) I've been dual booting between XP and Edgy no problems for a few months now. Have not messed around with Edgy to any particular, i've installed Beryl and Automatix. Now it could be because the laptop is not mine and belongs to Durham College I don't know or really care but I decided (thinking it would be a smart idea) to install JaS Mac OS X 10.4.8 (with the updates to 10.4.9) now I made sure Ubuntu/XP worked b4 install and they did. So I went on and decided to install OS X on 12GB of unpartitioned space which was allocated after the Linux-Swap partition. The Mac install went perfect no errors or warnings, but on first boot attempt OS X started to boot showing the splash screen then crashed to a grey screen and would not go further, if an attempt to repair my system I managed to change the MBR to tell it to boot Ubuntu and well GRUB is not damaged and will not boot into Ubuntu (I plan on following steps outlined in these forums to fix it) but what I am wondering is how to get OS X to use GRUB as a bootloader instead of Chain0, should I install OS X after windows XP then install grub? I'm not too sure ( and if anyone is wondering XP survived the whole ordeal because i'm using it to type this post right now).

oh and another thing windows through an ifs can access my ext3 Ubuntu partition, it reads all the files

---

### Post by mac.ryan on 2007-04-16
Does [this]("http://wiki.osx86project.org/wiki/index.php/Multibooting") help in any way?

---

### Post by topnotchvariable on 2007-04-16
Sorry it doesn't. The thing is I already Have windows XP installed and Ubuntu, what I'm looking for is a way to install OS X86 last but not damage Grub in the process. Or if anything just use Chain0 for the boot loader (I have no idea how to configure it to do so)

---

### Post by mac.ryan on 2007-04-16
Same site, [different page]("http://wiki.osx86project.org/wiki/index.php/Install_On_A_Partition_Simple_And_Accurate"). The section "installing the bootloader" says how to configure grub menu.lst. Hope this time it helps! :)

As for Win accessing all the files on an EXT3 partition regardless of the permissions, see the [FAQs]("http://www.fs-driver.org/faq.html#not_sup_feat") on their site.

---


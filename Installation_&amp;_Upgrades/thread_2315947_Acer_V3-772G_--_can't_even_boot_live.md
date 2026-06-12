---
title: "Acer V3-772G -- can't even boot live"
date: 2016-03-03
forum: Installation &amp; Upgrades
---

### Post by jabbermacy on 2016-03-03
New here.

OK, so I disabled all the power options stuff, disabled secure boot, actually reinstalled Win10 X64 (home) from scratch (deleted ALL partitions), tried two different ISO downloads, TWO different USB writing softwares (both for LINUX, you know which two), **THREE different USB sticks** (Sandisk USB 3.0's) and I can NEVER get live to boot.   I'm about to give up.  It's giving me a LONG list of text errors, goes to the five dots screen, sometimes just reboots, sometimes hangs.  I'm pretty fed up with this 'easy' OS.  Let me know what to try next because I'm about 2 seconds from deleting ALL the Linux stuff I downloaded past two days... also, why's it so hard to put the MD5 next to the ISO download? 14.04 LTS x64, btw...

Thanks.

(oh yeah, my work lappy boots live FINE, BOTH have dual graphics, so that's not it... nice try)

---

### Post by hansmc2 on 2016-03-04
If your system came with windows 10 or 8 it probably has UEFI boot enabled in the bios. According to "[help.ubuntu.com/community/UEF]("https://help.ubuntu.com/community/UEFI")I" 14.04 was one of the first versions to support UEFI[SIZE=2]. It looks like[/SIZE][SIZE=2] the section "Installing Ubuntu for Single Boot with a Random Boot Mode" talks about booting from a live cd. You might want to read through the above document and see if any thing solves your boot issue. The relevant part is pasted  bellow.
[/SIZE]
> [B]
Installing Ubuntu for Single Boot with a Random Boot Mode[/B]

 If  you aren't multi-booting with another OS and you don't care about your  boot mode, you can forego some of the picky details of the preceding  procedure and install Ubuntu in whatever boot mode your computer happens  to pick. This procedure is **not recommended** for  multi-boot installations alongside existing UEFI-based OSes, because it  can result in a combination of one OS installed in UEFI mode and the  other in BIOS mode. Such setups will require post-installation repair or  other awkward steps to manage switching OSes. 
You should be able to get Ubuntu installed quickly using the following steps: 

[LIST]
[*][Create a LiveDVD or LiveUSB]("https://help.ubuntu.com/community/LiveCD#How-To_LiveCD_Ubuntu") of Ubuntu (>=12.04.2) **64bit**. 
[*]In your firmware, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). 
[*]Boot your PC using the LiveDVD or LiveUSB and choose "Try Ubuntu". If you get a **Secure boot** or **signature** error, you may wish to disable [SecureBoot]("https://help.ubuntu.com/community/UEFI#SecureBoot") as described [here]("https://help.ubuntu.com/community/UEFI#SecureBoot"), then retry to boot the disk. 
[*]Install Ubuntu from the Live CD/DVD or Live USB in the usual manner, then reboot the PC. 
[*]If  the PC does not load Ubuntu, boot your PC using the Live CD/DVD or Live  USB and choose "Try Ubuntu" once again. When the live session has  loaded, run [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") (see link for details). When Boot-Repair loads, click on the "Recommended repair" button, and write on a paper the URL (**paste.ubuntu.com/XXXXXX/**)  that will appear. Then reboot the computer. Do not run Boot-Repair  unless you have problems booting the computer; the expression "if it  ain't broke, don't fix it" applies to this tool. 
[*]This should fix most boot problems. If this does **not** fix your boot problems, please create a new thread in [this forum]("http://ubuntuforums.org/newthread.php?do=newthread&f=333"), describing your problem and indicating the URL you wrote in the previous step. 
[/LIST]
[SIZE=2]
[/SIZE]

---

### Post by oldfred on 2016-03-04
Since you reinstalled Windows, did you reinstall in BIOS or UEFI boot mode.
Windows does not convert from gpt to MBR correctly if you installed in BIOS mode. Better to be UEFI.
Then system partition tools will not work, until you remove backup gpt data with fixparts.
Post this:
sudo parted -l
sudo fdisk -lu

And it an be dual graphics.
Which graphic mode is used for Booting. Or can you set that in UEFI?
If Intel you need an Intel boot parameter, and if nVidia you need nomodeset. And some laptops need additional boot parameters for backlight or acpi.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[URL="http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710"]http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710
[/URL]
 # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic 



[URL="http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710"]
[/URL]

---

### Post by jabbermacy on 2016-03-07
^^ thanks for the help guys... YES, Win10 is in UEFI mode, so I'll use a more recent build and follow the cautions related to install ... one question: why is 14.04 LTS the default download if newer versions are 'better'?  (ie. secure boot capable?)  That's really confusing.

---

### Post by oldfred on 2016-03-07
As of 12.04.2 or later, it is possible to install Ubuntu on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). But best to use newest version to have latest software updates as UEFI fixes for newest hardware is more up to date in newer versions.

You typically also want newest Acer UEFI version also. UEFI is new to vendors also and they have had to make a lot of updates to UEFI/BIOS.

Lots of info on UEFI in link in my signature. 
Bit more complicated since UEFI has more features and is both UEFI and BIOS.

---

### Post by jabbermacy on 2016-03-07
There's GOT to be something fishy with the UEFI on this laptop -- I downloaded 15.10 x64, same result. Downloaded openSUSE x64 (yeah, I know) SAME result -- it could not even complete a full load to BEGIN install.  I keep getting these text errors, caught one about something SSD related, most are 'neauvux-blahblahblah' ... next time I'm taking a photo, but for now I have to assume the UEFI is at fault, NOT Ubuntu.

Thanks again, I'm not a quitter, but this one's pushing my patience (too old for this crap :D  )

---

### Post by jabbermacy on 2016-03-07
^^ NOPE, it's NOT the machine or UEFI -- it's unetbootin-windows-613.exe AND Universal-USB-Installer-1.9.6.3.exe problem - I guarantee it.
**RUFUS 2.7+ includes the ability to write the live USB as .GPT for UEFI install / use.**  For whatever reason, that Acer (running UEFI) is not compatible with ANY stick written with those two apps. RUFUS (I strongly believe) is the only one compatible with UEFI.  

Final issue (I hope) is an error about the version of syslinux ([http://imgur.com/GtPfZ6O](http://imgur.com/GtPfZ6O)).  No idea, so I let it grab the files from the net.  If this works, I'll update to 'SOLVED' later this week!

---


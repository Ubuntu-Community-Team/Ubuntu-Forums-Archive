---
title: "Upgrade to 10.10 - no grub..."
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by pg1192 on 2010-10-14
Well, on my desktop, I dual boot Windows 7 and Ubuntu.  I had upgraded my netbook's Ubuntu from 10.04 to 10.10, and it worked fine.  I still need to play around with it.  However, I tried doing the same on my desktop, and now Ubuntu won't boot.  I still have Windows, since I decided to keep the Windows 7 bootloader.  Now, grub won't even load.  There's a really quick message that says "Error: file not found" twice, and then the computer reboots.  It looks like it's not even getting to grub.

I did the upgrade on both computers by running update-manager -d.  I installed any updates for 10.04, then clicked the button for the distro upgrade.  There were no errors during the upgrade, but now Ubuntu won't boot.

Is there a way I can fix this, or do I need to just reinstall Ubuntu fresh from a 10.10 livecd?

Thanks!

---

### Post by oldfred on 2010-10-14
Did you go into win7 and then it will not boot? Do you have a Dell or HP or some windows software that likes to write into the first sector to hide security info?

Grub team looking for info:
[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html)
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
[http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable](http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable)
In Windows 7, I had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

### Post by zazootheparrot on 2010-10-14
Hello there,

I have an ubuntu 10.04 Lucid Lynx running on a Sony Vaio VGN-SZ740.  During the past week I've had a problem with the operating system  booting. It happened after I did the usual update of the system using  the update manager.
It's worth mentioning that I have a Linux/ Windows 7 dual boot but they  all worked fine before. Here's what I see in the GRUB page when I start  my computer:
```
GNU GRUB version 1.98-ubuntu 7
Ubuntu, with linux 2.6.32-25-generic
Ubuntu, with linux 2.6.21-25-generic (recovery mode)
Ubuntu, with linux 2.6.21-24-generic
Ubuntu, with linux 2.6.21-24-generic (recovery mode)
Ubuntu, with linux 2.6.21-23-generic
Ubuntu, with linux 2.6.21-23-generic (recovery mode)
Ubuntu, with linux 2.6.21-21-generic
Ubuntu, with linux 2.6.21-21-generic (recovery mode)
Memory test (memtest 86+)
Memory test (memtest console 115200)
Windows 7 loader (on/dev/sda1)
```After I choose the first one (as I always did), I get the following:
```
Ubuntu 10.04.1 LTS ava-laptop tty1
ava-laptop login .. [129.736043] tpm_tis 00:09: tpm_trasmit :tpm_send:  error 42 94967234
```and then it takes more that 3 minutes for ubuntu  to come up!!!

I would we grateful if anyone could could help me solve this issue,

Thank you in advance

---

### Post by pg1192 on 2010-10-14
The Windows 7 Bootloader works fine.  Windows itself boots perfectly, but when I select Ubuntu, which should make grub come up, I get the 2 file not founderrors, and the computer reboots.

---

### Post by crienoloog on 2010-10-14
> **pg1192 said:**
> The Windows 7 Bootloader works fine.  Windows itself boots perfectly, but when I select Ubuntu, which should make grub come up, I get the 2 file not founderrors, and the computer reboots.

Same problem here on HP Probook 4510s.
Disabled all HP protect tools... I woudl just love to get back to 10.04... :(

---


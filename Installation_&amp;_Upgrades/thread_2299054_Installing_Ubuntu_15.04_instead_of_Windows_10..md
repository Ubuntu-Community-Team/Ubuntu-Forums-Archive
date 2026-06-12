---
title: "Installing Ubuntu 15.04 instead of Windows 10."
date: 2015-10-15
forum: Installation &amp; Upgrades
---

### Post by alexey19 on 2015-10-15
Hello, friends. I'm looking for solutions of my issue. My laptop acer aspire v3-772g has a pre-installed windows 8, which was upgraded to win10. System runs through UEFI. I've been trying to install Ubuntu in UEFI mode, with turned off secure boot/fast boot e.t.c. from usb-live and cd-live versions. Every time I try to run live version it just stucks at loading logo of Ubuntu with 5 white dots below. When I turn UEFI to legacy mode, Ubuntu goes on fine, but during installation it says that "no os detected", it says also that space for installation is available , and when I go to disk partition it sees all of parts, including EFS, windows parts, windows-recovery parts e.t.c. So I have the question: how do I remove windows , and correctly install Ubuntu?

---

### Post by alexey19 on 2015-10-15
The main purpose is actually to remove win10, and feel free to install 2 different Linux OS. But I'm not sured about what to do with UEFI and partition and deleting win10. Don't know how to configure grub, don't know what to do with MRB or GPT, don't know what to use - legacy mode or UEFI.

---

### Post by sudodus on 2015-10-15
Welcome to the Ubuntu Forums :-)

Please think twice before removing Windows! In the future you may need be some program or peripheral device, that needs Windows. Make a complete backup or at least create recovery disks for Windows, so that you can get it back, if you change your mind. See the discussion in the following thread

[Is there a way to scrap Windows in a dual booting system without a format?](http://ubuntuforums.org/showthread.php?t=2298603)

-o-

I think that is would be easier to install Ubuntu, if you prepare the internal drive before.

Boot into Windows and shrink the Windows partition. Do not create any new partition, just leave the free space. Reboot.

It is a good idea to turn off secure boot/fast boot e.t.c. like you explained in the opening post. Notice that you must not only do it in UEFI, but also in Windows, because there is a 'fast boot' setting, that is actually a kind of hibernation, and that should be turned off in a dual boot system.

Then boot in UEFI mode with the Ubuntu install drive.

Use ***gparted*** and create a big partition for the root file system and a small partition for swap.

Start the installer and at the partitioning window you should select ***Something else*** and select the partition for the root file system (that you created with gparted). The swap partition should be selected automatically. At the bottom of the page you can select where to install the bootloader. If you have only one drive attached (except the live drive with the Ubuntu installer), you need not change the target for the bootloader, but check it anyway before you continue.

See also the following links and links from them

[Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by alexey19 on 2015-10-15
I have already installed ubuntu, launching it with nomodeset and deleted win10.  but now when i go to grub, start ubuntu, it cannot start. Think that problem is still in nomodeset, dont know how to fix it. Runing ubuntu from grub with parametre "nomodeset" gives me just purple screen, and running "as it is" just gets cycled - it throws me back to grub after attempting to load ubuntu.

---

### Post by sudodus on 2015-10-15
When Windows is deleted, I think there is no reason to run in UEFI mode. It is probably easier in BIOS mode.

Have you got nomodeset in the 'linux line' in grub? See this link and links from it concerning grub2.

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

---

### Post by oldfred on 2015-10-15
All models of Acer require you to set supervisor password & set "trust" on Ubuntu's efi boot files.

       Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)

---


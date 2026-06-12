---
title: "Ubuntu 18.04 x64 not booting with Secure Boot enabled"
date: 2018-05-07
forum: Installation &amp; Upgrades
---

### Post by priz0nmike on 2018-05-07
I reset my HP laptop today and partitioned the hard drive to allow space for a Ubuntu 18.04 amd64 install.  When I tried to install it, I would a message that the disk image I was using failed to authenticate.  So I disabled secure boot and got it installed.  I read [here]("https://wiki.ubuntu.com/UEFI/SecureBoot") that Ubuntu 18.04 amd64 should work with secure boot, but if I disable secure boot I get the same authentication error when I try to boot Ubuntu. Everything works fine if I disable secure boot, but I'm worried it could be a security issue.  This is my first time dealing with a dual-boot system, so I'm completely lost.

edit: the exact error that appears when I try to boot while secure boot is enabled is "Selected boot image did not authenticate.  press <enter> to continue."

---

### Post by oldfred on 2018-05-07
HP is not UEFI dual boot friendly.
And if you need any proprietary drivers, like for video or wi-fi, you cannot have UEFI Secure Boot on.

What model HP?

Some other HP, issues are often common across many models of same brand as same UEFI is used with just minor changes for hardware differences. Often bigger difference if AMD or Intel.
 HP UEFI boot order change with efibootmgr does not stick, but change in HP's UEFI does work
[https://ubuntuforums.org/showthread.php?t=2390309](https://ubuntuforums.org/showthread.php?t=2390309)
HP 11m reinstall Windows & dual boot with Ubuntu 16.04
[https://ubuntuforums.org/showthread.php?t=2389104](https://ubuntuforums.org/showthread.php?t=2389104)
Probook G4 470 Ubuntu works fine with UEFI and secure boot. 
[https://ubuntuforums.org/showthread.php?t=2381663](https://ubuntuforums.org/showthread.php?t=2381663)
HP 8470p 
[https://ubuntuforums.org/showthread.php?t=2379728](https://ubuntuforums.org/showthread.php?t=2379728) 
      
 Some HP will not boot a flash drive that is gpt partitioned. Some only boot from the USB2 port not USB3 ports.
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260)
HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216)

---


---
title: "Fresh install stuck at grub prompt"
date: 2018-07-10
forum: Installation &amp; Upgrades
---

### Post by powerjas on 2018-07-10
As requested starting my own thread.

I'm not dual booting windows or anything, trying to do clean install. 

I have tried installing ubuntu and kubuntu 18.04 and both will not get past the grub prompt after reboot. 

I did have kubuntu installed and working on the same system 5 days ago and did not encounter this issue. I had switched to fedora for a few days to try it out and was wanting to try ubuntu and got stuck with this issue.

Here's the boot-repair info right after the install - [http://paste.ubuntu.com/p/mqjVMqVYVn/](http://paste.ubuntu.com/p/mqjVMqVYVn/)

Here's the boot-repair after trying to use the auto repair option - [http://paste.ubuntu.com/p/kWZ4RS49tF/](http://paste.ubuntu.com/p/kWZ4RS49tF/)

I'm not very good in grub never had to really do anything in it, so don't know much about the command or how it works. 

The boot repair looks like grub is trying to do something with my usb device I used to install it with and also used to run boot-repair from 
grub-probe: error: cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

Thanks.

p.s. - I just installed pop_os 18.04 and it is working, I also installed unbuntu 16.04 LTS with no issues.

---

### Post by mIk3_08 on 2018-07-10
Hello powerjas...

I don't know how this works but maybe it can help you about the boot info.

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by mIk3_08 on 2018-07-10
you can also visit here for grub rescue thread;
[https://ubuntuforums.org/showthread.php?t=2229621](https://ubuntuforums.org/showthread.php?t=2229621)

---

### Post by paranoidcoder on 2018-07-10
Try and install without any internet access, so no WiFi or ethernet. That seems to be causing my issues. I was able to install without internet access successfully, followed by a failed installation with internet access, and then yet again a successful installation without internet access.

---

### Post by powerjas on 2018-07-10
Turning off internet worked for me as well, not sure what happening with updates during install but something isn't working right for sure. 

I was also able to update the system after it was booted up, and rebooted with out issue.

Thanks for the help

---

### Post by paranoidcoder on 2018-07-10
Awesome, glad it worked for you. Hopefully this gets resolved soon.

---

### Post by oldfred on 2018-07-10
Looks like related to these other threads.
You really should not have a grub entry from an Ubuntu install. Some of the others do not have any ubuntu entry. But Ubuntu's UEFI boot expects to find /boot/efi/EFI/ubuntu/grub.cfg but if really in grub folder it does not work.
> Boot0000* ubuntu	HD(1,GPT,d035eaa3-d265-47fc-b18d-f97df36a3326,0x800,0x100000)/File(EFIubuntushimx64.efi)
Boot0001* grub	HD(1,GPT,d035eaa3-d265-47fc-b18d-f97df36a3326,0x800,0x100000)/File(EFIgrubshimx64.efi)

Looks like update to grub was rolled out to 18.04 before fix that was applied to 18.10.
       Ubuntu 18.10 Cosmic installed /EFI/grub
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1775743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1775743)
manual boot, if drive is first drive, hd0 and partition gptX is your install partition like gpt3 or gpt8:
grub> set root=(hd0,gptX)
grub> configfile /boot/grub/grub.cfg

---

### Post by paranoidcoder on 2018-07-10
Have you heard any word of Canonical officially recognizing this bug, or a timeline for a fix?

---

### Post by oldfred on 2018-07-10
All you really can do is report a bug or add to an existing bug and then follow that bug to see what developers propose.

---

### Post by mIk3_08 on 2018-07-11
> **powerjas said:**
> Turning off internet worked for me as well, not sure what happening with updates during install but something isn't working right for sure. 

I was also able to update the system after it was booted up, and rebooted with out issue.

Thanks for the help

Hi powerjas. If this issue is already been solve kindly mark as solve. Thanks a lot

---


---
title: "Ubuntu on old ex-Win7 computer doesn't boot even after BootRepair"
date: 2019-10-29
forum: Installation &amp; Upgrades
---

### Post by sainnr on 2019-10-29
Hello,

I'm trying to replace Windows 7 on my old Sony VGN-TT31 (2009) with Linux. Installation goes fine, however, the system refuses to boot Ubuntu when starting up without live USB. 
The exact steps I followed (with different distros):
[LIST=1]
[*]Started with live USB and dropped old Windows partitions, created 3 new ones: efi, swap and ext4 for / 
[*]Installed Ubuntu 
[*]Restarted with USB off 
[*]Evidenced "this is not a bootable disc" 
[*]Restarted with USB in 
[*]Installed Boot-Repair and executed it with default options 
[*]Restarted with USB off, the same thing 
[/LIST]

Here is the log: [http://paste.ubuntu.com/p/fRvdzGY3zj/](http://paste.ubuntu.com/p/fRvdzGY3zj/)

Distros I tried so far:
[LIST]
[*] Ubuntu 16, 18, 19 -- shows "this is not a bootable disc" on startup 
[*] Linux Mint 18, 19 -- shows errors about missing files when starting from live USB (the message flickers quickly and it's hard to grasp what's written, but looks like something related to "BOOT" folder) and then freezes on live USB options menu ("try", "install" etc.) 
[/LIST]

For USB preparation, attempted with mkusb and Balena Etcher, same result.

FWIW, the laptop seems to have BIOS InsydeH2O with a quite limited set of options, so can't be 100% certain that loading under UEFI mode is supported by default (though I expect there's a way to bypass and get access to all of them). The live USB start screen looks like this: 
[IMG]https://pix.toile-libre.org/upload/original/1347445084.png[/IMG]

Two random guesses I have so far:
[LIST=1]
[*]There's something wrong with the live USB, otherwise why it shows a strange message about missing things in BOOT (looks like [https://askubuntu.com/questions/1085550/cant-install-ubuntu-18-10-on-xps-15-efi-boot-mmx64-efi-not-found](https://askubuntu.com/questions/1085550/cant-install-ubuntu-18-10-on-xps-15-efi-boot-mmx64-efi-not-found) or what it was?). I also see some complaints about missing files in Boot-Repair log. 
[*]There's no UEFI and only BIOS mode is supported 
[/LIST]

Any help is appreciated!

**Edit:** Another attempt with creating a live USB with Rufus from Windows (worked for me last time) and Linux Mint 18 led to the same result: "this is not a bootable disk". The steps sequence was the same, here's the Boot-Repair log: [http://paste.ubuntu.com/p/PhsZgDpvC6/](http://paste.ubuntu.com/p/PhsZgDpvC6/).
Will be trying with non-UEFI installation.

---

### Post by yancek on 2019-10-29
Your windows 7 was installed in Legacy mode and is not UEFI.  When windowss 7 was released, UEFI was not being used.  First thing you need to do is delete the EFI partition as that will not be used.  Take a look at the Ubuntu documentation at the link below on dual booting windows/Ubuntu in Legacy mode.  YOur boot repair output clearly shows that you still have windows code in the MBR of the drive and you will not be able to boot so make certain you install Grub to the MBR of the drive.

  [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by sainnr on 2019-10-29
Thanks a lot, looks like it worked! I removed efi partition, made sure I'm installing in compatibility mode and then ran BootRepair. After that, I managed to boot into Linux without live USB.

---


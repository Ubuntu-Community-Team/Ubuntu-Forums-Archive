---
title: "Adding Win10 (separate SSD) to existing Ubuntu 18.04 system (legacy boot)"
date: 2019-11-26
forum: Installation &amp; Upgrades
---

### Post by damiank2 on 2019-11-26
Currently running Ubuntu 18.04, with legacy boot, confirmed via:
```
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
```

Desired outcome:
[LIST]
[*]a dual boot system, with existing Ubuntu install on 1 SSD, and Win10 on another new one.
[*]grub menu offering both OS
[*]ideally want to avoid doing anything that prevents a simple regression back to plain Ubuntu system.
[/LIST]

I've read various posts but haven't seen anything (yet) that exactly fits. But i think it may be as simple as:


[LIST=1]
[*]Disconnect existing Ubuntu SSD and connect new SSD
[*]Boot from Win10 install USB and install.
[*]Reconnect Ubuntu SSD and set bios to boot into Ubuntu
[*]Run boot-repair in Ubuntu to update grub to show both OS in grub menu.
[/LIST]

is it really this straightforward? (and apologies if i've missed a thread which explains this.)

---

### Post by oldfred on 2019-11-26
If Windows is also BIOS boot, then you do not even need Boot-Repair.
Just boot into Ubuntu and run sudo update-grub.
Although I like to run Boot-Repair just to document system. I usually run bootinfoscript which is the first part of Boot-Repair as part of my normal backup.

Some UEFI based hardware, forgets boot entries in UEFI, if drive is disconnected and you have to restore those. Not sure if UEFI but BIOS booting.

Is hardware newer and UEFI based?
If so at some point you may want to consider changing to UEFI installs.

Windows requires MBR with BIOS installs and gpt with UEFI installs.
How you boot install media for both Windows & Ubuntu UEFI or BIOS, is then how it installs.

---

### Post by C.S.Cameron on 2019-11-26
I have just moved Windows to it's own drive.
Both drives BIOS boot.
I simply set the Ubuntu drive as first drive then ran update-grub.
Windows will boot via win bootloader when I press f12.

---

### Post by yancek on 2019-11-27
The information you posted is minimal and if you haven't resolved this situation, answer the questions asked above and/or read the Ubuntu documentation on dual booting with windows 10 at the link below which should answer most of your questions.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by damiank2 on 2019-11-27
> **oldfred said:**
> If Windows is also BIOS boot, then you do not even need Boot-Repair.
Just boot into Ubuntu and run sudo update-grub.
Although I like to run Boot-Repair just to document system. I usually run bootinfoscript which is the first part of Boot-Repair as part of my normal backup.

Some UEFI based hardware, forgets boot entries in UEFI, if drive is disconnected and you have to restore those. Not sure if UEFI but BIOS booting.

Is hardware newer and UEFI based?
If so at some point you may want to consider changing to UEFI installs.

Windows requires MBR with BIOS installs and gpt with UEFI installs.
How you boot install media for both Windows & Ubuntu UEFI or BIOS, is then how it installs.

> **C.S.Cameron said:**
> I have just moved Windows to it's own drive.
Both drives BIOS boot.
I simply set the Ubuntu drive as first drive then ran update-grub.
Windows will boot via win bootloader when I press f12.

many thanks both, sounds like a plan.

---


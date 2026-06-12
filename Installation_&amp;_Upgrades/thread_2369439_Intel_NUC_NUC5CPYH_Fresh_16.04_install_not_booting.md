---
title: "Intel NUC NUC5CPYH: Fresh 16.04 install not booting"
date: 2017-08-23
forum: Installation &amp; Upgrades
---

### Post by mlester2 on 2017-08-23
Hi everyone,

I just installed Ubuntu 16.04 from the mini.iso on a Intel NUC NUC5CPYH. The installation works flawlessly. When it reboots, the only thing I see after the UEFI menu of the NUC is this:

/dev/sda1: clean, 121563/920272 files, 701079/3680256 blocks

And a blinking cursor underneath. Nothing else happens. No HD activity, nothing.

What could be wrong here?

---

### Post by gordintoronto on 2017-08-23
Most of the time, "nomodeset" solves this problem.

[https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu)

---

### Post by copperlizard on 2017-09-26
I'm also having trouble with a NUC5CPYH; I updated the bios and installation (Ubuntu Server) went fine. Even spent 15 or 20 min tooling around before shutting the machine down. Now it won't boot. Just hangs up after "started auto import assertions from block devices." No error/failed messages. Just freezes. 

I'm new to Ubuntu/Linux, and would love some help solving this problem.

Update: sorry for invading the thread; I thought our problems were similar enough... I seemed to have fixed mine for the moment. I changed the BIOS settings to use legacy boot mode and reinstalled. I haven't had any more trouble yet (fingers crossed).

PS: this doesn't help me, but might help somebody else:
"[COLOR=#000000][FONT=opensans]Each time we would install one of our Debian-based distros (Ubuntu, Mint, or SteamOS), the NUC would boot to the USB drive and install the operating system to the internal mSATA SSD without issue. The problem was that the NUC wouldn't see the drive as a EFI boot target, and it would refuse to boot from the drive..."[/FONT][/COLOR]

suggests a couple possible solutions.

[https://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/](https://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/)

---

### Post by wildmanne39 on 2017-09-26
Welcome to the forum copperlizard please start your own thread so you and the OP of this thread can get the help you need.

---


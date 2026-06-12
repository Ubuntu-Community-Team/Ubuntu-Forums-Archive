---
title: "Grub freezes (and overall glitchy) on fresh 18.04 dual-boot install"
date: 2022-04-16
forum: Installation &amp; Upgrades
---

### Post by printf42 on 2022-04-16
Hi all, 

In short the problem is: Grub menu glitches out (arrow down key) jumps the selection from top to bottom.

Selecting anything from the grub menu makes the system freeze (including pressing 'e' to open the editor).  I can log-in to the (Ubuntu system only, since, again, selecting anything else from the grub menu freezes the system) if I let it do its automatic countdown and let it boot Ubuntu.

Here is my boot-repair log: [http://paste.ubuntu.com/p/VR9v4pW3VJ/](http://paste.ubuntu.com/p/VR9v4pW3VJ/)

I'm guessing it has something to do with my video card... I cannot get the system to show the actual model of the card (nvidia gtx 1650) at all...

---

### Post by grahammechanical on 2022-04-16
I see this.

> Unknown BootLoader on sda3

But sda3 is the extended partition. In Ubuntu please run

```
sudo update-grub
```

Does Grub detect both Windows 8 and Windows 10? The three operating systems are installed in legacy/mbr/csm mode. When that is the case and there is one drive and it is Master Boot Record (MBR) partition table we can re-install Grub with

```
sudo grub-install /dev/sda
```

That will install the updated Grub into the Master Boot Record (MBR). It may solve the problem. With BIOS boot and not UEFI and on an MBR partitioned drive the Grub boot loader goes into the drive's MBR and not into a partition. That may or may not be the case.

Regards

---

### Post by tea for one on 2022-04-17
[COLOR="#0000FF"]Line 5[/COLOR] -  Grub2 (v2.00) is installed in the MBR of /dev/sda
[COLOR="#0000FF"]Line 48[/COLOR] - OS#1:   The OS now in use - Ubuntu 18.04.6 LTS CurrentSession on sda5
[COLOR="#0000FF"]Line 49 [/COLOR]- OS#2:   Windows 10 (boot) on sda1
[COLOR="#0000FF"]Line 50[/COLOR] - OS#3:   Windows 8 or 10 on sda2
[COLOR="#0000FF"]Line 63[/COLOR] - The firmware seems EFI-compatible, but this installed-session is in Legacy/BIOS/CSM mode (not in EFI mode)

Your Operating Systems are installed in old-style mbr/bios.
In order to be more future-proof, it would be advisable to:-

Back up all your personal data
Install Windows 10 and Ubuntu 20.04 (or soon to be released Ubuntu 22.04) in UEFI mode with GPT.

If you need help with this, please reply in this thread.

---

### Post by printf42 on 2022-04-17
Thank you very much for the replies - I could not get it to work, so I wiped the whole disk and installed a fresh 20.04.

---


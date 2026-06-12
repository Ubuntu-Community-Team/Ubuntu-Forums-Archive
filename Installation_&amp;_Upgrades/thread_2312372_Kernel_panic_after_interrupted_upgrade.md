---
title: "Kernel panic after interrupted upgrade"
date: 2016-02-03
forum: Installation &amp; Upgrades
---

### Post by charlie_bravo2 on 2016-02-03
I have the problem listed there in the subject.  To go into excruciating detail, I had an HP laptop, that had hardware troubles that necessitated a replacement.  I had a 1TB drive installed, on which I had a dual boot configuration with xubuntu 14.04 and Win7.  I pulled this drive, and dropped it into my new ([Dell Inspiron i5759-4129BLK]("https://smile.amazon.com/gp/product/B015JV7LQK/ref=oh_aui_detailpage_o03_s00?ie=UTF8&psc=1")) computer today, and it ran well until I tried to play a video, and I had no sound.  I attempted several fixes recommended on this forum, to no avail, but I saw that there was a new version of the OS available, so I ran:

sudo update-manager -d 

The update manager suggested version 16.04 and I proceeded.  The process had advanced through to the Installing the Upgrades step when the entire system froze.  I tried to be patient, and I let it sit like this for about two hours, pointer not moving, no response from keyboard, no activation of any power-save.  I powered down the system, hoping that on reboot it would pick up where it had left off.  Instead, it now gives a kernel panic on power-up, the caps lock key flashes for a bit, and then the laptop powers off.  An internet search yields several possibilities for a kernel panic, one of which is "Hosed update/upgrade".  Yeah, I am the Captain of the HumpedShip.

The system reboots, and GRUB gives me the usual options.  I have tried selecting Ubuntu, and Advanced Options for Ubuntu, the latter of which gives me the option of selecting any of the previous versions, from "Ubuntu, with Linux 4.4.0-2-generic" to "Ubuntu, with Linux 3.13.0-59-generic, and each of these includes the (systemd), (upstart), and (recovery mode) choices.  So far I have tried the normal and the (recovery mode) options from both 4.4.0-2-generic and 3.13.0-77-generic, each of which errors out with a kernel panic.  Those are the things I have tried.  Things I have not yet tried are the other two modes, (systemd) or (upstart), for any of the versions, nor have I tried all of the other versions I didn't mention above.  I also haven't bothered to try booting into Win7, as I can't see how that would do any good repairing the Ubuntu partition.

Now, having described the symptoms, the questions are "Can this be repaired without losing the data on the drive?" and "If so, would someone please be so kind as to provide a step by step method for that repair?"

Thanks in advance, and please feel free to ask any questions that I can answer if I have left out any information required to help with this matter.

Charlie

---

### Post by charlie_bravo2 on 2016-02-03
Update:
Ubuntu, with Linux 3.13.0-77-generic (systemd) boots and gets me to a command prompt.  Cursory attempts to attempt repair unsuccessful, as no network adapters are in evidence when I run ifconfig.

---

### Post by charlie_bravo2 on 2016-02-05
Solved it myself.  Downloaded the ISO for 16.04 64bit,  Made a bootable USB stick, booted, and when asked, clicked on "Install Xubuntu".  The installer discovered my hosed upgrade, and repaired everything with virtually no fuss.  All is good

---


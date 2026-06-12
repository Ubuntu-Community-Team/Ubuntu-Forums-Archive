---
title: "Multiboot - In over my head"
date: 2005-11-07
forum: Installation &amp; Upgrades
---

### Post by waslost1 on 2005-11-07
I thought I was getting the hang of this stuff but Once again I have proven that I need to learn more. Here is what I have.

Dell machine with 2 hard drives installed.
Drive 1 Partition 1 is Windows 2k NTFS
Drive 1 partition 2 is just files FAT32
Drive 1 partition 3 is freeBSD (default file systems)
Drive 2 Ubuntu Linux (default file system)

I installed Windows a long time ago. Later I decided I wanted Ubuntu and installed it on the second hard drive. It set up the Grub loader so I could dual boot. I figured, hey If I can do that then surely adding freeBSD would be just as easy. <sigh>

Anyway, I got freeBSD installed although I have no idea what I was doing, it does run but it installed a new boot loader called booteasy??? I think. Anyway, it did not pick up my Ubuntu on the second hard drive so all I can do is boot to freeBSD or Windows.

I want my Ubuntu back! What are my options here. Keep it simple, I am really really new to this. I probably should not have been installing freeBSD, but hey that is how we learn right?

---

### Post by BLTicklemonster on 2005-11-08
Whoa, wait a minute, how exactly did you set that up to dual boot on two different drives in the first place? I have xp on one drive, and ubuntu on another, and I want to be able to dual boot. Would you please be so kind as to tell me how you did that? I'm a total newb, so you may want to include stuff like "use your fingers to tap the little things with letters on them, they are attached to a flat rectangular shaped thing wired into the back of your computer. most people call it a keyboard, but there's no telling if people like you know what that means, newb-ticklemonster". :)

Please.

---

### Post by Cufishing on 2005-11-08
Yes, I felt your pain. My first install was very similar. Everything worked fine, the I needed windoze for something, and once that loaded, the bootloader was gone forever.

I have yet to learn why, but it has something to do with M$ and check disk during boot cycle. If the '2nd' OS is not present on the primary HDD, the the MBR gets re-written, and drops the GRUB.

I recall a person downloding from download.com a multi boot bootloader, and installing it into the MBR. It worked, but I had already rebuilt my system and have yet to try it.

If you ever lose your MBR from M$, you would load your M$ CD and boot from CD, use the recovery command, and once you got the DOS prompt you would fixmbr to re-enable the boot to M$, but would destroy any bootloader insatlled.

Sorry I can't help fix the problem.

---


---
title: "Errors when starting and shutting down the computer"
date: 2022-06-28
forum: Installation &amp; Upgrades
---

### Post by lovenguyen on 2022-06-28
When I turn on the computer and turn off the computer I got an error like the video at the link below:
[https://youtu.be/5UlRIcNT_lc](https://youtu.be/5UlRIcNT_lc)
[https://www.youtube.com/watch?v=cjemfX4fkm4](https://www.youtube.com/watch?v=cjemfX4fkm4)
The  report online:[https://paste.ubuntu.com/p/WRyBd57F9q/](https://paste.ubuntu.com/p/WRyBd57F9q/)
Thanks to the support forum to fix the above error as soon as possible without reinstalling and without losing data on the computer.

---

### Post by tea for one on 2022-06-28
[COLOR="#0000FF"]Line 22[/COLOR] - You have a BIOS boot partition sda1
[COLOR="#0000FF"]Line 28[/COLOR] - Also an EFI partiton sda2
An installation in UEFI mode would not create a BIOS boot partition, do you know how that happened?

[COLOR="#0000FF"]Line 255[/COLOR] - The boot of your PC is in BIOS-compatibility/CSM/Legacy mode. You may want to retry after changing it to UEFI mode

In your UEFI settings, can you disable Legacy Boot Mode and then reboot?
Any good?

---

### Post by lovenguyen on 2022-06-30
Thanks but: 
1. I replaced window to use ubuntu so no partition.
 2. My computer's BIOS is in Legacy mode so I use MBR

---

### Post by Impavidus on 2022-07-01
Partitions aren't something unique to dual boot systems. Every non-empty hard drive has partitions, at least one. (Technically, you can create a filesystem directly on the drive, without partitions, but this is not recommended and for bootable drives not allowed.)

In legacy mode, you can choose between GPT and MBR. In UEFI mode, GPT is mandatory. It looks like your drive is GPT partitioned, but it has both grub in the first sector with a bios_boot partition (used for legacy) AND a non-empty EFI partition (used for UEFI). It seems you tried both UEFI and legacy. On somewhat recent hardware (later than 2015), I'd recommend UEFI and GPT, but when single-booting like you do, legacy should work too.

As for preventing data loss, I recommend backups. Use your live disk to create them, if you haven't already.

---

### Post by lovenguyen on 2022-07-19
ok , thanks for support

---


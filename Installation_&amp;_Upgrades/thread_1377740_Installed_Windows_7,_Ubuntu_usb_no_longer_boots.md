---
title: "Installed Windows 7, Ubuntu usb no longer boots"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by Spongeloaf on 2010-01-10
I had Karmic 32bit set up to use my whole hard drive, in one partition. (Excluding swap space of course) In order to dual boot Windows 7, I re sized the partition, and let windows install itself on the unallocated space. As I expected, Windows disabled GRUB, and the computer can no longer boot into Ubuntu. I used Unetbootin to create a Live Jaunty USB drive in order to boot from it, and re-install GRUB. 

However, I can no longer boot from the USB drive. I checked the MD5sum of several versions; 9.04, 9.10 and 9.10 64bit, but they all hang during boot on: 

"Verifying DMI pool data" 

I'd like to get Ubuntu running again, Windows 7 is better than Vista, but I'm much more comfortable with Ubuntu. I'm running an AMD 64 bit dual core CPU, and a Gigabyte GA-MA74GM-S2 mother board, set up to boot from USB drives first. I've booted from USB drives before, the only difference now is Windows. I did some searching here and with Google, but found nothing. I have no idea why this happens, or what to do about it. Any help is appreciated.

Thanks

---

### Post by darkod on 2010-01-10
1. You do not reinstall grub2 that Karmic uses with a Jaunty cd/usb. It includes only grub1. You need Karmic cd/usb.

2. The resize might have messed up your / partition. You are probably better to boot with the karmic usb, Try Ubuntu option (/ from your hdd install is not mounted then) and in terminal execute:
sudo fsck /dev/sda1 (or what ever your / partition is)

That will run a check on the partition.

---

### Post by Spongeloaf on 2010-01-10
> **darkod said:**
> 1. You do not reinstall grub2 that Karmic uses with a Jaunty cd/usb. It includes only grub1. You need Karmic cd/usb.

2. The resize might have messed up your / partition. You are probably better to boot with the karmic usb, Try Ubuntu option (/ from your hdd install is not mounted then) and in terminal execute:
sudo fsck /dev/sda1 (or what ever your / partition is)

That will run a check on the partition.


I have tried both Karmic and Jaunty USB drives. Neither gets farther than "Verifying DMI pool data" Therefore, it is currently impossible for me to boot my computer into Ubuntu.

---

### Post by darkod on 2010-01-10
Is it an option to boot with cd?

---

### Post by Spongeloaf on 2010-01-10
> **darkod said:**
> Is it an option to boot with cd?

  My DVD drive has been acting up lately, and I have no disks handy.

---

### Post by phillw on 2010-01-10
Hi

Verifying DMI pool data

Is done pretty early on jjst after the POST, as the computer gets ready to send information to the OS for booting.

This link has some pointers on it --> [http://www.duxcw.com/faq/computer/dmi.html](http://www.duxcw.com/faq/computer/dmi.html)  

As you mention that your DVD drive is 'playing up' - I'd suggest disconnecting it along with those hints, in case it is causing a hang.

> Therefore one should be aware that the message *Verifying DMI Pool Data...* is the last message given from BIOS before booting the operating system. What happens next is not recorded on the computer screen. This means that a defective power supply or other hardware device may be the culprit.

Regards,

Phill.

---

### Post by Spongeloaf on 2010-01-10
Thanks Phillw and Darkod. I'll look into the possibility of hardware failure.

EDIT: I've been very busy this last week, so I didnt get around to trying anything until yesterday. I disconnected all drives, except the USB disk, and still no dice. My EEE running Xubuntu made a boot disk that it can boot, but my 7/Ubuntu machine cannot. It's the infamous "Could not load Kernel image" error. Since that error does not pertain this thread, it should probably be locked.

---


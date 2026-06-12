---
title: "boot problem on Lenovo ThinkPad X1 with preinstalled Ubuntu"
date: 2024-07-27
forum: Installation &amp; Upgrades
---

### Post by robbi60 on 2024-07-27
I just bought a ThinkPad X1 with Ubuntu 22.04 LTS preinstalled (no Windows). I wanted to install a fresh version, with a personal partition. I tried the Ubuntu Cinnamon 24.04 LTS. Everything was fine, except the boot. If I take Ubuntu at start it doesn't work. It starts only by using the recovery mode and re-running the grub configuration. I run also boot-repair and here the result :
[https://pastebin.ubuntu.com/p/jTt2wbz2QJ/](https://pastebin.ubuntu.com/p/jTt2wbz2QJ/)

I am doing something wrong and I looked for many similar situations in the forum, nothing working. Any idea? Thanks a lot.

---

### Post by tea for one on 2024-07-27
Advanced Options > Recovery > Update Grub Bootloader
You select this every time?
And, you always arrive at your desktop?

---

### Post by robbi60 on 2024-07-27
yes, so in some sense it is conforting that it is not a major problem

---

### Post by tea for one on 2024-07-27
Therefore, next time you arrive at your desktop, it may be worth re-installing Grub from a working session.
Open a terminal and enter:-
```
sudo grub-install /dev/nvme0n1
```
```
sudo update-grub
```
Any terminal messages?

Power off then boot from cold
Any good?

---

### Post by robbi60 on 2024-07-27
From the first command I obtained 

```
Installazione per la piattaforma x86_64-efi.
Installazione completata, nessun errore segnalato.
```

with the second one. 
```
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.8.0-39-generic
Found initrd image: /boot/initrd.img-6.8.0-39-generic
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Adding boot menu entry for UEFI Firmware Settings ...
done
```

But unfortunately the situation remains the same. I am locked from the main entry and I can access only from the "recovery" way. 
Thanks a lot for the suggestion, anyway! r

---

### Post by robbi60 on 2024-07-27
Anyway I run again the boot-repair and I obtained this report [https://paste.ubuntu.com/p/qCwB4KjtYh/](https://paste.ubuntu.com/p/qCwB4KjtYh/)

---

### Post by tea for one on 2024-07-27
> **robbi60 said:**
> But unfortunately the situation remains the same. I am locked from the main entry and I can access only from the "recovery" way.
That's disappointing, but, let's bash on
Something, somewhere has got grub in an armlock
```
sudo nano /etc/default/grub
```
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
[s]GRUB_DISABLE_OS_PROBER=false[/s] [COLOR="#0000FF"]delete this line[/COLOR]
```
```
sudo update-grub
```
Fingers, arms, legs and toes crossed............

---

### Post by robbi60 on 2024-07-28
Bad luck! it doesn't work! But thanks again for keep trying!

---

### Post by tea for one on 2024-07-28
Still here, still trying...............

How about a radical option?
Bypass grub completely and boot the kernel directly?
I keep a USB with rEFInd for emergency use, it often helps to find and boot an OS (if Grub is damaged/not responding)

Install rEFInd on a USB stick temporarily to see if it offers any improvement. 
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)
[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html) > A USB Flash Drive Image File

Options include:-
(a) Boot the kernel directly
e.g. Boot boot\vmlinuz-6.2.0-35-generic from 35 GiB ext4 volume

(b) Find and boot the grub efi file
e.g. Boot EFI\ubuntu\grubx64.efi from 510 MiB FAT volume

(c) Start an EFI shell
The boot instructions are similar to this:-
Identify your Efi System Partition e.g. FSO
Type FSO: i.e. FSO and colon symbol (press enter)
Then type \EFI\ubuntu\grubx64.efi (and hit enter)

Try option (a) first.

If successful, rEFInd is in the universe repo for permanent installation.

---

### Post by robbi60 on 2024-07-28
Ok, this solution works very well, just some works to understand the usage of this powerful piece of software. So, even if I don't understand why grub is not working I can consider this problem as SOLVED. 
Many thanks again. r

---


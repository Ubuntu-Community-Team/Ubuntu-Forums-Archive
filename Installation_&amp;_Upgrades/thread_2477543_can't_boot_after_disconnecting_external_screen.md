---
title: "can't boot after disconnecting external screen"
date: 2022-07-29
forum: Installation &amp; Upgrades
---

### Post by nizarmb on 2022-07-29
Hello all,

- I previously had windows installed on my laptop, but I completely removed it and installed Ubuntu 20.04.4 LTS, and I've been using it for months with no issues.
- I have an external screen connected to my laptop, and I usually hibernate instead of shutting down.
- yesterday, I disconnected the screen then turned my laptop on, and ubuntu not starting up at all. All I get is "boot menu" dialog with "ubuntu" and other options available, clicking any of them including ubuntu does nothing but shows the "boot menu" dialog again.
- I used a live ubuntu image to run "boot-repair", here's the bootInfo summary: [https://paste.ubuntu.com/p/R2HmMDPhMD/](https://paste.ubuntu.com/p/R2HmMDPhMD/)
- Note I didn't even have a "recommended repair" option when boot-repair finished scanning.

I have no clue what to do, any help will be extremely appreciated

---

### Post by tea for one on 2022-07-29
[COLOR="#0000FF"]Line 36[/COLOR] - 0 OS detected

Your drive sda does not display any Linux partitions such as ext4.
You only have two partitons sda1 and sda2, which are both Windows ntfs format?

Does your laptop have more than one internal drive?

---

### Post by nizarmb on 2022-07-29
Thanks @tea for one for your reply.

Yes I have 2 drives, a 256GB SSD drive and 1TB HDD drive. but sda1 and sda2 seem to be the 2 partitions on the 1TB

please find below output of "sudo fdisk -l"
note my /dev/sdb1 is my USB drive
and I can't see my 256 SSD drive

```

Disk /dev/loop0: 2.13 GiB, 2285019136 bytes, 4462928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 61.93 MiB, 64917504 bytes, 126792 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 54.24 MiB, 56872960 bytes, 111080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 65.22 MiB, 68378624 bytes, 133552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 43.6 MiB, 45703168 bytes, 89264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 248.78 MiB, 260841472 bytes, 509456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000LM035-1RK1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: DF081A34-8DEF-4109-9EDA-0069A77CD5AE

Device          Start        End    Sectors   Size Type
/dev/sda1        2048 1016823807 1016821760 484.9G Microsoft basic data
/dev/sda2  1016823808 1953521663  936697856 446.7G Microsoft basic data


Disk /dev/sdb: 28.67 GiB, 30765219840 bytes, 60088320 sectors
Disk model: Cruzer Blade    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x231a0d42

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 60088319 60086272 28.7G  c W95 FAT32 (LBA)

```

---

### Post by tea for one on 2022-07-29
Boot-repair has only identified one internal drive:-
[COLOR="#0000FF"]Line 92[/COLOR] - Disk sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors

Can you jump into your UEFI settings and see if the 256GB SSD is visible?

---

### Post by tea for one on 2022-07-29
> **nizarmb said:**
> 
please find below output of "sudo fdisk -l"
note my /dev/sdb1 is my USB drive
and I can't see my 256 SSD drive

If you add extra details to your earlier post, other forum members, who wish to help, may have difficulty following the chronology.

---

### Post by nizarmb on 2022-07-29
Thanks for the note regarding post edits.

Regarding UEFI I can see NVMe but it's not showing in boot menu, here's my bios boot menu: [https://ibb.co/B4GjXNW](https://ibb.co/B4GjXNW)
[IMG]https://ibb.co/B4GjXNW[/IMG]

---

### Post by tea for one on 2022-07-29
Boot priority 2 is NVMe
Boot priority 4 is Ubuntu

What happens if you select either of those choices?

---

### Post by nizarmb on 2022-07-29
NVMe is showing in bios config only and not in boot menu when booting laptop

When I select ubuntu, dialog disappears and just reappears as if nothing happened

---

### Post by tea for one on 2022-07-29
Any settings in your UEFI set up which enable/disable internal drives?
Devices > sata 
Devices > pci

Perhaps try resetting UEFI to default?
Open up the laptop and check physical connections to the missing drive?

---

### Post by tea for one on 2022-07-29
> **nizarmb said:**
> 
- I have an external screen connected to my laptop, and I usually hibernate instead of shutting down.
- yesterday, I disconnected the screen then turned my laptop on, and ubuntu not starting up at all. All I get is "boot menu" dialog with "ubuntu" and other options available, clicking any of them including ubuntu does nothing but shows the "boot menu" dialog again.


When you disconnected the screen, was the laptop hibernating or powered off?

---

### Post by nizarmb on 2022-07-29
> **tea for one said:**
> Any settings in your UEFI set up which enable/disable internal drives?
Devices > sata 
Devices > pci

Perhaps try resetting UEFI to default?
Open up the laptop and check physical connections to the missing drive?

No such config in bios. And tried resetting to defaults.

I'm opening up the laptop and checking connectors.

---

### Post by nizarmb on 2022-07-29
> **tea for one said:**
> When you disconnected the screen, was the laptop hibernating or powered off?

It was hibernated yes

Edit:
It was already done hibernating and all leds are off.

---

### Post by nizarmb on 2022-07-29
> **tea for one said:**
> Any settings in your UEFI set up which enable/disable internal drives?
Devices > sata 
Devices > pci

Perhaps try resetting UEFI to default?
Open up the laptop and check physical connections to the missing drive?

I did check physical connectors, and resetting bios settings but didnt work.

If the ssd drive failed, why I'm still seeing ubuntu in boot menu? and I havent faced any single issue with it before, could it just "stop" suddenly like that? because I unplugged a screen when it was off?

---

### Post by tea for one on 2022-07-29
> **nizarmb said:**
> If the ssd drive failed, why I'm still seeing ubuntu in boot menu? and I havent faced any single issue with it before, could it just "stop" suddenly like that? because I unplugged a screen when it was off?

I don't know why the drive is invisible (other than hardware failure).

Is your UEFI firmware up to date?

Sometimes, it may be possible to persuade the UEFI firmware to recognise a missing drive.

Physically remove the 256GB nvme drive.
Boot into a live session via USB a couple of times.
Power off.
Insert the 256GB nvme drive.
Boot into a live session and see if it appears.
It may need a couple of boots for the UEFI firmware to recognise it?

---

### Post by nizarmb on 2022-07-29
> **tea for one said:**
> I don't know why the drive is invisible (other than hardware failure).

Is your UEFI firmware up to date?

Sometimes, it may be possible to persuade the UEFI firmware to recognise a missing drive.

Physically remove the 256GB nvme drive.
Boot into a live session via USB a couple of times.
Power off.
Insert the 256GB nvme drive.
Boot into a live session and see if it appears.
It may need a couple of boots for the UEFI firmware to recognise it?

Thanks for your help and time. I will try what you suggested.

---

### Post by nizarmb on 2022-07-29
> **tea for one said:**
> I don't know why the drive is invisible (other than hardware failure).

Is your UEFI firmware up to date?

Sometimes, it may be possible to persuade the UEFI firmware to recognise a missing drive.

Physically remove the 256GB nvme drive.
Boot into a live session via USB a couple of times.
Power off.
Insert the 256GB nvme drive.
Boot into a live session and see if it appears.
It may need a couple of boots for the UEFI firmware to recognise it?

I have tried your suggestions but nothing changed. If its a hardware failure, how come I still see ubuntu among the boot options?

---

### Post by tea for one on 2022-07-29
> **nizarmb said:**
>  how come I still see ubuntu among the boot options?
Just a guess but probably a Lenovo firmware feature (Line 47 of the boot-repair report mentions Lenovo firmware)
For example, I have a small Lenovo netbook where I completely removed Windows 10 S Mode and installed Xubuntu.
When I use F12 to reach the boot menu, Windows Boot Manager is still there.
If I select it, I arrive at Grub.

It looks like the firmware remembers previous entries.

---

### Post by nizarmb on 2022-07-29
> **tea for one said:**
> Just a guess but probably a Lenovo firmware feature (Line 47 of the boot-repair report mentions Lenovo firmware)
For example, I have a small Lenovo netbook where I completely removed Windows 10 S Mode and installed Xubuntu.
When I use F12 to reach the boot menu, Windows Boot Manager is still there.
If I select it, I arrive at Grub.

It looks like the firmware remembers previous entries.

In my case even selecting windows boot manager does nothing. However, I re-flashed the bios, still not detecting the drive but the boot menu is not showing ubuntu anymore. It seems it just died or its slot connector is corrupted and hopefully I can recover the data at least.

Thanks a lot for your support @tea for one

---

### Post by tea for one on 2022-07-29
Two more shots in the dark:-

(a) Download a Windows 10/11 iso, make a boot disk and see if the Windows installer will find your 256GB nvme.

(b) Visit this site [https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/) to understand the utility.
     You can make a portable USB of rEFInd [https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html) - Option 5

---

### Post by nizarmb on 2022-07-30
> **tea for one said:**
> Two more shots in the dark:-

(a) Download a Windows 10/11 iso, make a boot disk and see if the Windows installer will find your 256GB nvme.

(b) Visit this site [https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/) to understand the utility.
     You can make a portable USB of rEFInd [https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html) - Option 5

Just tried them, both didn't detect the ssd drive :(

---


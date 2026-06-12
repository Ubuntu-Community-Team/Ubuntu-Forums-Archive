---
title: "Short question about dual boot Ubuntu Studio/Vista installation"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by XmaX on 2008-01-24
Hi,

I am just about to start installing Ubuntu Studio 7.10 on my laptop with Vista. I intend to install it on the second partition, for which I will free some space with Vista partition-shrinking tool. I already had ubuntu, but not with Vista and not from text istallation.

The questions I have are:
- I have a weird 1.6 GB EISA Configuration partition. No idea what it does, but would it affect the partition setup during the installation?
- I have 2 GB of RAM, so I don't think I'll ever use swap. I don't want to waste 2 or 4 GB for it, so I'll probably use 700 - 800 MB. Would that have any negative effects? From what I've read, it seems I won't be able to hibernate, right?
- Is it safe to assume, that if the Gutsy LiveCD worked properly, then the Studio also will? I'm asking, because I know there are some issues with my graphics card (Mobility Radeon HD2600), and I would like to try to fix this with graphical interface, I'm not too comfortable with working solely in terminal (and in 7.04, I had to).
- And the most important question - where should I install the GRUB - on MBR, or somewhere else? I tried to find an answer for that, but it seems tham some recommend to do it on MBR, some don't.

---

### Post by wolfen69 on 2008-01-24
1. choose manual partition and just avoid your 1.6gb partition.
2. it wont have any negative effects as far as performance. i dont have a laptop, so i dont know about hibernation.
3. chances are you wont have any problem with studio.
4. just let it install grub automatically.

---

### Post by XmaX on 2008-01-24
What do you mean by installing GRUB automatically? As far as I know, the installer asks:
```
Install the GRUB boot loader to the master boot record?
<Go Back>                                    <Yes>      <No>
```
If I choose no, I have to specify where to install it manually.

---

### Post by travis31 on 2008-01-24
> **XmaX said:**
> What do you mean by installing GRUB automatically? As far as I know, the installer asks:
```
Install the GRUB boot loader to the master boot record?
<Go Back>                                    <Yes>      <No>
```
If I choose no, I have to specify where to install it manually.

I have a dual boot Vista and Ubuntu laptop with GRUB installed in the MBR. I prefer that over having to boot Ubuntu using the Vista Bootloader. With the Vista Bootloader, if you hibernate Vista and later start your laptop, it boots into Vista without showing the OS selection screen, so to get back to Ubuntu I would have to restart Vista.

---

### Post by XmaX on 2008-01-24
That's a good point, actually. However, isn't booting Ubuntu while Windows is hibernated quite problematic? Back when I was using Dapper and Edgy, I couldn't access my NTFS drives if Windows was hibernated. Myabe that's not the case, Ubuntu has now native support of reading/writing NTFS, so who knows.

I also just realized, that there might be another problem with hibernation in my computer. Earlier today, when I was playing with LiveCD and checking out the installer for Studio, I hibernated Windows. However, when I tried to turn it on again, I couldn't enter BIOS, and the computer didn't boot from the CD as it should, it went straight to wake Vista up. Now, how could that affect the bootloader? I am using Toshiba A210-11P, if that makes any difference.

---

### Post by wolfen69 on 2008-01-24
> **XmaX said:**
> What do you mean by installing GRUB automatically? As far as I know, the installer asks:
```
Install the GRUB boot loader to the master boot record?
<Go Back>                                    <Yes>      <No>
```
If I choose no, I have to specify where to install it manually.

you're right. i had a brain freeze and was thinking of the ubuntu live cd. you are ok to install it to the mbr.

---

### Post by travis31 on 2008-01-24
> **XmaX said:**
> That's a good point, actually. However, isn't booting Ubuntu while Windows is hibernated quite problematic? Back when I was using Dapper and Edgy, I couldn't access my NTFS drives if Windows was hibernated. Myabe that's not the case, Ubuntu has now native support of reading/writing NTFS, so who knows.

I also just realized, that there might be another problem with hibernation in my computer. Earlier today, when I was playing with LiveCD and checking out the installer for Studio, I hibernated Windows. However, when I tried to turn it on again, I couldn't enter BIOS, and the computer didn't boot from the CD as it should, it went straight to wake Vista up. Now, how could that affect the bootloader? I am using Toshiba A210-11P, if that makes any difference.

To answer your first question, if you boot Ubuntu with Windows hibernated, Ubuntu will not attempt to mount the Windows partition. You definitely don't want to mess around with Windows when it is hibernated.

The behavior you saw with hibernate in Vista with the live cd is exactly what I was talking about earlier.

---


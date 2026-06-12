---
title: "[SOLVED] Installing Xubuntu 18.10 32-bit alongside Windows 10"
date: 2019-02-19
forum: Installation &amp; Upgrades
---

### Post by biassiw on 2019-02-19
Hello everybody

Today I wanted to install Xubuntu 18.10 32-bit in my Samsung NP-NF310 Netbook. Currently I have Windows 10 32-bit on it.

I have used many versions of Xubuntu, Lubuntu and Linux Mint in this machine. When I need to install any of them, I always shrink my C drive to whatever size I need for my Linux.

In this case I have 39,06 GB of unassigned space, which is much more than enough for my requirements.

My problem starts when I try to install Xubuntu from a flash drive. I created it with Universal USB Installer, I have done many times in the past. The installer detects that I have Windows 10 in my computer. However, it doesn't offer the option to automatically install the system alongside Windows. I always saw the option of install alongside Windows in previous versions that I used of Linux Mint, Xubuntu or Lubuntu.

I understand that it's possible to manually create the necessary partitions and then install. However, I want to know if this feature of installing Linux automatically alongside Windows has been removed?

I also tried with Linux Mint 19.1 to see if the problem was with the Xubuntu ISO. However, the exact same happens. I didn't change any settings in my BIOS since my last installation of Xubuntu 16.04.1, which worked completely fine for me. I tried with 3 different flash drives and in all the available USB ports of my laptop, but still no success. Fast boot of Windows 10 is disabled.

Thanks in advance

---

### Post by yancek on 2019-02-19
Your images do not show.  Installing Alongside should still be an option although I haven't specifically tried Xubuntu lately.  Do you see the various partitions/unallocated space in the installer window?  What you describe is often the result of leaving the default hibernation/fastboot on in windows.  If that's the case turn it off.

---

### Post by biassiw on 2019-02-19
Now that I checked the "something else" menu I saw something weird. Basically the space that I allocated for Linux via the Windows 10 disk manager appears as "unusable" as can be seen on the following screenshot. This never happened with me before. Is it beause I already have 4 partitions in the hard drive? In general I have only 1 for Windows, and the others seem to be for recovery purposes.

[img]https://i.imgur.com/FciDFsb.jpg[/img]

Also, to clarify, the installer recognizes Windows 10, but it offers only to wipe it to install Xubuntu, as can be seen in the following screenshot.

[img]https://i.imgur.com/huRvSAF.jpg[/img]

About the fastboot, yep, I checked it and it's disabled

---

### Post by biassiw on 2019-02-19
I solved the problem. It turns out that recently Windows 10 created a new recovery partition, which made a total of 4 partitions in my hard drive.

Because of this, I tried to remove the older recovery partition, which was obsolete. After this, the option to install Xubuntu alongside Windows 10 reappeared. I think that the issue was that I couldn't have more than 4 partitions in my hard drive.

---

### Post by Impavidus on 2019-02-20
That was indeed the issue. There's no EFI partition, which means that Windows is installed in bios mode on an mbr partitioned hard drive. That's uncommon for Windows 10. On mbr partitioned hard drives, there's a limit of 4 primary partitions.

---


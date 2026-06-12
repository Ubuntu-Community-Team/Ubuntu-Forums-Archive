---
title: "why can't i install on an external HD?"
date: 2024-03-23
forum: Installation &amp; Upgrades
---

### Post by hmiersch on 2024-03-23
hi. i want to install ubuntu on an externsal HD so i can run some tests without screwing up my main partition. the problem is that the installer only gives me one option: the internal HD which is not what i want. i downloaded the .iso file and created a bootable USB stick, in case that makes a difference. so what can i do to get ubuntu 23.10 installed on that external HD?

---

### Post by ubfan1 on 2024-03-23
What kind of external disk -- USB, eSATA, something else? What's on the external disk now, a partition table (what kind gpt, MSDOS), partitions/empty space?  If any partitions, what filesystem is on them, if any? Do you have any UEFI settings (BIOS) which might disable the external disk?

---

### Post by oldfred on 2024-03-23
Also what version/flavor of Ubuntu?
There now are several different installers.
Older Ubuntu used Ubiquity which has a bug on install to any drive other than first internal drive.
Newer Ubuntu uses Subiquity which does not have bug.
But many flavors still use Ubiquity.
Lubuntu uses Calmares installer and Kubuntu will use it with 24.04, but thru 23.10 used Ubiquity. I had to use work around to install Kubuntu to second & external drives.

---

### Post by sudodus on 2024-03-24
The following alternative makes it easy to install Ubuntu to an external drive, but you cannot get an excrypted system that way. And the whole drive will be used (existing file systems on the target drive will be overwritten).

You can use a compressed image file, that is simply extracted and cloned to the external drive. See [this link](https://ubuntuforums.org/showthread.php?t=2474692). Read the whole thread before deciding to use it.

Ubuntu Server will be installed. After installation you can boot into Ubuntu Server and install the desktop environment that you want, for example the meta package  **[FONT=Courier New]ubuntu-desktop[/FONT]** to get the standard Ubuntu Desktop system.

---


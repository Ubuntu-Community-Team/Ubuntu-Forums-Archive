---
title: "Boot-repair USB says I don't have a partition, but I do"
date: 2020-12-11
forum: Installation &amp; Upgrades
---

### Post by aheirich on 2020-12-11
I have a Lenovo Thinkpad that came with Ubuntu 20.04 and also a Windows 10 partition.  It used to boot into Ubuntu.  After setting up Windows it boots only into Windows and no longer goes through the Grub menu.  I have installed Boot-repair USB to a USB drive and can boot my laptop that way.  When I try to run boot repair it tells me that I have to create a fat32 partition > 100 MB with the boot flag at the start of the drive.  Well, such a partition already exists as I can see in gpartd.  I cannot create a new one, gpartd has that menu entry unselectable.  

How can I get back to an Ubuntu boot?  (Did I mention I hate Windows :-( )

Here is the boot info, I had to break it into three files to get through the upload filter, just cat them together

[ATTACH]287529[/ATTACH][ATTACH]287530[/ATTACH][ATTACH]287531[/ATTACH]

---

### Post by GhX6GZMB on 2020-12-11
Ubuntu or Lubuntu? I'm confused.

---

### Post by ajgreeny on 2020-12-11
Can you please post the boot-info results again but this time use [https://paste.ubuntu.com/](https://paste.ubuntu.com/) as the site to copy the text, as the script tells you, not as three separate text file attachments that we have to concatenate.

---

### Post by aheirich on 2020-12-11
solution: I reinstalled Ubuntu from a USB drive.  This overwrote the Windows crap.  Shame on Microsoft for not playing nice with Grub.

---

### Post by CelticWarrior on 2020-12-11
> **aheirich said:**
> solution: I reinstalled Ubuntu from a USB drive.  This overwrote the Windows crap.  Shame on Microsoft for not playing nice with Grub.

If the only thing Windows did was to change the boot order in UEFI - BTW, for your convenience because it takes a lot of reboots for installing those huge feature updates - then there's nothing to be ashamed of.

Users that purposely install dual- or multi-boot systems must know how to manage them and that implies being very familiar with the motherboard's firmware, BIOS or UEFI, differences between then and the respective requirements for installation, and how the boot process works and how to change bootloaders. Users should also be aware that any firmware update tends to reset its settings so users must know how to change them back.

Windows and Microsoft have lots to be criticized about. What you chalked to "Windows not playing nice" is not one of them.

---


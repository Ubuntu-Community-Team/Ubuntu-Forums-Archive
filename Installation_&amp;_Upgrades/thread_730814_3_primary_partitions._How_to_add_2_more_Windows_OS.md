---
title: "3 primary partitions. How to add 2 more Windows OS's?"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by phenest on 2008-03-21
I read somewhere you can only have a maximum of 4 primary partitions on a single hard drive.

My current hard drive partition setup:

1st primary: Linux Swap
2nd primary: Ubuntu root
3rd primary: Ubuntu home

I now want to add Vista and XP to make a triple boot. I have made a 20GB space after the 3rd primary partition to add them. I figured the best way was to add an Extended partition and divide that into 2 equal sized Logical partitions (one for Vista, and one for XP). But XP complains the partition is not an "XP-compatible partition".

Erasing (or backing up) everything on the hard drive to start fresh is not an option.

So what am I doing wrong, and how do I accomplish this?

---

### Post by Pumalite on 2008-03-21
You can't. Start from scratch. Install both Windows first, Create an extended partition and within that Ubuntu will create the logicals it needs.

---

### Post by phenest on 2008-03-21
> **Pumalite said:**
> You can't.

I can't what? Install them afterwards? Install to logical partitions?

> **Pumalite said:**
> Start from scratch. Install both Windows first, Create an extended partition and within that Ubuntu will create the logicals it needs.

I already said this was not an option.

---

### Post by sh4d0w808 on 2008-03-21
Then the other possibility is to install Windows OSes to Virtualbox if there is no special software used, which requires a real Windows XP.

Another possibility is to create a swapfile on your /home filesystem and delete the swap partition. Then one primary flag will be available for Windows XP.

---


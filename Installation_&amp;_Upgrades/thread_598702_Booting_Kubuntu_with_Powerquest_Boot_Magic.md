---
title: "Booting Kubuntu with Powerquest Boot Magic"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by StGeorge on 2007-10-31
My laptop is running XP Pro.
I used Partition Magic 8 to make space for Kubuntu root and Swap.
I formatted the space I made with Partition Magic on the Kubuntu install for the Kubuntu OS.
I did not install Grub as I find it a pain. It chooses the linux distro as default and I cannot find a way to get the windows OS set as default.
Not to keen on loading grub.
I want to use Powerquest Boot Magic as my Boot Loader.
I have pointed Boot Magic to the linux partition containing Kubuntu.
It shows in the Boot Menu but when I select it just states Loading and goes no further.
Kubuntu is on its drive as I have explored the drive with Partition Magic.
Any ideas how to get Boot Magic to see Kubuntu.
Thanks in advance.

---

### Post by earth on 2007-10-31
I've tried the same thing with Boot Magic, several times, & never succeeded in booting a Linux OS from it!  The GAG bootloader works well if the Linux installation allows its own bootloader to be installed on the root partition; unfortunately, so far, I haven't figured out a way to do that with Ubuntu.  PCLOS installation gives you that option, and I've successfully booted Windows XP & PCLOS with the GAG bootloader, a free internet download that always detects each OS & bootloader on their own parititions.

---


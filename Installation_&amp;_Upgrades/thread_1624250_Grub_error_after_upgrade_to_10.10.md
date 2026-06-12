---
title: "Grub error after upgrade to 10.10"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by Skynyrd9 on 2010-11-17
So yesterday i upgraded Ubuntu 10.04 to 10.10. During installation i also upgraded grub to version 2. It said that there were two options that i could choose to boot and i choose both. Installation finished with out a hitch. When i attempted restart my laptop i got this message:

error: no such device: 12631218-8ac6-4505-b4cb-a66a1de1814f
grub rescue>

I tried the command help and received a message saying that the help command was not recognized. So i then gave Google a bit of a work out and have tried reinstalling grub and manually coping the grub files all to no avail.  The problem i believe stems from how i have Ubuntu installed. I have Ubuntu installed like an application on windows 7 on a separate partition on my hard drive. Looking back on it i'm not to sure why i choose that route, but that is how it is installed.  So if anyone has suggestions on how to fix this problem, it would be greatly appreciated.

---

### Post by drs305 on 2010-11-17
Skynyrd9

Welcome to Ubuntu and the Ubuntu forums!

I wrote a guide on booting from the grub rescue prompt. You can read through the early info but there is a section specifically for Wubi installations, which is what you have.

If you aren't sure about why you installed within Windows vs a normal install, I'd recommend a quick attempt to boot wubi. If it doesn't work, since you just installed it, I'd suggest just reinstalling in a normal partition.

In any case, here is the link for trying to get wubi to boot:
[Grub Rescue Prompt Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")

---

### Post by bcbc on 2010-11-17
If you see the grub rescue prompt when your computer boots (i.e. you can't boot windows at all), then you have installed grub to the MBR of the drive. Just reinstall the windows bootloader. (Insert a windows 7 repair CD and run 'bootrec.exe /fixmbr')

---

### Post by Skynyrd9 on 2010-11-17
bcbc thanks that worked perfectly

---


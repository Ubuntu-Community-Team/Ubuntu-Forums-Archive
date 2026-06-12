---
title: "[newbie question] How to install full ubuntu to 8gb flash drive?"
date: 2012-09-26
forum: Installation &amp; Upgrades
---

### Post by gunnerbob101 on 2012-09-26
I wanted to get ubuntu full install on my 8gb, USB3 flashdrive.
I dont want livecd, as it resets when you shut down.
I also tried pendrivelinuxs installer, which enable persistency,but i want the full install(to get logins, updates, "full ubuntu experience")
I am currently on windows 7, and sadly i dont know much about linux nor installing full version to USB.
Can someone help me with this?

---

### Post by oldfred on 2012-09-26
Welcome to the forums.

I have a full install in a 8GB partition in my 16GB flash drive. But do not have USB3. Should be faster, but some computers do not support USB3 well for booting. 

It really is just like any install to a second drive, but that requires you to manually partition using Something Else. Only the manual partition screen offers the choice on where to install the grub2 boot loader and you have to have the grub2 boot loader in the MBR of the flash drive.

Are you using LiveCD or another USB flash drive as the installer? You need to keep track of which physical drive is which. Some systems BIOS promote a flash to to sda or first drive where most make flash sdb or even sdf.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

It does not have to be encrypted BIOS based system, but to use encryption you need the alternative installer:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---


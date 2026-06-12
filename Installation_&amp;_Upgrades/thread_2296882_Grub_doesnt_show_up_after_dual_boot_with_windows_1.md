---
title: "Grub doesnt show up after dual boot with windows 10"
date: 2015-09-29
forum: Installation &amp; Upgrades
---

### Post by martin171 on 2015-09-29
Hello i have a big problem i have windows 10 installed on my Lenovo miix 3 8 and i want to do a dual boot then i create a partition for ubuntu and run ubuntu from USB then i select install ubuntu alongside windows boot manager and after the installation i reboot the tablet PC and its show Lenovo and after Lenovo black screen and then the windows dot circle loading screen and then its load a windows no grub then i shut down tablet PC and i boot USB ubuntu and run boot-repair and after that operation i reboot the tablet PC and the same only windows boot up can you help me with this problem please ? i really want ro dual boot the windows 10 and ubuntu 14.04.3 LTS:D PS: sorry for my english

---

### Post by yancek on 2015-09-29
Boot repair has an option to "Create BootInfo Summary" which will output some detailed information and someone will likely be able to help.  You didn't post that, or if you didn't select that option, repeat the boot repair selecting that option and not trying to do any repairs.  Post the output here.

If you have windows 10, it is probably installed using UEFI, if so you need Ubuntu in UEFI mode also.

---

### Post by martin171 on 2015-10-01
[http://paste.ubuntu.com/12632288/](http://paste.ubuntu.com/12632288/) here is boot log

---

### Post by oldfred on 2015-10-01
Is this system using a flash drive as main drive? 
/dev/mmcblk0

But with new Windows you must make sure you have turned off fast startup which is really always on hibernation.
> The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/mmcblk0p4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
Fast Startup off/hibernation[URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"]
http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html[/URL]
 [http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

---

### Post by martin171 on 2015-10-02
yes the main drive is flash disk ok i will try to disable the fast startup and i will send here the resoult

---

### Post by martin171 on 2015-10-02
still the same problem after disabling fast boot

---

### Post by oldfred on 2015-10-02
Fast boot is in UEFI, fast start up is in Windows. Best if both are off.

---

### Post by martin171 on 2015-10-02
both is disabled and nothing ok i will try virtual machine and kali kinux maybe when i have an notebook i will try ubuntu dual boot

---


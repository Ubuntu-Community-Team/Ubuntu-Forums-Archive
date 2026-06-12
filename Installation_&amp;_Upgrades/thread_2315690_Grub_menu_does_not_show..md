---
title: "Grub menu does not show."
date: 2016-03-01
forum: Installation &amp; Upgrades
---

### Post by pxie on 2016-03-01
Hello. I have installed windows 8.1 alongside with ubuntu 14.04. I had to reinstall the ubuntu like i did many times but this time when i installed ubuntu and started notebook it does not show Grub menu it boots directly to windows. I have to press F12 or special button on my notebook go to boot menu choose ubuntu to show the grub menu. Could anyone tell me how to fix that please? Also i feel like my notebook is really loud it is not like it used to be.

notebook specs:
lenovo ideaPad y50-70
nvidia gtx 980 4gb
intell i7 4720 HQ haswell
Windows 8.1 + Ubuntu 14.04

I somewhere read that i should add "#" before GRUB_HIDDEN_TIMEOUT=0, but it was set by default like that.
#GRUB_HIDDEN_TIMEOUT=0

---

### Post by oldfred on 2016-03-01
Did you install both Windows & Ubuntu in UEFI boot mode?

May be best to see details, be sure to boot installer in UEFI mode, if installs are UEFI.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by pxie on 2016-03-01
Hello here is the link to pastebin :

[http://paste.ubuntu.com/15262446/](http://paste.ubuntu.com/15262446/)

---

### Post by oldfred on 2016-03-01
You are showing two ESP - efi system partitions, both sda2 & sda3.
I believe Lenovos use a second FAT32 partition for its recovery partition. It does not have boot flag, so not an ESP, even though it has .efi boot files.

You do show grub installed to both ESP and to partition boot sector of sda3. That may cause issues with that partition.

Remove boot flag from sda3, and boot into Windows. Then turn off fast start up or its always on hibernation.
       Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

---

### Post by pxie on 2016-03-02
Hi, I removed boot flag from sda3 partition and turned off fast start up but it did not help and still  boots directly to windows.

---

### Post by oldfred on 2016-03-02
If you use one time boot key often f10 or f12 does it show ubuntu as boot option?

Some copy /efi/Ubuntu to /efi/Boot and rename shimx64.efi to bootx64.efi and boot hard drive entry. Many vendors now are violating UEFI spec and using description as part of boot. And only valid description is "Windows". But all systems have fallback or hard drive boot entry if set up for that.

 Lenovo rename files
[http://ubuntuforums.org/showthread.php?t=2302170](http://ubuntuforums.org/showthread.php?t=2302170)
Lenovo Laptops there is NOVO button on left side 

 Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

### Post by pxie on 2016-03-02
Yes when i press F12 i can choose ubuntu as boot option adn then it opens grub menu and i can start ubuntu however since i run boot repair from usb there are now 2 ubuntu to choose and when i choose the second one it shows unable to boot - small bios window.

---

### Post by oldfred on 2016-03-02
Typically you get two Ubuntu entries. One is shim and one is grub. Where Shim version of grub is for secure boot. But if you have secure boot on, you cannot boot Windows from grub menu only from UEFI menu.

To see differences in entries.
sudo efibootmgr -v

---


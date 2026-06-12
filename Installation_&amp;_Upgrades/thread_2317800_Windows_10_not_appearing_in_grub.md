---
title: "Windows 10 not appearing in grub"
date: 2016-03-19
forum: Installation &amp; Upgrades
---

### Post by visitnag on 2016-03-19
Hi,

I have upgraded windows 10 32bit  to windows 10 64bit later UBUNTU 15.10 32bit to 64bit (in non uefi mode i dont remember how I have upgraded windows 10 , i mean whether uefi or not).

After loading ubuntu no os was seen in grub (it started in grub rescue mode)
later I logged in to system with live ubuntu(usb stick) and installed boot-repair and executed it.

After rebooting I could see only ubuntu 15.10 in grub.

How to get the Windows10 in my grub menu??

Thank you.

---

### Post by oldfred on 2016-03-20
Unless both are BIOS or both UEFI, you cannot boot from grub.

And whether UEFI or BIOS Windows 10 fast start up or always on hibernation must be off for grub to be able to see it and to boot it.
       Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

After making sure fast start up is off, in Ubuntu run this:
sudo update-grub

       
 If that does not work, it may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---


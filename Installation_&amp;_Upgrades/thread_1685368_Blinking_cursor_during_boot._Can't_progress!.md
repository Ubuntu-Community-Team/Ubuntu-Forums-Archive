---
title: "Blinking cursor during boot. Can't progress!"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by AsherSevyn on 2011-02-10
I am attempting to install Ubuntu 64Bit Server 10.04 on a new server. 

Server Specs:

Xeon E5620 
12GB RAM
2X 160GB 7200 RPM in RAID1 (Onboard Software RAID) 
Super Micro X8DTI-8

I am doing a typical install with no special functions on a RAID1 onboard Intel array. I know the array works because I tested it by installing Windows Server 2003 which works fine. The RAID also shows as healthy in the BIOS.  

This problem is very difficult to remedy because everything seems to install fine with Ubuntu but when you reboot after the install you get a blinking cursor _ and nothing else. 

It appears that something happened when loading the OS but it's impossible to get past the blinking cursor because you can't type anything or escape out of it. The only thing that it will register is Ctrl+Alt+Del which will restart the server. 

The funny thing is it does not display the typical Sigkill and show processes shutting down. The screen goes black and it restarts only to return to the blinking cursor. I am on my 6th attempt at an install with ubuntu and I am seriously considering switching over to windows unless you of you guys can help me. 

I am almost certain this is a RAID issue because I can load the Ubuntu on 1 drive without any issues but I always get the blinking cursor in the RAID. PLEASE HELP!

---

### Post by dabl on 2011-02-10
It sounds more like a video driver issue than anything to do with RAID, but I'm not sure.

To learn whether Linux is actually running, use the "magic" SysRq keys.  Press and hold Alt and SysRq (aka "Print Screen"), and while holding them down, press in sequence R S E I U B.  If it shuts down and reboots, then you'll know that it is actually booting and running Linux, and the problem is all about a video driver.  If nothing happens, then that's our clue that there's a booting problem with your RAID setup.

---


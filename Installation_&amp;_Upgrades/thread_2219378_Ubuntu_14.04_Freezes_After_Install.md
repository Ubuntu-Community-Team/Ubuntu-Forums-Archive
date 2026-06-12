---
title: "Ubuntu 14.04 Freezes After Install"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by Yogi2 on 2014-04-23
I have two computers with Ubuntu 14.04 installed.  One is an hp Pavililon dv5 laptop where all is well. 
The other computer multi-boots to one of three hard drives.  All was well with Ubuntu 12.04 installed.

I reformatted the desktop drive with Ubuntu 12.04 and installed 14.04 in it's place being sure GRUB was installed on the same drive and allowing the Windows bootloader to run from its own drive. BIOS determines which has boot priority. All went well installing from the same DVD that I used to install 14.04 on the laptop. When the desktop install completed, I rebooted, logged in, and after about 10 seconds the system froze.  It did not respond to mouse or keyboard after that.  The only way to recover was a hard reboot.  Rebooting does not fix the problem. I then tried running off the live CD with the same results.  

I had similar problems on this desktop hardware when I installed Ubuntu 12.04, and eventually discovered that the nVidia card drivers had to be installed using a shell script provided by nVidia.  This was possible only by adding the *nomodeset *parameter at boot time and downloading the drivers with a very low resolution screen.  The system would not freeze under these boot conditions and I was able to install the driver successfully.  No problems after all that.

I tried to do the same with Ubuntu 14.04 but the *nomodeset *parameter is not available.  If it's there, I can't find it.  While I can start and login, Ubuntu does not stay live long enough for me to download any drivers, much less install them.  I don't know if the upgraded video drivers will fix the freeze problem, although I suspect it will, and I have no way to install them to find out.  

Can anyone suggest a way around this problem?

My desktop configuration is[INDENT]Processor: Intel i5-3750K CPU @ 3.4GHz
MSI mobo: B75 MA-E33 (MS7808)
RAM: 16GB
Video Adapter: nVidia GeForce GTX 580
Monitor: NEC Multisync LCD2070NX
Mouse and Keyboard are hard wired
[/INDENT]

---

### Post by sudodus on 2014-04-24
> **Yogi2 said:**
> ...

I tried to do the same with Ubuntu 14.04 but the *nomodeset *parameter is not available.  If it's there, I can't find it ...
Can anyone suggest a way around this problem?

My desktop configuration is[INDENT]Processor: Intel i5-3750K CPU @ 3.4GHz
MSI mobo: B75 MA-E33 (MS7808)
RAM: 16GB
Video Adapter: nVidia GeForce GTX 580
Monitor: NEC Multisync LCD2070NX
Mouse and Keyboard are hard wired
[/INDENT]

I am rather sure that you can add nomodeset 'manually'.

1. In the installer

Click on F6 and then on ESC. You get a line, with some boot options at the end

```
... quiet splash --
```

If you add nomodeset before -- (and a space as separator) it will be used during the live session. If you add nomodeset after -- (and a space as separator) it will be transferred to the target system.

```
... quiet splash -- nomodeset
```

2. In the installed system you can add it directly to grub.cfg. Mount the installed root file system to /mnt.

```
sudo nano /mnt/boot/grub/grub.cfg
```

and add nomodeset after quiet splash (in the 'linux line' which is the first choice). [COLOR=#696969]There is no '--' in grub.cfg.[/COLOR]

---

### Post by marginal39 on 2014-04-24
Same thing here.

After the upgrade to 14.04 my PC started freezing as it used to happen in the good old times with Win '95 :-).
Any suggestions?

I have:
Memory: 5.8 GiB
Processor: Intel® Core&#8482; i7-2630QM CPU @ 2.00GHz × 8 
Graphics: GeForce GT 525M/PCIe/SSE2
OS type: 32-bit
Disk: 247.8 GB

Regards.

---

### Post by Yogi2 on 2014-04-25
Many thanks to *sudodus* for the suggestions on how to manually  add the nomodeset parameter at boot time.  All I had to do was press 'e'  to edit the boot commands, which I missed the first time around.  

**UPDATE:**  I was able to install the current nVidia driver from the shell.  It's  not easy to do for a novice such as myself, but I can list what I did if  anyone is interested.  Unfortunately, only the symptoms have changed;  the original problem still exists.  The cursor disappears after about  ten seconds and I am left with only a splash screen.  No Unity desktop.   

Any suggestions on how to solve this problem would be greatly appreciated.

---


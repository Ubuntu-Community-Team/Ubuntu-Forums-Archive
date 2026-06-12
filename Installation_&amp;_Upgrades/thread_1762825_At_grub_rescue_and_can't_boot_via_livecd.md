---
title: "At grub rescue and can't boot via livecd"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by jmeasns on 2011-05-19
**Short Story:** 
I'm stuck at "grub rescue>" and can't boot via livecd.
 
**Long story:**
I have a new Toshiba Satellite. With Windows 7 already installed, I shrunk its partition and began an ubuntu 11.04 (64bit) install (as a dual boot) from the LiveCD. It got through most of the install, but the computer hibernated before completing. I rebooted and ran GParted, wiping the ext4 partition, and reran the ubuntu install. It froze most of the way through. I forced a reboot, and now the LiveCD freezes on the Ubuntu logo (with the 4 dots progress bar). Hitting alt+f4 during boot I get this after a minute or two:
```
 
[  122.472619] SP5100 TC0 timer: mnio address 0xb8fe00 already in use

```
 
Taking the LiveCD out and booting, I get a "grub rescue>" prompt:
```
 
Booting from local disk...
error: unknown filesystem.
grub rescue> help
Unknown command `help'
grub rescue> ls
(hd0) (hd0,msdos7) (hd0,msdos6) (hd0,msdos5) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)
grub rescue> ls (hd0)
error: unknown filesystem.
grub rescue> ls (hd0,msdos7)
error: unknown filesystem.
grub rescue> ls (hd1)
error: hd1 cannot get C/H/S values.
grub rescue> ls (test)
error: no such disk.

```
 
I've tried as many of the suggestions in these forums I can, but my options are rather limited. I checked the dvd for errors, which ran successfully and found none. I can probably boot into a knoppix cd and run commands if necessary, but I'd like to know if anyone has any suggestions for how to proceed before I start rooting around there. 
 
Thanks for the help!

---

### Post by Quackers on 2011-05-19
You could try booting with the nomodeset boot option.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by jmeasns on 2011-05-19
Thanks for the suggestion, Quackers. However, I tried that and got the same behavior:

```

                         Ubuntu 11.04

[COLOR=Red]. . . [/COLOR]. * Stopping System V runlevel compatibility[COLOR=Red]ss 0xb8fe00 already in use[/COLOR]                   [ OK ]

```

The text in red is actually in yellow (and the presentation here is identical to my screen, "overlapping" text and all). The system freezes at this point. Is there anything else I can try? 

Thanks again,
   -Jess

---

### Post by jmeasns on 2011-05-20
I'm getting similar behavior from other distros, including DSL. That has me worried, since my normal approach of chrooting won't work if I can't boot at all. I was able to get in briefly by setting acpi=off, but the system froze after a minute or two, and after two boots, I can't get in that way anymore either. 

Any help or suggestions would be terrific.

Thanks,
   -Jess

---

### Post by jmeasns on 2011-05-20
Quick *bump*. 

I'm able to boot into an old version of GParted, which allowed me to wipe the unfinished linux partition, and to open a terminal to examine the windows partitions. I'm not familiar with locating the MBR and modifying it by hand, particularly on a windows partition. Can anyone point me to resources on how to do this? Also, anyone with any clues as to why I now can't boot into a linux livecd would be appreciated.

Thanks,
   -Jess

---

### Post by linuxinstalledfromhdd on 2011-05-20
Check out and see if this helps at all:

[http://cinderbox.net/2011/03/10/how-to-recover-grub2-after-windows-installation/](http://cinderbox.net/2011/03/10/how-to-recover-grub2-after-windows-installation/)

---

### Post by Rubi1200 on 2011-05-21
> **jmeasns said:**
> Quick *bump*. 

I'm able to boot into an old version of GParted, which allowed me to wipe the unfinished linux partition, and to open a terminal to examine the windows partitions. I'm not familiar with locating the MBR and modifying it by hand, particularly on a windows partition. Can anyone point me to resources on how to do this? Also, anyone with any clues as to why I now can't boot into a linux livecd would be appreciated.

Thanks,
   -Jess
I assume this is a LiveCD version of GParted?

If yes, run the boot info script please:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Another question; have you tried booting with Slax?

---

### Post by jmeasns on 2011-05-22
Thank you both for the responses. 

*@linuxinstalledfromhdd* That was helpful to read through, but unfortunately doesn't resolve this issue, since I can't get into the LiveCD. Thank you, though.

*@Rubi1200* I'm trying to get you that bootinfo output, but Grub doesn't have some required libraries (including gawk) and I can't boot into the ubuntu LiveCD. I'm going to get a more recent version of GParted and see if I can run the script from there. I'll also be trying some other distros' lievcds, but I doubt they'll work if DSL doesn't. 

FYI: I'm also planning to run a windows recovery utility to fix the MBR to point back to Win7, which will hopefully put me back at square 1, and then start over again. I don't know how effective this will be. I'm still confused about what changed to prevent booting from the LiveCD, and I don't know how to fix that. :/

Thanks guys. I'll post back with the GParted boot info if I can get that.
    -Jess

---

### Post by Hedgehog1 on 2011-05-22
Once you do the FIXMBR and are booting into windows again, perhaps you can make a LiveUSB to work from using the ISO and **unetbootin** [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/") to convert the ISO into a LiveUSB, and then run the boot info script using that.

***The Hedge***

:KS

---

### Post by englishforyou on 2011-07-21
Hello jmeasns, I think I had exactly your problem.  Here is my very simple solution.  1. Use another computer, then use unetbootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)) to make a bootable USB drive containing the iso file of Ubintu 11.04 or whatever you had on the liveCD that wasn't working.  2. Insert the USB drive into the one you want to repair.  3. Boot and go into the setup (F2 on my machine) to change the boot order to have the USB SD card first. Save changes and reboot.  4. The "LiveCD" function, where you can try Ubuntu or install it, should now work (though not via CD but USB).  5. Reinstall Ubuntu.  6. On next boot, you should be able to access all systems (ubuntu, windows, ubuntu safemode etc.) as before.   This worked perfectly for me.  For some reason in the grub rescue mode, the machine would not open via liveCD from the CD drive.  This problem was bypassed using the USB drive instead.  Hope this works,  englishforyou

---


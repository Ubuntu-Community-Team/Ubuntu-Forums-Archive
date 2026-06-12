---
title: "Windows 10 and Ubuntu 14.04.3 LTS on Lenovo IdeaCentre B540 -- how to dual boot?"
date: 2015-08-14
forum: Installation &amp; Upgrades
---

### Post by jeremy53 on 2015-08-14
I have been running Windows 10 on my Lenovo IdeaCentre B540 and did a USB install of Ubuntu 14.04.3 LTE. I partitioned 250GB of my 1TB hard drive for Ubuntu in the process. Everything seemed to go smoothly, but, on the restart, it booted back into the USB install (because it was still plugged in). Since removing the drive and restarting, my computer only boots into Windows 10, no options. I cannot get into any sort of BIOS using any of the F1-12 keys or holding down Shift. I can plug the USB stick back in and get it to boot back into the install, which also allows me to hit Esc and get to a Grub command line. I am guessing Grub needs to be installed on my master boot sector so that I am presented with a boot option of Windows or Ubuntu...? Is that not a standard part of the Ubuntu installation process? In the past, I've had no problems getting dual boot setups with Ubuntu and previous iterations of Windows (never had to do anything additional with the MBS or Grub); however, it has been several years since I've attempted this.

Would appreciate any help on how I can go about fixing the situation (i.e., having the computer ask which OS to boot into upon restart). I was hoping the install process would be as smooth as it's been in the past--and maybe it will after clearing what I hope is just a small Windows 10 (and/or Lenovo?) hurdle. I've done some searching for potential solutions (not to say it was exhaustive) but really turned up nothing for my situation (installing dual-boot from Windows 10, especially given my computer setup). Should I assume a situation with Windows 8 is comparable? I've read multiple threads that suggest different setups behave different ways, so I've been less inclined to follow some of the rather involved Windows 8 potential solutions.

I wouldn't say I'm very Linux/Ubuntu savvy, but I'm trying to learn, so I appreciate your patience and don't mind if you assume my baseline of knowledge is next to nothing!

---

### Post by JonPaul on 2015-08-14
You might find this helpful
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
i just did an ubuntu 14.04.3 LTS on my Acer E1-571 without any problem although I was using legacy bios...

---

### Post by jeremy53 on 2015-08-14
Thanks! I will look at this more closely. They do mention some differences with a Lenovo. I guess I should try installing Ubuntu 15.

---

### Post by chsbrg on 2015-08-14
Hi jeremy53,

maybe [http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594) helps. oldfred posted links to all the issues I was confronted with when trying to dual boot Windows 8.1 and various Linux distros on my Acer Aspire netbook. Maybe you'll have to fiddle around a little with the BIOS / UEFI settings as I had.

Good luck!

---

### Post by jeremy53 on 2015-08-14
Thanks! I can't even get into the BIOS/UEFI settings at this time -- many of the posts I find say it's located in some Advanced Settings within Windows (starting at 8.0), but it doesn't appear on mine. Surely I can't be the first to attempt this with Windows 10 (and a Lenovo)!

---

### Post by chsbrg on 2015-08-14
If you aren't able to access the BIOS/UEFI settings on boot you should be via a detour that should be viable in W10 too: boot into Windows and then press the *Power* button at the Windows login screen or in the *Settings* charm. Then, press and **hold** the *SHIFT* key on your keyboard and click *Restart*. I haven't upgraded to Windows 10 myself but with Windows 8.1 you get into a screen with various options - one of them troubleshooting. There you should find a tile/submenu that leads to UEFI/firmware settings (cannot recall the correct name right now).

---

### Post by oldfred on 2015-08-16
Some other Lenovo:
 T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)

But may be best to see details of your install. What video chip does your system have?
      
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---


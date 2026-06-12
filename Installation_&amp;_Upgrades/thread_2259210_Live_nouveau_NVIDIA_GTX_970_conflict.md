---
title: "Live nouveau NVIDIA GTX 970 conflict"
date: 2015-01-02
forum: Installation &amp; Upgrades
---

### Post by krahvaal on 2015-01-02
I been trying for several days to get the 14.04 live media to load and install.
Nothing I've tried avoids blackscreen or freeze (panic?).
Replacing "quite splash" with various commands has allowed me to get some idea of what's going on.

I tried nomodeset or modeset=0 or nouveau.modeset=0 etc with/without combinations of vga=771 or video=1280x1024x24 or xforcevesa.
A number of those get a message something like "..fall back graphics...[fail]" (sorry but this flashes past to fast for me to be accurate).
A number fail on the line "fb: conflicting fb hw usage nouveaufb vs VESA VGA - removing generic driver." and/or go to blackscreen.

Anything I have found on "nouveau 970 blackscreen" is to do with upgrades/updates that have seem to a head start with at least something on screen.
If I understand, I won't be able to load into live DE, let alone installed, until I find a command that will completely stop the kernel handing over to nouveau.
Does such a thing exist for 14.04 and/or 14.10 live/install?


NOTE: I have already established that this has nothing to do with UEFI, it is a dual board that has installed other linux distos either way.
I have already established that the NVIDIA proprietary driver works quite well on another Debian based distro however it's not what I want.

This is what I know about the hardware...
Gigabyte Z97X-SLI...
...Intel GbE LAN with CFOS internet accelerator software
...Realtek ALC1150 115dB SNR HD Audio with built-in rear audio amplifier
...GIGABYTE UEFI DualBIOS
Intel(R) Core(TM) i7-4790S CPU @ 3.20GHz (8 CPUs), ~3.2GHz
16384MB RAM
NVIDIA GeForce GTX 970 4096 MB GDDDR5

Regards,
Greg

---

### Post by efflandt on 2015-01-02
I don't know if there is an X-less install (other than maybe a server version?). I have a GTX 750 Ti which also has the Maxwell chip. Video in the 64-bit 14.04.1 Live install CD worked fine for me. However, once installed I could not get into the installation at all. It did not automatically install nvidia drivers like 12.04 did and I could not even log into any of the tty's (Ctrl+Alt+F1, F2, etc.). When I tried to log into tty's they would flash motd for an instant and go back to login prompt. I knew I had proper login because incorrect login would error about invalid login. And thought I could not login to recovery either because when I tried to enable networking from the menu, it did not recognize a couple of PCI devices and hung.

So I reinstalled using **nomodeset** boot parameter for live/install, going directly to install instead of live. Then when I booted installed system I got as far as gui login screen, but it would do nothing after logging in. So I booted recovery and discovered I had to wait longer after enabling network with unrecognized PCI hardware until it went back to menu to get into root shell. Installed nvidia-current, rebooted normally, and either at that point or when I tried to login, PC started beeping continuously. From examining the logs from another drive apparently the ancient nvidia-current 304 version does not recognize nvidia cards with Maxwell chip. So from recovery root shell with networking I purged nvidia-current and installed nvidia-331 (or maybe nvidia-331-updates transitional package) and that worked fine.

However, I knew that even the nvidia 344 driver driver in Win7 did not fully recognize my card (could not optimize games in Nvidia Experience until updated to 347). So I edited grub line during boot to **text** in place of **quiet splash vt_handoff***, added xorg-edgers ppa, updated apt-get, then figured out how to use aptitude to purge everything related to nvidia-331 and nvidia-settings and install nvidia-346 and its nvidia-settings. Note that unlike past nvidia drivers **sudo nvidia-xconfig --cool-bits=8** allows you to overclock your video card using Nvidia X Server Settings, or 12 also provides fan control.

So this is what I currently have installed for my GTX 750 Ti with Maxwell chip that uses half the power of my previous GTX 550 Ti:
```
efflandt@XPS-8100-1404:~$ dpkg-query -l nvidia* | grep ii
ii  nvidia-346                                            346.22-0ubuntu1~xedgers14.04.1                         amd64        NVIDIA binary driver - version 346.22
ii  nvidia-346-uvm                                        346.22-0ubuntu1~xedgers14.04.1                         amd64        NVIDIA Unified Memory kernel module
ii  nvidia-opencl-icd-346                                 346.22-0ubuntu1~xedgers14.04.1                         amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                                       346.22-0ubuntu1~xedgers14.04.1                         amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-settings-updates                               346.22-0ubuntu1~xedgers14.04.1                         amd64        Transitional package for nvidia-settings
```

PS: Newest BIOS for my PC from 2010 (Dell XPS 8100) was from 2010, so it does not have UEFI. But my MSI TwinFrozr Gaming GTX 750 Ti has a switch for UEFI/BIOS hybrid (default) set to the other position for Legacy BIOS. I have not delt with UEFI yet (my laptop came w/Win7 and msdos partitions), so not sure if you need to do something else with live/install for UEFI.

---

### Post by MAFoElffen on 2015-01-02
If you need more instructions-- Look at my sticky (link in my signature line), 2d post... follow link to temporarily edit boot menu... use "nomodeset" as a temporary kernel boot option. Continue to boot, then go to System settings > Additional drivers... to load the recommended nVidia drivers.

You could use the 2 other links from post #2, or the instructions on nVidia from the last part of post #1 to install your drivers.

---

### Post by krahvaal on 2015-01-03
Thank you efflandt and MAFoElffen.

"nomodeset xorg-edgers ppa" loaded into live so I could install 14.04.
That and editing gfxmode were then required for booting up.
Having run Software Update I installed NVIDIA Current for the NVIDIA-Linux-x86_64-343.36.run dependancies.
"service stop lightdm" hung so I rebooted only to find no desktop panels or response to Ctrl Alt t :shock:
Recovery boot with drop to root and NVIDIA-Linux-x86_64-343.36.run threw "can't write file to /tmp"
Chmod messaged "chmod read-only /tmp"....:redface:
Recovery boot using "rw" with drop to root, NVIDIA installation went fine, reboot with default boot 1920x1080.

I can now reconnect my other drives and update grub for multi-boot.

Thanks for the heads up on overclocking, I did not know.

Regards,
Greg

---

### Post by MAFoElffen on 2015-01-03
Since everything is working for you now, pleas come back to this thread and use the thread tools (link on upper left of this page) to mark this thread as Solved.

---


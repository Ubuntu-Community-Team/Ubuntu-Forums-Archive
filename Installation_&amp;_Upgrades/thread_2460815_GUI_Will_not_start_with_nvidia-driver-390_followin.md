---
title: "GUI Will not start with nvidia-driver-390 following 20.04 upgrade"
date: 2021-04-19
forum: Installation &amp; Upgrades
---

### Post by PaulRSte on 2021-04-19
Error message: (EE) Screen(s) found, but none have a usable configuration

NB This was upgrading from 16.04 via 18.04 which is where the issue started. Upgraded from there to 20.04 hoping for a shortcut fix but no.

Can log in via tty2. System seems ok apart from  no GUI. Have tried nvidia-340 but similar results. The only way I have been able to get the GUI to load is to run "sudo apt purge nvidia*" and then reboot. System then loads using "nouveau" driver. I have installed the driver using the "additional drivers" and "apt-get", same result. Latest attempt was to install the driver and then run "sudo nvidia-xconfig" to create a new xorg.conf file but this didn't help either.  
Graphic card details as follows:_
```
paul@PVR-1:~$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0 ==
modalias : pci:v000010DEd00000DE4sv00001043sd000083D4bc03sc00i00
vendor   : NVIDIA Corporation
model    : GF108 [GeForce GT 520]
driver   : nvidia-340 - distro non-free
driver   : nvidia-driver-390 - distro non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin
From "journalctl":-

Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) Module glx: vendor="NVIDIA Corporation"
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]:         compiled for 4.0.2, module version = 1.0.0
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]:         Module class: X.Org Server Extension
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) NVIDIA GLX Module  390.141  Mon Dec 28 16:17:40 UTC 2020
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) LoadModule: "nvidia"
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) Loading /usr/lib/x86_64-linux-gnu/nvidia/xorg/nvidia_drv.so
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) Module nvidia: vendor="NVIDIA Corporation"
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]:         compiled for 4.0.2, module version = 1.0.0
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]:         Module class: X.Org Video Driver
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) NVIDIA dlloader X Driver  390.141  Mon Dec 28 16:20:32 UTC 2020
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) systemd-logind: releasing fd for 226:0
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) Loading sub module "fb"
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) LoadModule: "fb"
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) Loading /usr/lib/xorg/modules/libfb.so
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) Module fb: vendor="X.Org Foundation"
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]:         compiled for 1.20.9, module version = 1.0.0
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]:         ABI class: X.Org ANSI C Emulation, version 0.4
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) Loading sub module "wfb"
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) LoadModule: "wfb"
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) Loading /usr/lib/xorg/modules/libwfb.so
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) Module wfb: vendor="X.Org Foundation"
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]:         compiled for 1.20.9, module version = 1.0.0
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]:         ABI class: X.Org ANSI C Emulation, version 0.4
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) Loading sub module "ramdac"
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) LoadModule: "ramdac"
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) Module "ramdac" already built-in
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (==) NVIDIA(0): RGB weight 888
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (==) NVIDIA(0): Default visual is TrueColor
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) Applying OutputClass "nvidia" options to /dev/dri/card0
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration"
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (**) NVIDIA(0): Enabling 2D acceleration
Apr 19 11:18:47 PVR-1 systemd[1]: Starting NVIDIA Persistence Daemon...
Apr 19 11:18:47 PVR-1 nvidia-persistenced[1535]: Verbose syslog connection opened
Apr 19 11:18:47 PVR-1 systemd[1]: Started NVIDIA Persistence Daemon.
Apr 19 11:18:47 PVR-1 nvidia-persistenced[1535]: Now running with user ID 124 and group ID 132
Apr 19 11:18:47 PVR-1 nvidia-persistenced[1535]: Started (1535)
Apr 19 11:18:47 PVR-1 nvidia-persistenced[1535]: Received signal 15
Apr 19 11:18:47 PVR-1 systemd[1]: Stopping NVIDIA Persistence Daemon...
Apr 19 11:18:47 PVR-1 nvidia-persistenced[1535]: PID file unlocked.
Apr 19 11:18:47 PVR-1 nvidia-persistenced[1535]: PID file closed.
Apr 19 11:18:47 PVR-1 nvidia-persistenced[1535]: The daemon no longer has permission to remove its runtime data directory /var/run/nvidia-persistenced
Apr 19 11:18:47 PVR-1 nvidia-persistenced[1535]: Shutdown (1535)
Apr 19 11:18:47 PVR-1 systemd[1]: nvidia-persistenced.service: Succeeded.
Apr 19 11:18:47 PVR-1 systemd[1]: Stopped NVIDIA Persistence Daemon.
Apr 19 11:18:47 PVR-1 kernel: resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000d0000-0x000dffff window]
Apr 19 11:18:47 PVR-1 kernel: caller os_map_kernel_space.part.0+0x100/0x140 [nvidia] mapping multiple BARs
Apr 19 11:18:47 PVR-1 snapd[1182]: AppArmor status: apparmor is enabled and all features are available
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (EE) NVIDIA(GPU-0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (EE) NVIDIA(GPU-0):     check your system's kernel log for additional error
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (EE) NVIDIA(GPU-0):     messages and refer to Chapter 8: Common Problems in the
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (EE) NVIDIA(GPU-0):     README for additional information.
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (EE) NVIDIA(GPU-0): Failed to initialize the NVIDIA graphics device!
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (EE) NVIDIA(0): Failing initialization of X screen 0
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) UnloadModule: "nvidia"
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) UnloadSubModule: "wfb"
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (II) UnloadSubModule: "fb"
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (EE) Screen(s) found, but none have a usable configuration.
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (EE)
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: Fatal server error:
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (EE) no screens found(EE)
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (EE)
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: Please consult the The X.Org Foundation support
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]:          at [http://wiki.x.org](http://wiki.x.org)
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]:  for help.
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (EE)
Apr 19 11:18:47 PVR-1 kernel: NVRM: RmInitAdapter failed! (0x26:0xffff:1123)
Apr 19 11:18:47 PVR-1 kernel: NVRM: rm_init_adapter failed for device bearing minor number 0
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1469]: (EE) Server terminated with error (1). Closing log file.
Apr 19 11:18:47 PVR-1 /usr/lib/gdm3/gdm-x-session[1467]: Unable to run X server
Apr 19 11:18:47 PVR-1 gdm-launch-environment][1330]: pam_unix(gdm-launch-environment:session): session closed for user gdm
Apr 19 11:18:47 PVR-1 gdm3[1325]: Child process -1467 was already dead.
```

---

### Post by CelticWarrior on 2021-04-19
When release upgrades fail the best solution is a fresh install.

---

### Post by grahammechanical on 2021-04-19
If you can get to a working desktop environment using the open source video driver (Nouveau) then continue doing so. What advantage do you expect to get from the Nvidia driver?

The only Nvidia driver available for my GT 216 is the 340 driver. I stopped using that some years back. Nvidia have a habit of dropping support for what they consider obsolete hardware. I do not have a problem with Nouveau using Wayland on Linux 5.4, 5.8 & 5.11 kernels. I have not run on the X Server for a long time. Or the Nvidia driver.

I understand the Nvidia drivers for some newer Nvidia cards are not working well with the latest Linux kernels. 

I have a question. What user interface were you using on 16.04. Was it Gnome 3 shell or Unity 7? If you were using Unity 7 and the LightDM display manager and at some point in the upgrade to 18.04 you authorised the removal of obsolete packages. Then the upgrade process would have removed Unity 7. It happened to me. If I am guessing correctly then you need to set GDM3 as the display manager.

```
sudo dpkg-reconfigure gdm
```

Choose GDM as the display manager.

Regards

---

### Post by ubfan1 on 2021-04-19
The daemon no longer has permission to remove its runtime data directory /var/run/nvidia-persistenced
Any UUID/GUID changes on the upgrade for nvidia-presistenced?

kernel: resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000d0000-0x000dffff window]
PCI buffer seems too small.  Mine is f80f7fff&#8722;bfa00000 (and is really boarderline for my needs).
Check your BIOS/UEFI settings.

Did you try running with no xorg.conf file?  It's been awhile since I've needed one.  Also, 20.04 secure boot needs to be off, while previously (not sure what ver) it didn't matter.

---

### Post by PaulRSte on 2021-04-20
> **CelticWarrior said:**
> When release upgrades fail the best solution is a fresh install.

Hi

I really considered this option as I have installed an SSD for the system files. The two HDDs are now used purely for Mythtv recordings and some backups. The reason that I didn't was that there were problems that people had on clean installs of 20.04 that they resolved by first installing 18.04. I was quite happy with the state of my 16.04 system so decided to go this route. I might still dig out an old disc and try it. Cheers

---

### Post by PaulRSte on 2021-04-20
> **grahammechanical said:**
> If you can get to a working desktop environment using the open source video driver (Nouveau) then continue doing so. What advantage do you expect to get from the Nvidia driver?

The only Nvidia driver available for my GT 216 is the 340 driver. I stopped using that some years back. Nvidia have a habit of dropping support for what they consider obsolete hardware. I do not have a problem with Nouveau using Wayland on Linux 5.4, 5.8 & 5.11 kernels. I have not run on the X Server for a long time. Or the Nvidia driver.

I understand the Nvidia drivers for some newer Nvidia cards are not working well with the latest Linux kernels. 

I have a question. What user interface were you using on 16.04. Was it Gnome 3 shell or Unity 7? If you were using Unity 7 and the LightDM display manager and at some point in the upgrade to 18.04 you authorised the removal of obsolete packages. Then the upgrade process would have removed Unity 7. It happened to me. If I am guessing correctly then you need to set GDM3 as the display manager.

```
sudo dpkg-reconfigure gdm
```

Choose GDM as the display manager.

Regards

I have been using Ubuntu to run Mythtv since version 7 (Feisty Fawn, I think) in the same Antec HTPC case. I replaced all the innards 5 years ago due to a power supply failure (under spec'd) but keeping the original specification in mind for a cool, quiet system. Hence the fanless Nvidia GeForce 520 and huge cooling fans on the power supply, cpu, and case. It runs at 8% cpu usage playing full HD at 1080p. I've always used the Nvidia drivers and rarely had a problem. I believe that the current version of Mythtv (31) relies on Open GL which the card also supports via the Nvidia drivers. At some stage  we will be replacing the TV with one giving 4K resolution so may need extra acceleration for that.
Not sure what shell  16.04 was running as it auto logged in, which it's not doing at present. Nearest option to what 16.04 was like is the one that just says "Ubuntu". Am I right in thinking that GDM3 is the current display manager from the log entries?

Regards

---

### Post by PaulRSte on 2021-04-20
> **ubfan1 said:**
> The daemon no longer has permission to remove its runtime data directory /var/run/nvidia-persistenced
Any UUID/GUID changes on the upgrade for nvidia-presistenced?

kernel: resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000d0000-0x000dffff window]
PCI buffer seems too small.  Mine is f80f7fff&#8722;bfa00000 (and is really boarderline for my needs).
Check your BIOS/UEFI settings.

Did you try running with no xorg.conf file?  It's been awhile since I've needed one.  Also, 20.04 secure boot needs to be off, while previously (not sure what ver) it didn't matter.

Hi

Not sure what is happening with nvidia-persistenced. The above folder doesn't exist; if it can't be deleted then maybe it hadn't created one. Don't know if it's possible to tell at that stage in the boot process.
Regarding the sanity check, this is the point at which the driver fails but I'm not sure exactly what it's saying. I've checked through the BIOS, and the motherboard manual, and the only options in that area are for legacy cards. not PCI PNP. The only option that seems relevant is one that controls the re-mapping of the memory hole, set to "Allowed". Also, cannot find a "Secure Boot" option so am presuming that it doesn't exist on this motherboard.  

Regards

---

### Post by ubfan1 on 2021-04-20
I have an old Lenovo Laptop, pre-secure boot, but full UEFI 64 bit, originally sold with 32 bit Windows 7.  I hung an external GPU adapter off the expresscard slot, and studied the egpu.io site for expected problems with graphics cards -- too big and the 32 bit PCI buffer overflows.   Worse, Lenovo had a late  firmware update which SHRUNK the PCI buffer space (TOLUD -- Top of Lower usable device space or something ) -" to give more room in the lower 4GB to 32 bit OS users"!"  Luckily I had not applied that firmware update.  The egpu.io site does offer instructions for changing the PCI buffer space to 36 bit to handle larger video cards.    I got a 4GB card, GTX970 to work, but maybe because it was really 3.5GB + 0.5 GB without any modifications of the existing PCI buffer  space, but others have had problems with 4GB cards.

---

### Post by PaulRSte on 2021-04-21
> **ubfan1 said:**
> I have an old Lenovo Laptop, pre-secure boot, but full UEFI 64 bit, originally sold with 32 bit Windows 7.  I hung an external GPU adapter off the expresscard slot, and studied the egpu.io site for expected problems with graphics cards -- too big and the 32 bit PCI buffer overflows.   Worse, Lenovo had a late  firmware update which SHRUNK the PCI buffer space (TOLUD -- Top of Lower usable device space or something ) -" to give more room in the lower 4GB to 32 bit OS users"!"  Luckily I had not applied that firmware update.  The egpu.io site does offer instructions for changing the PCI buffer space to 36 bit to handle larger video cards.    I got a 4GB card, GTX970 to work, but maybe because it was really 3.5GB + 0.5 GB without any modifications of the existing PCI buffer  space, but others have had problems with 4GB cards.

I have an HP laptop with Radeon graphics built in. This gives a similar message re the PCI bus

Apr 12 18:00:49 tancove-lt2 kernel: resource sanity check: requesting [mem 0x000c0000-0x000dffff], which spans more than PCI Bus 0000:00 [mem 0x000c0000-0x000c3fff window]
Apr 12 18:00:49 tancove-lt2 kernel: caller pci_map_rom+0x71/0x18c mapping multiple BARs
Apr 12 18:00:49 tancove-lt2 kernel: ATOM BIOS: HP
Apr 12 18:00:49 tancove-lt2 kernel: radeon 0000:00:01.0: VRAM: 384M 0x0000000000000000 - 0x0000000017FFFFFF (384M used)
Apr 12 18:00:49 tancove-lt2 kernel: radeon 0000:00:01.0: GTT: 1024M 0x0000000018000000 - 0x0000000057FFFFFF

This doesn't happen on the Mythtv machine when Nouveau is selected. When I install the Nvidia driver it loads this and the Nouveau driver.

The Mythtv (HTPC) system is a 64 bit AMD CPU on an ASUS M5A78L-M USB3 board. The graphics card is also ASUS - a GT 520 Silent with Nvidia GEForce 520 chips and 2GB memory.

---

### Post by PaulRSte on 2021-05-03
Summary of Responses and Actions:-

Celtic Warrior - Try a rebuild. I found a disc yesterday, disconnected all drives and connected this and then:-
     Wiped all petitions and installed 20.04.2 from DVD. Although the GUI did load whilst booting, it crashed before the login screen came up. The only thing displayed was a whirly circle with three sectors and "Ubuntu" in large caps. When it reverted to text mode it only displayed the results of the disc check. Logging in on TTY2, journalctl showed (again) that both nvidia and nouveau were being loaded, detail was shown about video modes, but in the end the system crashed exactly as logged above, i.e. gpu starts 2d acceleration, sanity check shows multiple bars being mapped, NVRM: RmInitAdapter failed! (0x26:0xffff:1123).

grahammechanical - sudo dpkg-reconfigure gdm, tried this - no change

ubfan1 - The daemon no longer has permission to remove its runtime data directory /var/run/nvidia-persistenced -  I believe that this is as expected. It is packaged to run as not root under system user "nvidia-persistenced" initiated by gdm. Have seen same in 16.04 logs.

ubfan1 - kernel: resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000d0000-0x000dffff window] - Theoretically this is not a problem but I believe that this is the issue as it always fails at this point, even on a clean build of 20.04. I have found some mention of this on web  with exact fail of NVRM but with multiple GPUs. Still searching for this.

ubfan1 - Check BIOS settings re PCI address space and also egpu.io site - Cannot find any reference to this in mother board manual, possibly hidden. Cannot find detail to change these settings on web site.

ubfan1 - Did you try running with no xorg.conf file? -  nvidia packaging creates this automatically.

ubfan1 - Also, 20.04 secure boot needs to be off - Not an option. I have enabled the virtual machine instructions as kernel complaining that kvm not enabled.

Think that's everything?

---

### Post by PaulRSte on 2021-05-04
In an attempt to bottom this, and working on the premise that it is related to "kernel: resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000d0000-0x000dffff window]".

This morning, I have tried the following, all without success:-
1)  Tried setting UMA framework size for onboard GPU to free off more memory. Made no difference at all, and when set to maximum value did not make it any worse. There is no BIOS option to disable this altogether.
2)  Tried setting "vmalloc=192M" on grub (see [https://forums.linuxmint.com/viewtopic.php?t=276488](https://forums.linuxmint.com/viewtopic.php?t=276488)). Absolutely no difference. Of course I realise that this might need totally difference for Ubuntu but I have no guidelines.
3)  Tried setting "PNP OS" to "Yes" in the BIOS. Again, no difference. Exactly same error message. Again though I cannot find what the setting should be for Ubuntu. I've always run with it set to "No", from Feisty Fawn (07) days.

I cannot find anything in the BIOS about changing the PCI address space. The PCIPnP menu only has the "Plug and Play O/S" options, the "Internal Graphics" section only has options for "Primary Display Adapter", "UMA Frame Buffer Size". an option to enable "Surround View" if an additional ATI card is present in the PCIE 16 slot, and an option to specify the location of the frame buffer "Above or Below 4G" (set as above).

Still trying to find a way to increase the PCI address space. Can anyone help?

---

### Post by PaulRSte on 2021-05-05
Testing with Ubuntu 18.04, kernel 5.4.0-72-generic, nvidia drivers 390 and 340, vmalloc at 512M, reverting Secure Virtual Machine Mode and PNP O/S both to off, vmalloc defaulted, have all yielded similar results around the kernel resour4ce sanity check with some results seeing the following repeated continuously:-


May  5 11:20:22 PVR-1 kernel: [  275.208125] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000d0000-0x000dffff window]
May  5 11:20:22 PVR-1 kernel: [  275.208376] caller os_map_kernel_space.part.11+0x104/0x140 [nvidia] mapping multiple BARs
May  5 11:20:22 PVR-1 kernel: [  275.311152] NVRM: RmInitAdapter failed! (0x26:0xffff:1123)
May  5 11:20:22 PVR-1 kernel: [  275.311192] NVRM: rm_init_adapter failed for device bearing minor number 0
May  5 11:20:22 PVR-1 kernel: [  276.108153] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000d0000-0x000dffff window]

---


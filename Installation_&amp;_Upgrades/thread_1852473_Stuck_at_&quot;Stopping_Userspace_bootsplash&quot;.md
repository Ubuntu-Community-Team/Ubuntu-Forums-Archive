---
title: "Stuck at &quot;Stopping Userspace bootsplash&quot;"
date: 2011-09-30
forum: Installation &amp; Upgrades
---

### Post by speculater on 2011-09-30
I've been using 11.04 for about 4 months and I just recently lost my old 500gb HDD due to "imminent failure".   Nothing else has changed on this PC, except for now I can't get past the  text that loads before the Desktop after installing nvidia  proprietary drivers.  I've tried about a dozen different methods (Including the entire trouble shooting flow chart),  nothing is working.  Attached are my most recent xorg logs.

The only way for me to regain control of my PC is to: 

alt+ctrl+f1

sudo apt-get remove --purge nvidia*

reboot




Otherwise I'm stuck at either "*Checking battery state" or "Stopping Userspace bootsplash"

my lspci is:

speculater@OldFaithful:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 Multimedia video controller: Conexant Systems, Inc. CX23418  Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio  Decoder
01:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
02:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
04:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)



If anyone can shed some light on this I will greatly appreciate your  help!  I've spent about 14 hours trying to get this working.

Let me know if more logs are needed.

---

### Post by dino99 on 2011-09-30
from the terminal:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo dpkg-reconfigure -phigh -a

sudo reboot

boot in recovery mode (hold "shift" key down at bios end process to get the grub menu) and select "repair packages"

---

### Post by speculater on 2011-09-30
That didn't work, but I'm curious if it's because I did this:
 
Boot and got stuck:
 
alt+ctrl+f1
login
sudo apt-get remove --purge nvidia*
 
reboot
 
While in X I used the terminal to:
 
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo dpkg-reconfigure -phigh -a
 
reboot
 
Entered Grub recovery mode
selected "repair damaged packages"
 
reboot
 
in X installed additional drivers
 
reboot and got stuck agian.
 
 
 
Do I need to do the steps you told me while the proprietary drivers are installed??
 
 
(attached is the picture I took of my screen at lockup.)

---

### Post by speculater on 2011-09-30
Please can anyone help?  This is really killing me not being able to use my Physic research software at home.

---

### Post by speculater on 2011-09-30
Bump and again I appreciate any advice and time spent helping me!

---

### Post by speculater on 2011-09-30
With the proprietary drivers installed I did the following:

alt+ctrl+f1 (To get a terminal)
login

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo dpkg-reconfigure -phigh -a
 
reboot
 
Entered Grub recovery mode
selected "repair damaged packages"
 
reboot

Held shft to get to grub menu
hit 'e' to enter temporary changes into grub
placed 'vmalloc=192MB' next to quiet splash
f10

And problem solved!

I then made the change permanent by editing my /etc/default/grub to include:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vmalloc=192MB"

---

### Post by brunolopes446 on 2012-02-23
Try this link, there is a command to restore the xorg.conf backup file
[http://ubuntuforums.org/showthread.php?t=1556967](http://ubuntuforums.org/showthread.php?t=1556967)

---

### Post by MAFoElffen on 2012-02-23
> **brunolopes446 said:**
> Try this link, there is a command to restore the xorg.conf backup file
[http://ubuntuforums.org/showthread.php?t=1556967](http://ubuntuforums.org/showthread.php?t=1556967)
That does not restore the Xorg.conf file... in that thread the solution was to remove all traces of the nvidia driver and move the Xorg.conf file somewhere where it won't be found by Xorg, yet you still have a copy of it if needed.

Actually, even if you do have a NVidia driver installed, if you move the xorg.conf file it will be disabled.  There are also other ways... But yes you are right.

The OP removed the driver but not the /etc/X11/Xorg.conf file... So in the file, Device section, Drver line... It is still like this example:
```
[FONT=monospace]
[/FONT]Section "Device"     
    Identifier     "Device0"     
    [COLOR=Red]Driver         "nvidia"[/COLOR]     
    VendorName     "NVIDIA Corporation"     
    BoardName      "GeForce 9800 GTX/9800 GTX+" 
EndSection

```Which would point xorg to a non-existent NVidia driver, which would cause a lock-up. 

You could move it, delete it or edit it to change the device section to 
```

Section "Device"     
[COLOR=Red]    Identifier    "Default Device"[/COLOR]     
    Option    "NoLogo"    "True" 
EndSection

```Any of those ways should work.
```

04:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)

```Now was one of your goals to reinstall a working NVidia driver, use Nouveau or VESA?

---


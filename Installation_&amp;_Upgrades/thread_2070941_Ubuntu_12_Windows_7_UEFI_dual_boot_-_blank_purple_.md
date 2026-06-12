---
title: "Ubuntu 12 Windows 7 UEFI dual boot - blank purple screen"
date: 2012-10-14
forum: Installation &amp; Upgrades
---

### Post by ssin16 on 2012-10-14
I got a new laptop (Asus K55A) and I am trying to dual boot ubuntu along with windows 7 (boots into UEFI mode and has GPT partition).  
I finished installation from a LiveCD. I was able to use ubuntu from LiveCD for most common applications, video/graphics/audio/wireless/touchpad all seemed to work fine. 
When I start my computer, I see the grub menu with ubuntu and windows option. I am able to start Windows7 from this grub menu (worked after doing boot-repair) but when I select ubuntu it goes into a purple blank screen and remains there until I turn off the power button.

What can i do next to further diagnose or fix this problem? This is the latest boot-info
[http://paste.ubuntu.com/1278578/]("http://paste.ubuntu.com/1278578/")
```
You can now reboot your computer.
Please do not forget to make your BIOS boot on sda1/efi/ubuntu/grubx64.efi file!

The boot files of [Ubuntu 12.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair].
```
I did not make any changes to my BIOS boot as it already shows the correct options (ubuntu/win7), would changing bios boot help?
I already have sda1 FAT 32 boot partition at start of the disk, so I don't understand why adding a new EXT4/start of disk partition is needed.   

Really appreciate all the help from these forums. I use RH linux at work for development but this is my first time doing a linux install on my own machine, thanks for the guidance/help here.

---

### Post by dino99 on 2012-10-14
while on the grub boot line, edit it to remove "splash", then ctrl+x to continue booting.

---

### Post by ssin16 on 2012-10-14
I tried a few of these options such as remove splash/quiet or both, add noapic or apic=off from the grub cmd line at start up but still did not help. Continue getting purple screen with nothing happening when i select ubuntu, windows 7 boots up fine from grub menu.

---

### Post by oldfred on 2012-10-14
Did you try nomodeset? What video card do you have?
Have you tried recovery mode? I think that now is with nomodeset.

And some systems need nomodeset plus some of the other settings you have tried.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by ssin16 on 2012-10-14
nomodeset option did not help, but after further reading on some other threads, I tried the following

On the grub menu, edit kernel cmd line parameters, make it "ro nosplash --verbose text" then press F10. Doing this I have been able to boot up into a text session 3 times but it is really random when I can log in and when I cannot (with same parameters as above). Once at a root prompt, I can do "sudo lightdm start" I get the login screen, I enter my password and I am logged into the desktop, everything works great. 

The REAL problem is I don't know when I will get this far or remain stuck on the purple screen, at this point seems really random. I got to the root text prompt 3 out of maybe 20 times I tried.

thanks for the help.
Here is the output from sudo hwinfo --frambuffers

```
process 6297: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
02: None 00.0: 11001 VESA Framebuffer
  [Created at bios.464]
  Unique ID: rdCR.QgFYtsmQZBC
  Hardware Class: framebuffer
  Model: "Intel(R) Sandybridge/Ivybridge Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(R) Sandybridge/Ivybridge Graphics Controller"
  SubVendor: "Intel(R) Sandybridge/Ivybridge Graphics Chipset Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 63 MB + 960 kB
  Memory Range: 0xe0000000-0xe3feffff (rw)
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x037d: 1366x768 (+1408), 8 bits
  Mode 0x037e: 1366x768 (+2752), 16 bits
  Mode 0x037f: 1366x768 (+5504), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

---

### Post by ssin16 on 2012-10-14
I think I finally solved it, this thread was very helpful to diagnose the issue
[http://ubuntuforums.org/showthread.php?t=1743535]("http://ubuntuforums.org/showthread.php?t=1743535")

I had to add the correct vga=XXX to the kernel command line and also set the gfxmode to the resolution supported by my machine. 

Steps:
1. Get the resolution supported by your drivers. I used "videoinfo" command from grub cmd line. It showed two different resolutions under "Adapter 'EFI GOP driver'", I used the lower resolution 800*600*32. 

2. Do "sudo hwinfo --framebuffer" (can be done from liveCD). Get the hexadecimal code matching the resolution we picked in step 1 above.

3. Convert the hexadecimal code to decimal, put the decimal value in place of XXX in vga=XXX string. 

4. Grub changes (/etc/default/grub)- add vga=XXX and resolution selected
GRUB_CMDLINE_LINUX_DEFAULT="nosplash vga=XXX"
GRUB_GFXMODE=800x600 (whatever resolution picked in step 1).

5. Install grub (sudo update-grub)

Thanks a lot, I am so happy I got my first dual-booting machine ready is less than 24 hours, would be impossible without all the forum help and the stuff I could read up and plan ahead of time.

---

### Post by Swoorup on 2012-10-15
Giving this a try. I too had this problem, almost too months nothing solved!

---

### Post by oldfred on 2012-10-15
I thought you were not supposed to use the vga= settings anymore.

vga=xxx is a deprecated boot option
Use this with your monitor size in /etc/default/grub:
GRUB_GFXMODE=1024x768
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993)
"VGA Deprecated" Message on Boot
[http://ubuntuforums.org/showthread.php?t=1453524](http://ubuntuforums.org/showthread.php?t=1453524)

VGA conversions:
[http://wiki.archlinux.org/index.php/Gensplash](http://wiki.archlinux.org/index.php/Gensplash)
[http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes](http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes)

---

### Post by Swoorup on 2012-10-15
I don't know why I cannot still get it to work with this method too. I have been watching the forums for almost 2 months hoping that someone had similar issue to one and have resolved it Even this method didn't work for me.

---

### Post by ssin16 on 2012-10-15
I removed vga=xxx and it continues working so vga was redundant. I did not know it was no longer used.
 What it really needed was the correct resolution supported by the driver in GRUB_FXMODE value in the grub file.

---

### Post by Swoorup on 2012-10-17
Nothing really seems to be working for me. I couldn't get verbose texts with
--verbose tex too

---

### Post by Swoorup on 2012-10-17
I have almost lost hope on ubuntu 12.04. I am wondering if the new ubuntu which is scheduled to be released by tomorrow will solve my problem because it uses a new kernel and addresses graphical issues?

---

### Post by mlaverdiere on 2012-12-31
I don't know if your problem is the same as mine, but in my case, disabling the integrated NIC in BIOS allows me to boot Ubuntu 12.10 64 bits in UEFI mode on a Dell Inspiron 14z Ultrabook with an Atheros AR8162 ethernet card (NIC).

See this thread I've started about this:  [http://ubuntuforums.org/showthread.php?p=12418593#post12418593](http://ubuntuforums.org/showthread.php?p=12418593#post12418593)

---


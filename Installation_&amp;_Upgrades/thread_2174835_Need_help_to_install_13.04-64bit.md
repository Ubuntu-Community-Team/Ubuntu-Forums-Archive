---
title: "Need help to install 13.04-64bit"
date: 2013-09-16
forum: Installation &amp; Upgrades
---

### Post by Michael_Symons on 2013-09-16
Hi,

I'm a Linux novice.

My laptop is this:
[http://www.mytoshiba.com.au/products/computers/qosmio/x70/psplta-014001](http://www.mytoshiba.com.au/products/computers/qosmio/x70/psplta-014001)

Secure boot is disabled. EFI is locked to enabled.

I have tried to boot from both live USB and live CD. Each time I get the EFI boot loader. After choosing any option the screen goes blank and the computer hangs.

After inserting "nomodeset" into the boot loader options, I got:

(edited)
 3 screen flashes of white text

whole bunch of lines of white text here.............................
.................................................................................
Hard drive detected
USB device detected
etc etc
....................................................................................
Welcome to GNU linix (kernel-version-generic)

[EMAIL="Ubuntu@ubuntu~$"]Ubuntu@ubuntu~$[/EMAIL]

That's it. It stops there at BASH ([EMAIL="Ubuntu@ubuntu~$"]Ubuntu@ubuntu~$[/EMAIL]         ). I can type HELP to get a list of commands but I have no idea what is useful.

I was able to type "sudo reboot" and get back to windows 8.

If I could just get to the installer GUI I could go from there. But I can't get to it.

Any help appreciated, because VMs are laggy and Win8 is brilliant, but there are some glitches which drive me mad, like persistent corrupted web browser windows/images + general graphics glitches after the computer changes power states and the failure to shut down normally sometimes. 

Thanks :)

---

### Post by Michael_Symons on 2013-09-16
Any ideas what to do after I get [EMAIL="Ubuntu@ubuntu~$"]Ubuntu@ubuntu~$[/EMAIL]  on the live USB?

I really would prefer a GUI install.

---

### Post by Kirboosy on 2013-09-16
Welcome to the forums! :D

How did you go about making your USB drive? It sounds like something isn't setup correctly on the USB drive.

[UEFI Community Documentation ]("https://help.ubuntu.com/community/UEFI")

Hope that helps!
~Caboose

---

### Post by oldfred on 2013-09-16
Different model newer Toshiba.
 Toshiba Satellite P75  intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

Another user posted this

 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Ubuntu on Laptop Toshiba Satellite P75 - Haswell
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by Michael_Symons on 2013-09-16
I managed to get a GUI boot after setting "NOMODESET" in the "Install Ubuntu option"

It does not detect a windows 8 partition (worrying)

The rendering was a tiny bit glitchy in this mode, for example dropdown boxes left their borders behind.

I don't want to purge my win8 without knowing with at least a little certainty I can complete the installation of Ubuntu, and have graphics that work without nouveau crashing/preventing boot up (in CMS boot, which was tricky to do.... the live disk crashes after initialising nouveau). 

After install, can the issues with (presumably) optimus bootups be fixed to a tolerable level? I really like Ubuntu, I just don't want a headache.

---

### Post by Michael_Symons on 2013-09-16
Going to pull out both my hard drives and try playing around on a spare 300gb HDD to see what happens, but first I must sleep OMG 3am!!!!

---

### Post by oldfred on 2013-09-16
If you have not turned fast boot off then it will not 'see' the Windows NTFS partition. Fast boot is hibernation.

       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by Michael_Symons on 2013-09-16
So far still no successful boots.

I have managed to install Ubuntu 13.04 on my old hard drive, but now I boot to a black screen without NOMODESET and to a purple screen with NOMODESET

The recovery boot works and I was able to SUDO APT-GET UPGRADE from the terminal.

But still no GUI!

without NOMODESET
black screen
power button does not work

With NOMODESET I get purple screen with the following output
Starting (kernel version-generic)
Starting initial RamDISK
_
(system hangs)

power button successfully shuts down

---

### Post by oldfred on 2013-09-16
I thought recovery mode just included nomodeset (and recovery) parameters?

It says it includes SSD. So is it classified as an Ultrabook?

 Ultrabooks use dual video both Intel & nVidia. Some auto switch and others have settings in UEFI/BIOS to select one or the other. If Intel you may need different settings or with nVidia sometimes other settings that nomodeset may be required.

 Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1 
[*]nVidia: nomodeset 
[*]Generic: xforcevesa or nouveau.modeset=0 
[*]Radeon: radeon.modeset=0 
[/LIST]

 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
 i915.i915_enable_rc6=1

 Asus i3 with Intel graphics, 
acpi_osi=Linux
video=1280x1024-24@75 or whatever native resolution is

   Some other boot options
acpi_osi=Linux 
acpi_backlight=vendor

---

### Post by ubfan1 on 2013-09-16
Have you tried the acpi_osi=linux as well as the nomodeset?

---

### Post by Michael_Symons on 2013-09-17
I started a new thread since I feel the issue has changed to a slightly different topic, and I don't feel this thread will get the help I'm looking for. Thanks to everybody who posted :)

---


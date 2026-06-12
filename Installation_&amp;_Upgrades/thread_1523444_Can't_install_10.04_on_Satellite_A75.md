---
title: "Can't install 10.04 on Satellite A75"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by patanjalimuni on 2010-07-03
[SIZE=4]Friends,[/SIZE]
 [SIZE=4]I've tried unsuccessfully to install Ubuntu 10.04 (the latest edition as of this date) on my Toshiba satellite a75 running XP Home, trying all the things detailed below. Thanks for any suggestions.[/SIZE]
 [SIZE=4]
[/SIZE] 
 [SIZE=4]All my attempts were with the desktop edition. My large-screen laptop is more like a desktop than like a netbook.[/SIZE]
 [SIZE=4]
[/SIZE] 
 [SIZE=4]1. Since I didn't see a checksum on the site, I downloaded the iso file twice, and compared them with a Windows utility&#8212;the iso files were the same, so I assume they are valid.[/SIZE]
 [SIZE=4]2. I thoroughly checked my RAM and 2 hard drives on which I tried the install, both before and after the failed installations, using the manufacturer's "advanced" utility and also another drive utility which shows SMART values. All the hardware seems very healthy.[/SIZE]
 [SIZE=4]3. When burning the CD, I selected the option to verify the CD&#8212;the CD's match the iso files.[/SIZE]
 [SIZE=4]4. First I tried doing a full install on a spare drive (which I put inside the laptop), i.e. installing Ubuntu by itself on the drive, without Windows. The install seemed to go fine. After reaching 100%, a dialog appeared saying something like 'click to restart'. After clicking, the CD automatically ejected and I got a screenful of errors something like:[/SIZE]
 [SIZE=4][1950.240390] end_request: i/o error dev sr0 sector 506416[/SIZE]
 [SIZE=4]init plymouth main process killed by BUS signal  [/SIZE]
 [SIZE=4]init: plymouth-splash main process (21554) terminated with status 1.[/SIZE]
 [SIZE=4]Note: in one attempt, it also said something like "atiixa codec reset timeout" (this may be misspelled)[/SIZE]
 [SIZE=4]
[/SIZE] 
 [SIZE=4]When I rebooted, then it got to the login screen, but then a few seconds later went into 'standby' mode. Usually on this laptop, when the power button is pushed in standby mode, then it boots up, but in this case it was stuck. I had to force the power off.[/SIZE]
 [SIZE=4]
[/SIZE] 
 [SIZE=4]5. I tried booting up several times, then reburned the CD and tried again. Same story.[/SIZE]
 [SIZE=4]
[/SIZE] 
 [SIZE=4]6. Someone said sr0 may be the cd drive. I thought perhaps the cd was being ejected too early, so I tried to hold the tray in to keep it from ejecting (that doesn't harm my tray). Same results.[/SIZE]
 [SIZE=4]
[/SIZE] 
 [SIZE=4]7. I tried installing Ubuntu alongside my existing system (this is a different hard drive). Same story: everything seemed fine until login, then it immediately got stuck in standby mode. I don't know if it displayed the screenful of error messages, since I was out of the room.[/SIZE]
 [SIZE=4]
[/SIZE] 
 [SIZE=4]8. I tried running from the CD. This worked, except that when I tried to import contacts into Evolution, Evolution (but not Ubuntu) crashed. On terminating the session, I again got a similar screenful of error messages. Don't recall whether the CD had automatically ejected before that.[/SIZE]
 [SIZE=4]
[/SIZE] 
 [SIZE=4]9. I emailed the person who maintains a page in the Ubuntu community on testing the Satellite A75. The page indicates a few problems, but he said that basically Ubuntu ran on that model--nothing like the problems I had.[/SIZE]
 [SIZE=4]
[/SIZE] 
 [SIZE=4]10, I tried running from a USB flash drive. After accessing the boot selection menu and selecting something like "external drive", the system pondered for a while, then said "PXE-2.0 No boot file name received", and booted into XP. Tried this with two different flash drives.
[/SIZE]
 [SIZE=4]
[/SIZE] 
 [SIZE=4]11. About ready to give up :( --thanks for your thoughts![/SIZE]

---

### Post by oldfred on 2010-07-03
I thought I saw where some messages after the install from a CD should be ignored. The error messages are an error.

Many seem to have issues with video drivers. My monitor  went to sleep, but I could see it still working from the USB flash drive.  I have a desktop with nvidia but the nomodeset setting works for many video systems:

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
I edited my grub.cfg as I use grub to boot ISO, in syslinux.cfg or text.cfg
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Kernel update splash screen issue.
[http://ubuntuforums.org/showthread.php?t=1503509](http://ubuntuforums.org/showthread.php?t=1503509)

---

### Post by patanjalimuni on 2010-07-03
Thanks *very* much. May take several days to work through this, but I will let you know the outcome.
BTW, I have a ATI/Radeon graphics card.

---

### Post by patanjalimuni on 2010-07-06
Friends,
A report...
I should say that I am a complete newbie to Linux.
I read through the helpful references given by OldFred and have tried a number of things.

1. When installing Ubuntu this time, I did choose the 'no-APCI' option.
Pressing 'e' on the first boot of Ubuntu, I removed 'quiet' and 'splash', replacing them with 'nomodeset'.
This led the the same result, i.e. about one second after the login screen appeared, the system went into standby and had to be forced off.

2. Tried booting into failsafe graphic mode. The system gave the following error:

"The following error was encountered. You may need to update your configuration to solve this.
error: (EE)HD 1267:0103 failed to initialize for relative axes"

I then selected the option to run in low graphics mode for one session--same problem of going into standby mode.

3. I should mention again that when running from the Live CD (i.e. without installing Ubuntu), then everything seems to work well. There was no obvious problem with graphics or anything else. 

4. Someone told me how to start in recovery mode.
I tried various options here. There's a lot of troubleshooting information, logging the boot process which I wouldn't know how to use. I tried booting to a root shell, but couldn't seem to access any files.

BUT the good news:
I tried installing Fedora, and it worked perfectly. At some point in the future, I would still like to try Ubuntu, but at this point I think it makes sense for me to learn more about Linux first.
I very much like the organization and richness of the Ubuntu site, and the community help that is available, and plan to be back sometime.

Many thanks again for your help!

---

### Post by patanjalimuni on 2010-08-28
THE SURPRISING SOLUTION:
Using Kubuntu instead of Ubuntu solved the problem.

After encountering this problem, I tried installing several other distributions. OpenSUSE sometimes had a similar problem, and then would often give an error that Power Manager was not responding.

Searching for this, I found that others had solved it by disabling the Gnome Power Manager, though some said that somehow it got re-enabled later. I decided just to go with KDE, which solved the issue on OpenSUSE and Ubuntu.

In all fairness to Gnome, probably my system could have been configured to work with Gnome. For one thing, Fedora 13 + Gnome didn't have this anomaly. BUT there were many other issues, probably unrelated, with Fedora 13, including frequent kernel crashes and the inability to install any updates. Some people say that Fedora 13 is much more stable than previous Fedora releases, but that was not true on my system.

I see too that on the Gnome Power Manager page, it advises "Make sure to get  latest release of UPower, the service that GNOME Power Manager depends on."

I appreciate the suggestions to look into video card problems, since evidently that is an issue for many systems. I guess the first option there is to try putting "nomodeset" in the kernel boot command line, or just try booting into failsafe graphics mode, though didn't address my situation.

By the way, I love Kubuntu with the beautiful KDE 4 desktop. 

Thank you all again.

---


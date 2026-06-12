---
title: "Ubuntu installer does not detect hard drive"
date: 2017-04-02
forum: Installation &amp; Upgrades
---

### Post by gategatebodhisvaha on 2017-04-02
My mother just purchased an Acer Aspire ES 13 (ES1-332-C3QY), and has asked me to wipe and install ubuntu on it. However, the Ubuntu installer does not detect the hard drive, the liveusb stick shows up as /dev/sda and no other drives show up. So far I have disabled secure boot and fastboot. As an aside, I have also noticed that whenever windows has started up the bios clock is moved back 2 hours, don't know if that is pertinent to the issue at hand.

Thankful for any help!

---

### Post by Dennis_Beekman on 2017-04-03
I have got the same problem here... Arch linux and Debian see the storage drive normally but the Ubuntu livedisk for 16.10 and 17.04 are both unable to find the drive at all.
Why don't you have a look at my post from last week to see if any of the feedback helps you at all.

[https://ubuntuforums.org/showthread.php?t=2357354](https://ubuntuforums.org/showthread.php?t=2357354)

---

### Post by Mark Phelps on 2017-04-03
If the new PC came preinstalled with Win10, then the problem is that Fast Startup is enabled (by default) in Win10 so that even when Windows is not running, the filesystem remains mounted.  This prevents any Linux distro from mounting that filesystem -- and if it can't mount it, it will have problems seeing it.

You have to go into Win10 and disable Fast Startup...

There are two ways to disable FastStartup in Win8/10; (1) through the Control Panel, and (2) through an elevated command prompt.
 
Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup
 
Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F
 
In both cases, reboot Windows.
 
NOW, FastStartup is disabled.

---

### Post by gategatebodhisvaha on 2017-04-03
Thank you for your responses!

Dennis: I checked your thread, and just like for you the drive is not listed by gparted nor fdisk. Hmm, so maybe have to do a debian install... weird. I wonder if I could install debian and then ubuntu.

Mark: Fastboot was my first suspected culprit, but as stated I have already turned it off (and restarted windows several times).

---

### Post by gategatebodhisvaha on 2017-05-04
Finally had a chance to attempt the install again trying with debian, but the debian installer was unable to find the drive as well. Any input would be welcome!

---

### Post by oldfred on 2017-05-05
Is drive set to AHCI in UEFI?
Is this a new NVMe SSD?

Have you installed the latest UEFI from Acer. Some have had issues.
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 

Once installed you will have to enable a supervisory password & set trust on the Ubuntu .efi boot files in the ESP.
      
 Acer Aspire ES1-132 cannot able to install kubuntu UEFI missing options, rEFInd
[https://ubuntuforums.org/showthread.php?t=2348269](https://ubuntuforums.org/showthread.php?t=2348269)
Acer Aspire R5-417T
[https://ubuntuforums.org/showthread.php?t=2346815](https://ubuntuforums.org/showthread.php?t=2346815)
Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757) 
            Acer Spin 5 Ubuntu 17.04 Needs Acer password & trust
[https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx/909238#909238](https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx/909238#909238)

---

### Post by gategatebodhisvaha on 2017-05-05
Thank you for your response.

I have updated to the latest bios version, set bios password, disabled secure boot, disabled fast boot in windows 10. My problem however is that unlike all the other people struggling in different ways with acer laptops i can't actually install ubuntu on to the laptop as the only drive that shows up in the ubuntu installer is "/dev/sda 'name of usb stick'". Nothing else but this and ram under sudo fdisk -l. It seems the installation device is unable to see the hard drive, which to answer your question is an eMMC ssd. I've tried making liveusb sticks with both startup disk creator and unetbootin, and have tried to both make the liveusbs direct and after clearing them in gparted.

Also for clarification, my mother doesn't want to dual boot, she wants me to wipe it and just put ubuntu on the laptop. The problem isn't that grub can't find the partition, it's that the installer doesn't actually find the hard drive to install ubuntu.

---

### Post by oldfred on 2017-05-05
Is that a Bay Trail cpu?

I do not think the newer versions of Ubuntu need the intel_idle.max_cstate=0
[https://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10](https://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10)

 Acer Aspire ES1-132 cannot able to install kubuntu UEFI missing options, rEFInd
[https://ubuntuforums.org/showthread.php?t=2348269](https://ubuntuforums.org/showthread.php?t=2348269) 

 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)

---

### Post by Geoffrey_Arndt on 2017-05-06
If only Ubuntu is to be on the laptop, . . . AFTER setting up a supervisor password (and then rebooting and going back into uefi/bios) - - - I would suggest to enable Legacy mode (ignore the warnings from Acer).   Also, be sure you have enabled special bootmenu and placed usb device as the top listing in the boot sequence.   Might have to play around with that sequence to find just the right combo.    To display the one time boot menu at startup, just keep tapping the F12 key.

---

### Post by gategatebodhisvaha on 2017-05-06
@oldfred
The processor is a Intel Celeron N3350.

All the other issues i keep finding and that you are linking to are people who can actually go through the installation process and then not find the install. The problem here is that I can't even go through the install as no drive to install comes up other than the liveusb media that the installer is on.

---

### Post by gategatebodhisvaha on 2017-05-06
@Geoffrey_Arndt

That's another issue, there is no option for legacy mode in the bios. I checked an acer video showing where it is supposed to be (above the secure boot option), but there is just nothing there.

---

### Post by Geoffrey_Arndt on 2017-05-06
The UeFI  spec says OEM's _have to provide the option to enable Legacy mode_.  Two situations may be happening that prevents you from seeing that option:

1).   A supervisors "log-in" to the uefi firmware (aka bios) is required - - so, first setup the password (aka, register the password on the bios), then save (usually F10), then reboot and F2 back into the bios, enter your supervisors password and you should see additional options on some or all of the bios setup screens.    If you still don't see an enable "Legacy CSM" mode option, then,

2).   You may have an old bios that needs a firmware update.   Some users have written that doing the firmware update gave the option to setup Legacy mode.

note, one also needs to closely examine every single page in the uefi . . some see the "Boot" tab & enter that page.   Often these settings are on the "Main" tab page instead.

note2:   the video you saw may be how bios looked before Acer changed to requiring Supervisor password . . . 

As a final resort, you can always contact Acer support via email or live chat and ask how to set Legacy mode and disable uefi.    These OEM's don't want users doing that (enabling Legacy) so it's often hidden and convoluted how to do it.

---

### Post by gategatebodhisvaha on 2017-05-10
Okay, so suddenly the hard drive showed up. I'm unsure if it was the fact that I turned of some form of drive protection feature in BIOS, or if it was because I tried using Ubuntu 17.04 instead of 16.04. Now however I have a new issue. After installing and rebooting I get no bootable device found. All other solutions seem to be either to set uefi file as trusted or to switch to legacy mode. Unfortunately neither of these options are available in my bios. I've set all passwords I can but still no option. It is not that it is greyed out, it's that it isn't there. Any idea on other methods that could work?

---

### Post by oldfred on 2017-05-10
Some that originally did not have setting mentioned downgrading UEFI.
But then many newer threads have said newest UEFI from Acer fixed issue. 
Do you have latest UEFI from Acer?

       Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

Each post essentially same, but each may give a bit different explanation that helps?
Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323) 

Other systems that do not boot boot a fallback or hard drive entry.
We can see if that works with your Acer if none of above works.
You can use Boot-Repair to do the file copy part (many threads where users manually copied /EFI/ubuntu to /EFI/Boot & rename shimx64.efi to bootx64.efi), and efibootmgr to add an entry if UEFI does not auto add one.
More details also in link in my signature.
[URL="http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141"]
[/URL]

---


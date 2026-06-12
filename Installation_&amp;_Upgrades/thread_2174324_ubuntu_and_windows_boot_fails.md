---
title: "ubuntu and windows boot fails"
date: 2013-09-13
forum: Installation &amp; Upgrades
---

### Post by pi149 on 2013-09-13
I am trying to install ubuntu 12.04 along side windows 8 on my new computer.
when ubuntu failed to boot (i get lots of messages too fast to read saying things like "unable to read config index scripter broken start error -71" or something, then it tries to go into low graphics mode, fails, and says broken pipe) after instalation i followed the steps at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair).
fixed nothing, but now windows wont boot.
 so, as instructed, i am posting here for help, and it said I should post the following address: paste.ubuntu.com/6104058

thank you for any help.

EDIT: windows magicaly works again

---

### Post by oldfred on 2013-09-14
When you say Windows works is that from grub menu?

What system is this and what video card/chip do you have?

Have you tried nomodeset? Some systems need other boot parameters instead of nomodeset or in addition to nomodeset.
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by pi149 on 2013-09-14
thanks,
yes windows works from grub.

ok, so now ubuntu will boot into a terminal and display the following messages infinitely

usb 1-7: unable to read config index 0 descriptor/start: -71
usb 1-7: cant read configurations, error -71
hub 1-0:1.0: unable to enumerate usb device on port 7

---

### Post by oldfred on 2013-09-14
Is this booting from USB?
Are you using a hub or is that just the internal configuration?
Do you have a device in the USB port that is conflicting? Mouse & keyboard should be ok.
Was ISO confirmed to be correct when you downloaded it with md5sum? 
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by pi149 on 2013-09-14
not booting from usb
no devices in usb ports
iso confirmed correct

---

### Post by oldfred on 2013-09-14
Some systems require other settings besides nomodeset or changes in UEFI/BIOS settings. These have been posted by other users.

 pci=nomsi  or  ACPI=Off
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
fixed the problem by adding rootdelay to grub.cfg this allows time for the usb drive to load.

  Some systems need these boot parameters usually nomodeset also required.
ACPI=Off 
pci=nomsi
 noapic
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
Some other boot options
acpi_osi=Linux 
acpi_backlight=vendor

      
 Toshiba Satellite P75  intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)
      
 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.

---

### Post by pi149 on 2013-09-14
ok, I tried all those options, result is:
ubuntu boots to terminal
displays something like "mei" (some numbers) "init hw failure"
and one other line to breifly to read
then repeats the same three messages forever:
usb 1-7: unable to read config index 0 descriptor/start: -71
usb 1-7: cant read configurations, error -71
hub 1-0:1.0: unable to enumerate usb device on port 7

---

### Post by oldfred on 2013-09-14
What is on port 7? 
If you do not know port 7 (I would not), try unplugging different devices. Is anything unusual in one port?

---

### Post by pi149 on 2013-09-14
as far as i know, nothing is in any port.

---

### Post by oldfred on 2013-09-14
Do you have the network interface controller in UEFI/BIOS? Try turning that off.

---

### Post by pi149 on 2013-09-15
turning off does nothing (at least i think its off)

---

### Post by oldfred on 2013-09-15
I am about out of ideas. What system was this?

---

### Post by pi149 on 2013-09-15
thats ok, i just went through every step i already tried one more time, and now it magically works!
I am still very confused about this.
Thanks for the help, guess i just needed to do everything 5 times

---

### Post by oldfred on 2013-09-16
Sometimes you just have to sprinkle the magic pixie dust before executing the command to get it to work. Many time that seems to be the only difference. :)

---


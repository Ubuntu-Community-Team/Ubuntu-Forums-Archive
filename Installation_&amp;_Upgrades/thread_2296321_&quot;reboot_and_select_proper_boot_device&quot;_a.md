---
title: "&quot;reboot and select proper boot device&quot; after ubuntu install"
date: 2015-09-25
forum: Installation &amp; Upgrades
---

### Post by Bob_Threshta on 2015-09-25
Hello! I have been attempting to dual-boot Ubuntu on a Windows 8.1 Machine. I was able to install Ubuntu onto a flash drive and successfully install it onto my computer, but when I go to reboot my PC from the Live envornment, I get the error "reboot and select proper boot device." I know that I have selected the proper boot device. (UEFI 2TB Harddrive where my Windows and Ubuntu is installed).
I have ran Boot repair nearly 20 times and it hasn't been able to fix this for me. I'm quite literally stuck in the Live envirnment as that's the only thing I can boot up right now. It's impossible for me to format the drive as I have important data on my Windows installation. Any help would be greatly appreciated.
Please use this: [http://paste.ubuntu.com/12551791/](http://paste.ubuntu.com/12551791/) as apparently that's useful.
Thank you!
I apologize if this is in the incorrect spot and if there is already documentation on this. I have literally spent 8 hours trying to fix this problem by looking at ubuntu documentation and forum responses, I have tried everything and I have not been able to fix it. I apologize if this is a stupid question, but I am new to Linux and this whole experience has just been completely offputting for me.

---

### Post by Bucky Ball on 2015-09-25
*Thread moved to **Installations and Upgrades**.*

> **Bob_Threshta said:**
> ... I am new to Linux and this whole experience has just been completely offputting for me.

That's why you post here. :)

Welcome, and not a stupid question. These things happen and you've done a good thing by posting the bootinfo from Boot Repair. 

Firstly, what is sdb and sdb1? You have sda, where everything is installed; sdb, which is unknown; then sdc, the Live install media.

Have you got the BIOS set to boot from sda, first boot device? (HD0 in Win terminology.) It may be booting the sdb drive which is 'unknown' and would cause an error pretty close to what you're getting.

May take a little tweaking to start with, but once you have a Linux box up and running it is very stable. ;)

PS: I'm also wondering about sda1, the BIOS boot partition, but I am not expert on this. There are members who are and hopefully they can chime in soon.Has a grub image in there. Looks like you've installed in EFI, which is correct as Win was in that. 

How exactly did you install? You switched off hibernation in Windows beforehand?

---

### Post by yancek on 2015-09-25
The BIOS boot partition is needed with a GPT disk that is NOT using UEFI.  You have both the BIOS boot partition (sda1) and a UEFI partition (sda2).  You have Grub boot code in the master boot record of sda which generally creates problems if you are using UEFI to boot.  sda2, the EFI partition has the correct Ubuntu and windows files to boot EFI.   Do you have the computer set to boot from sda and are you using UEFI setting in BIOS?

---

### Post by oldfred on 2015-09-25
It seems to say Acer. Acer is one that requires you to set a supervisory password and then set "trust" and the ubuntu efi boot files.

 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)
Details on password & trust setting:
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)

---


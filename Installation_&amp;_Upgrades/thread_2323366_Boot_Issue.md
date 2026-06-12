---
title: "Boot Issue"
date: 2016-05-04
forum: Installation &amp; Upgrades
---

### Post by wildmanne39 on 2016-05-04
Hi, I installed ubuntu mate on a laptop with windows 10 of it uses UEFI this time ubuntu intalled with UEFI enabled instead of legacy so I had a little hope it would boot correctly.

However whichever OS I want to boot has to be in the first boot position or it will not boot. I have to go into setup everytime I want to switch from ubuntu to windows.
I ran the boot script and the out put is at the link.
[http://paste2.org/5UvjyjYB](http://paste2.org/5UvjyjYB)
Thanks for all help! I hope to resolve this I have been having to go into to setup to change fro ubuntu to windows by changing UEFI to legacy for the last 3 years or so but now I am having to us windows more so it is more inconvenient.

I did run boot repair but that just added a lot more entires to the grub menu and I received a message saying the repair failed.

---

### Post by RobGoss on 2016-05-04
Hello Wild Man, I've ask this question seeing I have the same problem with one of my machines, I was told you probably need to** install Ubuntu in the same boot order as Windows **ether in **UEFI or Legacy**. I decided to leave mine as it is because i don't really use Windows that much but I'm kinda interested to see how you can fix this problem 

I'm sure there must be an easier way to accomplish this

---

### Post by ubfan1 on 2016-05-04
First, add yourself to bug 1091464,  "Unable to chainload Windows with secure boot enabled".  Then disable secure boot.  Edit /etc/fstab and remove the # (comment) on the /boot/efi mount.  Use the EFI menu at power-up (some function key) to select ubuntu, it should boot.  use efibootmgr to put the ubuntu entry (number 5) to the first place, or second after usb, but before Windows.  That should be a working setup for a UEFI boot.  If your specific machine strays from the standard UEFI path, because of vendor #@$%..., try looking for the solutions involving renaming the "ubuntu" boot entry to "Windows Boot Manager", maybe rename the shimx64.efi to bootmgfw.efi, and best to do anyway, copy the contents of /EFI/ubuntu to /EFI/Boot, rename any existing bootx64.efi to bootx64.efi.save, and rename the /efi/Boot/shimx64.efi to /EFI/Boot/bootx64.efi.  More details on many threads here, if those steps are necessary

---

### Post by oldfred on 2016-05-04
I see Gateway.
And the few Gateways seem to have a limited UEFI.
But it is part of Acer, so may have the same UEFI requirement of setting UEFI supervisory password and enabling trust?
Is it also an InsydeH20 UEFI ?

Acer also had issues with one version of UEFI. Early posts said to downgrade UEFI to previous, but newer posts said very newest UEFI works. Have you downloaded newest UEFI?
 One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)

---

### Post by wildmanne39 on 2016-05-04
No, I have not downloaded the newest UEFI but I will give that a try.
Thanks

---

### Post by wildmanne39 on 2016-05-09
I have done everything that I can with this gateway and it looks like I will have to go into setup and change the boot order when I switch from ubuntu to windows but I can live with that.
Thanks everyone for your help.

---

### Post by oldfred on 2016-05-09
Does system not have a one time boot key like f10 or f12. My Asus motherboard uses f8. So you do not have to go into UEFI/BIOS, but just choose when rebooting.

If UEFI has fast boot setting (not the Windows fast start up), that must be off, or it boots too quick to have time to press a key. 

My motherboard has separate fast boot settings for both cold boot & warm reboot and also a delay on fast boot which I set to 3 sec on reboot and normal boot on cold boot. And set grub to 3 sec/

---

### Post by wildmanne39 on 2016-05-10
> Does system not have a one time boot key like f10 or f12.I tried the f keys but they did not work.

I went into setup and there is nothing I can change except boot order well I knew it was dangerous but I reset the bios that I believe where changed when I installed ubuntu mate, after which I can now only boot windows.

Should I run boot repair again or what is your best guess.

Edit: When it is turned on I get a message HDD is not accessible due to security polices.
So I am guessing secure boot is causing the issue. 
Thanks

---

### Post by oldfred on 2016-05-10
I have with both old BIOS and new UEFI installed updates and the updates reset everything to system defaults. And in both systems, I had many settings that I had changed. With old BIOS I had to take photos to remember all settings. My UEFI spits out a list of changes on save and also has screen shots.

But if you reset to defaults, it almost for sure turned Secure boot back on. If you previously had changed other settings, you probably have to update those also.

---

### Post by wildmanne39 on 2016-05-11
I ran boot repair and I can now boot both OS's again. I found a setting in setup that let me turn on f12 as my boot menu key so I can now hit f12 and choose which system to boot.
Thanks everyone for your help especially oldfred.

---

### Post by oldfred on 2016-05-11
Glad you got it working. :)

---


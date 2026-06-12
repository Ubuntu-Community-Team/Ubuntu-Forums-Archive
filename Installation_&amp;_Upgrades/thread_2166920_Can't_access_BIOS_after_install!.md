---
title: "Can't access BIOS after install?!?"
date: 2013-08-11
forum: Installation &amp; Upgrades
---

### Post by gabe2 on 2013-08-11
I'm a newb, and I posted this issue earlier in the Absolute Beginners section, but now I see that I should have posted my problem here, so here it is:

I installed Ubuntu 12.04 on my second hard drive, careful to manually assign the correct partitioning scheme while leaving my C drive alone with Win7. That went fine. I then proceeded to reboot, but trying to get into BIOS at the POST screen (yes, I hit the right button, the DEL key for my motherboard, I built the thing and overclock, so I know my way around). To my surprise, I did not go into BIOS, instead I got a screen telling me to either boot up Win7 or configure my boot options. Ok, I figured, I go into boot options, but there was nothing about Ubuntu and it only asked me if I wanted to boot up Win7 in safe mode, normal, etc. I thought maybe it was a one-time glitch. I rebooted, but the same thing still happened but no asking me for options, just a longer-than-usual Win7 load. I was able to get into Ubuntu by using F12 and changing the boot order, but it's only a one-time deal and I'd have to do that every time I boot up if I want to get into Ubuntu. Not only is that annoying, but I don't like not being able to access BIOS, especially considering I've tweaked settings in there.

Anyway, I noticed that I had the wrong idea about the /home partition and didn't give it the rest of the second hard drive space like I should have. I deleted the partitions in Win7 to start over, but now I can access BIOS again! WTH? Is there something about the boot sectors interfering with my ability to get into BIOS? I'm not dumb, I know the thing is isolated from the OS's and neither have any effect on it, but I'm at a loss here! I don't want to reinstall Ubuntu until I KNOW I can access BIOS after.

Thanks!

---

### Post by oldfred on 2013-08-11
Is your system newer and has UEFI, but Windows installed in BIOS mode? Since BIOS is really UEFI, you may have installed Ubuntu in UEFI mode? Both systems must be the same.

Best to only use Windows disk tools to shrink a Windows partition. And then use gparted for anything else.
You can use Boot-Repair to fix many boot issues or issue a link to a report we can use to analyze details.

Post this:
sudo parted -l

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

      
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by gabe2 on 2013-08-11
Thanks for responding. Actually, it's a hybrid EFI, although I looked up the BIOS version and they released a UEFI BIOS as of March, but I'm not too keen on flashing BIOS, especially a big one like that and I can't be sure I can flashback. I installed Ubuntu through a DVD at boot-up. I'll try installing it again and using Boot Repair if I still can't get into BIOS.

Actually, would it help if I reset BIOS to default before installing? Or optimized default, whichever...

*EDIT* Sorry, I just looked up what Gigabyte's "Touch BIOS" was...I DO NOT use that. I access BIOS the old-fashioned way, DEL key at POST and then the lovely blue screen set-up with various tweak options.

---

### Post by oldfred on 2013-08-11
What model motherboard?

 Upgrade Gigabyte to UEFI (Windows)
[http://www.youtube.com/watch?v=D-FcRUp2A-E](http://www.youtube.com/watch?v=D-FcRUp2A-E)
      
 Gigabytes P67 & H67 hybrid efi -Hybrid EFI is a UEFI based on the open source TianoCore
[http://www.rodsbooks.com/gb-hybrid-efi/](http://www.rodsbooks.com/gb-hybrid-efi/)
[http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html](http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html)
Gigabyte GA-X79-UD3 with I7-3820
Needed F6 to set ACPI=Off.and nomodeset
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB.

---

### Post by gabe2 on 2013-08-11
Z68X-UD3H-B3, rev 1.0. BIOS version is F10. I'd like to avoid updating the BIOS if I can. I'm about to run boot repair. Will return with an update.

---

### Post by gabe2 on 2013-08-11
OK, so I ran Boot Repair, it seems to have fixed the problem, thank goodness. I guess the issue had something to do with the boot sector and GRUB somehow. Thanks for the help.

---

### Post by oldfred on 2013-08-11
Glad you got it working. :)

---


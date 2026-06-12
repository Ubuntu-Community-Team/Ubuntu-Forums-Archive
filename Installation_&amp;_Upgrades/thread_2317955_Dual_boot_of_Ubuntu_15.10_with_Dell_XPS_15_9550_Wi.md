---
title: "Dual boot of Ubuntu 15.10 with Dell XPS 15 9550 Windows 10"
date: 2016-03-21
forum: Installation &amp; Upgrades
---

### Post by chaoticmoss on 2016-03-21
Dear Community,

I've spent all day trying to install Ubuntu 15.10 on a Dell XPS 15 9550 Windows 10 laptop. I created a USB live disk and the installation claims to have gone fine, but the boot list won't show it. When I boot back into the USB Ubuntu it recognizes that there is an Ubuntu installation there, but I can't seem to get in there. I ran Boot Repair and the record is here:
[COLOR=#000000][FONT=HelveticaNeue-Light]
[http://paste.ubuntu.com/15467995/](http://paste.ubuntu.com/15467995/)
[/FONT][/COLOR]
I'm a beginner and would like to learn Ubuntu but I gotta get in there! Thanks in advance for any help you can give me.

---

### Post by oldfred on 2016-03-21
Please review these threads for similar system and solutions to many issues.

 Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241)

---

### Post by chaoticmoss on 2016-03-21
The aforementioned threads are what I have been reading and trying for the past 8 hours, with the exception of the suggestion of un-checking SecureBoot in boot repair, which I did, generating this: 

[http://paste.ubuntu.com/15468459/](http://paste.ubuntu.com/15468459/)

The detail in those threads are what convinced me I could do this, as I'm using the same machine, but I am still unable to access Ubuntu. In fact, Windows Boot Manager is now the only item in my boot list. I used to have the hard drive listed there too (though it would also take me to Windows), but now that's gone.

Does anyone know why this could be?

---

### Post by Rommel_Lapuz on 2016-03-22
Try updating the bios again. Or manually assign the bios to boot on the grub.efi. Let me know if that's okay

---

### Post by chaoticmoss on 2016-03-22
> **Rommel_Lapuz said:**
> Try updating the bios again. Or manually assign the bios to boot on the grub.efi. Let me know if that's okay

Manual assignment worked!!! THANK YOU ROMMEL_Lapuz!!! :D

---


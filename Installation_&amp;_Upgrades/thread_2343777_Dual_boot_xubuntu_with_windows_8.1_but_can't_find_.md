---
title: "Dual boot xubuntu with windows 8.1 but can't find windows now"
date: 2016-11-19
forum: Installation &amp; Upgrades
---

### Post by kood on 2016-11-19
Not sure if I've screwed up anything. I was trying to dual boot xubuntu with windows 8.1. Made live cd 16.06LTS desktop amd64 with rufus. As my windows 8 is booting in legancy mode, so I guess I was using the same bios setup for live cd (or not?). Now i'm only able to boot in Ubuntu and my windows 8 selection blue screen has gone, any help would be much appreciated.

here is the link for boot-repair
 
[http://paste2.org/ZDAU06az](http://paste2.org/ZDAU06az)

by browsing through [http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
my best guess is i had selected wrong option for "device for boot loader installation"

Any work around on this?

Thanks

---

### Post by Bucky Ball on 2016-11-19
Welcome. You may want to try this before digging deeper. Open a terminal and paste in this command:

```
sudo update-grub
```

You will be asked for your password after you hit enter. It will be invisible. This is normal.

Reboot. Are you seeing Windows in the list of boot options in the grub menu?

Two things:

1 Are you seeing a list of OSs to boot when you boot the machine? If not, I think hitting escape (or shift) just after boot should get you to one.
2 Was Windows booting and functioning normally before you installed Ubuntu?

The bottom line, and it sounds like you figured it out, is that Ubuntu needs to be installed in the same mode as Windows. When you were installing there may have been two entries for the install media (but if you don't have an EFI BIOS then not sure if there would). One would have [EFI] or [UEFI] or something next to it. The Ubuntu installer has the facility to install in either EFI or BIOS so you need to choose the right one.

If that is the case, reinstall and choose the one without [efi] and you should be good to go. Should be ...

Having said that, don't see that there's an EFI partition on your drive.

PS: Just to confuse matters, on closer inspection it looks like you have Win7 and 8 installed on that drive.

```
sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  [B]According to the info in the boot sector, sda5 starts 
                       at sector 2048.[/B]
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD
```

The part in bold is problematic.

---

### Post by kood on 2016-11-19
Hi Bucky Ball, that update-grub works like a champ. This machine was installed with Win7 and then later upgraded to Win8. Thanks again

---

### Post by Bucky Ball on 2016-11-19
Excellent news! Yea, still a bit concerned about that sda5, though, but if it's no longer used Win7 you could always delete.

If everything's working, what the hey? Enjoy and thanks for marking as solved and sharing what fixed it. :)

Just a thought. You are positive, then, that when you boot to Windows you are not booting to that sda5 install of Win7? You write this:

> This machine was installed with Win7 and then later upgraded to Win8.

... and I'm presuming it was installed with Win7 and you clean installed Win8 on another partition rather than upgrading the existing Win7 to Win8 which is why you have two Win installs currently? Just wondering. :)

---


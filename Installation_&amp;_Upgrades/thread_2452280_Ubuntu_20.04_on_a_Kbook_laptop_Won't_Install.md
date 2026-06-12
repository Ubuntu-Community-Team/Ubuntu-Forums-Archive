---
title: "Ubuntu 20.04 on a Kbook laptop Won't Install"
date: 2020-10-19
forum: Installation &amp; Upgrades
---

### Post by DalkeGeedz on 2020-10-19
Trying to install Ubuntu 20.04 Desktop on a Kbook Pro laptop. Fresh out of the box, it finished its Windows setup (which was kept from updating with no internet connection). Then, shut it down in order to boot from the startup disk image of Ubuntu on USB.

If there is a hotkey to trigger the BIOS menu for the machine, I can't figure it out. (Escape, delete, F1, F2 & combinations of those with Alt -- nothing.) But I *could* access it in Windows using Settings > Update & Security > Recovery > Advanced startup > Troubleshoot > Advanced options > UEFI Firmware Settings > Restart -- which, finally, reboots into the "Aptio Setup Utility" which says the AMI BIOS version is AN12V 1.01 x64.

Under the "Boot" tab of the BIOS menu, there *is* an entry to change the Boot Option. The USB has to be plugged in for it to be recognized and appear in the menu though, but once that's all complete, it does seem to boot from the USB, as it shows the GNU GRUB 2.04 menu.

The GRUB menu has five options: Ubuntu; Ubuntu (safe graphics); OEM install (for manufacturers); Boot from next volume; UEFI Firmware Settings. I've tried the first three with two different USB sticks, and in all cases the screen simply goes black and stays that way for about 10 minutes until I figure it isn't working and shut it down.

I have no idea how UEFI works, haven't used Windows in well over a decade and just want to allow Ubuntu full reign on the computer -- not only do I not want to dual boot, I'd be thrilled if all traces of Microsoft can be removed from the machine. But I have little idea what I'm doing at this point, don't want to brick the laptop and am not sure what to try next.

Any thoughts? Happy to try anything I haven't thought of. A third USB stick? Network install? Is there something I should be doing in Windows to stop it from seemingly not letting go of the boot manager?

---

### Post by grahammechanical on 2020-10-19
This wiki page is old but I am sure that the information is relevant. Note the sections called: Case When Ubuntu Must Be Installed in UEFI Mode and General Principles.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards

---

### Post by CelticWarrior on 2020-10-20
Before installing Ubuntu only please take a moment to update the motherboard's firmware (UEFI) and, eventually, SSD's firmware (all that are applicable) as more often than not vendors provide those updates as Windows executable files only.  

Furthermore, yours is likelyn to use ESC to access UEFI settings but you must press (and spam it) immediately after pressing the power button. Alternatively it may work with FN+F2 (not ALT or CTRL like you've already tried). Again, whatever the key or combo required, it must be used immediately after powering on.

---

### Post by DalkeGeedz on 2020-10-25
Ok, first of all, thank you CelticWarrior for FN+F2. That was the correct combo. Having to use Windows just to access the BIOS utility made this too frustrating to troubleshoot.

Now that I've had a good look at the UEFI link above, and a way to more quickly boot from a USB, let me more simply describe the current setup and problem:

[LIST]
[*]I created a bootable USB using Startup Disk Creator and the ISO downloaded from the site, "ubuntu-20.04.1-desktop-amd64.iso" (using a separate Ubuntu laptop).
[*]In the BIOS utility, the Fast Boot option is set to "Disable". (There is no option for "legacy" or "csm" or "bios".)
[*]Using 'boot override' from the BIOS utility does load the GNU GRUB menu (v.2.04) and offers five options:
[LIST]
[*]Ubuntu
[*]Ubuntu (safe graphics)
[*]OEM install (for manufacturers)
[*]Boot from next volume
[*]UEFI Firmware settings
[/LIST]
[/LIST]
From here, I've tried the first three options (multiple times, with different USB sticks) and nothing seems to happen. The screen dims, and the system just hangs. (Figure after five minutes it should do something, but the screen doesn't even flicker.)

Anyway, with only a black screen it's hard to diagnose anything further. Any suggestions or ideas appreciated. I didn't see anything on the UEFI page (linked above) that would seem to be the issue. I'd be happy to do a dual boot just to keep the ability to access future BIOS update; I just want functioning Ubuntu on the machine. Maybe try 18.04?

---

### Post by kc1di on 2020-10-25
what is the video card in that machine?

---

### Post by DalkeGeedz on 2020-10-25
Just an "Intel HD Graphics" chip on the board, I'm not sure of the specifics.

_Update_: I did try **18.04** and (after a couple of tries) ***it worked***. And after reading through some threads here, it might be a wise idea to stick with 18 for awhile. Don't know if that merits marking this "solved" but I'm not going to push the effort. (The newer version would be nice, but I've got 2.5 years before 18.04's EOL and don't necessarily expect this laptop to survive that long.)

---

### Post by kc1di on 2020-10-25
Well if it works with 18.04 I'd stick with that :)

---


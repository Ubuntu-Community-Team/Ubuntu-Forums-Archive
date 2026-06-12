---
title: "Trouble installing Xubuntu 14.04 on Toshiba Satellite P55-A (UEFI)"
date: 2014-10-06
forum: Installation &amp; Upgrades
---

### Post by Steve_Nims on 2014-10-06
Have tried installing Xubuntu 14.04 from liveusb to my laptop, a Toshiba Satellite P55-A, with no success. Have been able to install Arch linux utilizing gummiboot without any issues.

Note: Have chosen to make new partition table, and overwrite entire disk on install, vs. installing alongside Arch.

Installer boots in EFI mode as verified by ```
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
```

Secureboot is off, fastboot is off, boot in EFI mode is on, boot order is HDD, CD-ROM, USB.

Install completes fine, but when I restart only this message is displayed: "Reboot and select proper Boot device or Insert Boot Media in selected Boot device and press a key" and nothing happens. Have to shut down and start up to get to a point where I can either boot back in to the liveusb or go into the America Megatrends settings.

Tried boot-repair, but it says it encountered an error, and to come here with this url: [http://paste.ubuntu.com/8507172/](http://paste.ubuntu.com/8507172/)

---

### Post by oldfred on 2014-10-06
Boot-Repair picks up some misc errors and reports that in the summary. But grub reinstalled ok. Exit code of 0 is no error.

 Reinstall the GRUB of sda2 into the MBR of sda
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

But some systems only boot Windows from UEFI. Can you from one time boot key, often f12 but varies boot ubuntu entry?

For systems that only boot Windows if booting Windows also, we rename bootx64.efi in /efi/Boot, but if you do not have Windows at all we an create a Windows efi folder and copy grub (secure boot off) or shim(secure boot) into it and rename it to be bootmfgw.efi or the Windows boot file. UEFI thinks it boots Windows but really boots grub.

The bootx64.efi was a default boot for removeable devices, but the newest UEFI spec update allows that for hard drives also.

You only have the ubuntu folder, but this is typical:

 /EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu

      Ubuntu only on HP, recreate Windows folder and grub as Windows boot file
[http://ubuntuforums.org/showthread.php?t=2238714](http://ubuntuforums.org/showthread.php?t=2238714)
    From live installer mount the efi partition on hard drive:
    mount /dev/sda1 /mnt
    cd /mnt/EFI

       use ls to see if created correctly
    ls -l
    mkdir Microsoft
    mkdir Microsoft/Boot
    cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmfgw.efi 

and/or:

 From live installer mount the efi partition on hard drive:
mount /dev/sda1 /mnt
mkdir /mnt/EFI/BOOT
cp /mnt/EFI/ubuntu/* /mnt/EFI/BOOT
mv /mnt/EFI/BOOT/grubx64.efi /mnt/EFI/BOOT/bootx64.efi

With newer larger hard drives I normally suggest a smaller / (root) partition of 20 or 25GB and use rest of drive as /home or data partition(s).

---

### Post by Steve_Nims on 2014-10-06
YES!

YESSSSSSSS!!!!!!!


YESSSSSSSSSSSSSSSSSSSSSSSS!!!!!!!!!

In other words, it worked. This can be marked as solved!

---

### Post by oldfred on 2014-10-06
Glad it worked. :)

But which of the suggestions did you try, so others can find this thread and know what works.

---

### Post by Steve_Nims on 2014-10-07
I added both folders and copied the efi file to both then restarted and voila! If I ever get around to removing one folder, then the other to see which actually made the difference I'll come back here to report. My issue now is my system seems to freeze when waking from suspend/resume (don't know which). I can move the mouse around, but no button clicks seem to be registered, and typing doesn't work either. Couldn't switch to a VT to try to trouble shoot either. Performed a hard restart and all is back to working again. Not sure if this goes in this forum or elsewhere...

---

### Post by oldfred on 2014-10-07
I have seen many issues on hibernation which is not recommended and some posts on suspend/sleep which does work on my system so I have not followed those threads. If you cannot find a thread with a solution that works, start a new thread with that issue in title along with your model again.

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[xhttp://kember.net/articles/reisub-the-gentle-linux-restart/](xhttp://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---


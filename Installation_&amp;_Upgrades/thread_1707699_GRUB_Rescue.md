---
title: "GRUB Rescue"
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by 2uRcJQ34G1 on 2011-03-15
Hiya,

So here is what happend: I installed Ubuntu on a USB from a LIVE USB using my laptop. My laptop has Windows 7 on it. I don't want anything to happen to my laptop, but for some reason once I finished installing a removing both the USBs from their ports- the GRUB Rescue showed up. The normal Windows 7 boot does not take place, unless I put my Ubuntu USB in and then choose Windows 7 from the GRUB Menu. How do I get rid of this, so that my computer returns to normal functioning, i.e. the windows 7 should run by default and no GRUBs looking for a Ubuntu disk??

Cheers, any help appreciated.

---

### Post by 2uRcJQ34G1 on 2011-03-15
Can I uninstall GRUB?

---

### Post by drs305 on 2011-03-15
To restore Windows, from Ubuntu, run the following commands. I'll assume "sda" is your Windows drive:

```
sudo apt-get install lilo
sudo lilo -M lilo MBR
```
Don't run any other lilo commands.

This will once again point the sda MBR to your Windows boot files. If you want to boot Windows, don't insert the USB drives.

The way your BIOS is probably set up, it will boot the USB drive first, where it finds Grub2. With the change above, if the USBs are not inserted, BIOS should revert to booting sda, on which your Windows files are located during boot.

To make sure Grub2 is still on the USB drive and looking for the Ubuntu boot files:  
Boot Ubuntu from your USB drive.
Identify the USB drive with Ubuntu, then make sure Grub2 is installed to the USB MBR by running the following (replace X with the drive designation):
```
sudo grub-install /dev/sd**X**  # X being the non-Windows USB drive (sdb, etc)

```

---

### Post by 2uRcJQ34G1 on 2011-03-15
Hiya mate,

Thanks for reply, I haven't tried it but I found another way:

Run Windows Installation/Upgrade disk->Repair Windows->Run Terminal
then run the following command:
Bootrec.exe /FixMbr
then restart
et Voila!

All better!

Cheers to all for trying!

---

### Post by matsamune on 2011-04-04
> **gore_grinder said:**
> Hiya mate,

Thanks for reply, I haven't tried it but I found another way:

Run Windows Installation/Upgrade disk->Repair Windows->Run Terminal
then run the following command:
Bootrec.exe /FixMbr
then restart
et Voila!

All better!

Cheers to all for trying!

Thank you so much!! This worked perfectly for me :D

---


---
title: "Duel Boot Ubuntu Windows 10 - GRUB issue, no grub menu only straight to Ubuntu"
date: 2017-01-18
forum: Installation &amp; Upgrades
---

### Post by mivankovic on 2017-01-18
Hi Guys,
Have not used ubuntu for years, back on the train and would appreciate some help.

My problem is my PC directly boots to Ubuntu and gives no option or GRUB menu.

My sequence of events were:
Install windows 10 (create unallocated partition for Ubuntu)
Install Ubuntu with Rufus - (install ubuntu alongside win 10 option)
Grub error in boot (error: no such device entering rescue mode)
Reinstalled Ubuntu - now (install ubuntu alongside 'other operating systems')
Fixed error but no grub just boots straight to Ubuntu 
Installed boot-repair distribution with Rufus and ran Boot-repair (no change)

Please help as i have ran out of options

Many thanks in advance

---

### Post by laurent85 on 2017-01-18
Boot a usb live session and open a terminal,

install boot-info:
```

sudo add-apt-repository ppa:yannubuntu/boot-repair
apt update
apt install -y --install-recommends boot-info
```
generate report and provide the online link:```
boot-info
```

---

### Post by yancek on 2017-01-18
You haven't indicated whether you installed windows 10 UEFI or MBR.  The same for Ubuntu.  They need to be the same or the result you get is what you have.  You might be better off using the manual (Something Else) option in the installer rather than the auto-install (Install Alongside) option.  Posting the boot repair output should answer these  questions.  You might also take a look at the Ubuntu documentation on UEFI dual boot below which is pretty detailed.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by mivankovic on 2017-01-19
Thanks laurent85 and yancek, much appreciated for the help and time

[COLOR=#000000][FONT=Arial]http://paste2.org/GJXFkdAY is the report

*Please note i only use windows 10 (and ubuntu hopefully again) on the 250GB SSD, other disks do have operating systems as from old computers

I would assume MBR as its a older computer but its out of my depth. I have old megatrends bios too

Thank you again in advance



[/FONT][/COLOR]

---

### Post by Bucky Ball on 2017-01-19
Have you tried the straightforward approach which just might work? Open a terminal and:

```
sudo update-grub
```

Then reboot. Also, it may be that the grub screen is hidden on boot. Just after boot and the splash before Ubuntu boots, hit the shift key (or you may need escape) and the grub list should pop up. Is Windows on it?

Your boot repair output is also showing you have some 'issues' which would need to be fixed. You have grub installed on sda5 as well as the MBR of sda.

You also have this:
```

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   ntfs-3g-mount: mount failed: Device or resource busy
ntfs-3g-mount: mount failed: Device or resource busy 
```

Is Windows hibernating? Ubuntu will never see it if so. And this:

```
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```

Issues. :-k Hopefully another helper can work through them with you as beyond my skill set.

PS: As mentioned by Yancek; I too would recommend the 'Something Else' option. Less problematic and less chance of obliterating Windows. You also need to make sure Windows is not hibernating.

---

### Post by laurent85 on 2017-01-19
Don't now much about fake raid but does not seem you need it, check your bios settings and disable the motherboard raid feature. Check the boot order settings and select 256GB drive as the boot disk.

Boot-repair also reports inconsistencies with 500GB hard disks sdb and sdc. 

Uninstall the dmraid package from Ubuntu :
```
sudo apt purge dmraid
```

And update-grub :
```
sudo update-grub
```

---

### Post by mivankovic on 2017-01-20
Thanks guys, really appreciate the help

Have tried both commands, now i can see my other HDD (files)

Still boots to Ubuntu no Grub

have set the 240G drive to boot 1st priority
 
Have trued pressing shift and also esc but no success

Any other ideas? Much love in advance
Thanks

P.S also if this helps 

[COLOR=#000000][FONT=Arial]Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Disklabel type: dos[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Disk identifier: 0x6dd89dc8[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Device [/FONT][/COLOR][COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Boot [/FONT][/COLOR][COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Start   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]End   Sectors   Size Id Type[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda1  *     [/FONT][/COLOR][COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]2048 469041151 469039104 223.7G  7 HPFS/NTFS/exFAT[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda2   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]487473152 488394751[/FONT][/COLOR][COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]921600   450M 27 Hidden NTFS WinRE[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda3   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]469043198 487473151  18429954   8.8G  5 Extended[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda5   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]469043200 479088639  10045440   4.8G 83 Linux[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda6   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]479090688 487473151   8382464 [/FONT][/COLOR][COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]4G 82 Linux swap / Solaris[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Partition table entries are not in disk order.[/FONT][/COLOR]

---

### Post by yancek on 2017-01-20
The bootinfoscript output shows you have both windows 10 and Ubuntu installed MBR and Grub in the MBR.  It also shows the core.img file as being in the correct location and you have correct entries for Ubuntu and windows 10 in the grub.cfg file for Ubuntu.  Most likely possibilities are pointed out by Bucky Ball above.  Either windows is hibernated or it's filesystem is corrupt.  You can't repair that from Ubuntu or any other Linux.  You should be able to run chkdsk from the windows installation device and make sure any reference to fastboot or hibernation is off in the BIOS.

---

### Post by mivankovic on 2017-01-27
Hi Guys,
THanks for the replys. 

What i have done:
- fixed MBR / boot through windows usb
- got to boot back to windows as per before
- turned off fast boot and hibernate options 
- used ubuntu live and installed boot-repair, run 
- ended up in same where it just boots to ubuntu straight (back to the start problem)

Im really not sure what to do now, when boot-repair asks where to install grub it should only be on the partition which ubuntu is on correct?

Any other help will be greatly appreciated, i really dont understand what other options i have now

THanks guys

---

### Post by Bucky Ball on 2017-01-27
> **mivankovic said:**
> Im really not sure what to do now, when boot-repair asks where to install grub it should only be on the partition which ubuntu is on correct?

Wrong. In most situations, the grub should be on sda, NOT a partition. Use Boot Repair to install it there or:

```
sudo grub-install /dev/sda
```

Might be an idea to run the bootinfo and post the link again, though, so we can see what you have there now, but grub should be on sda for your setup (Windows and Ubuntu). Read this for further info:
> 
Please select: 
* either the disk (eg /dev/sdX, not /dev/sdXY) on which the BIOS is setup to boot (recommended for normal use) 
* OR the partition (eg /dev/sdXY, not /dev/sdX) on which Ubuntu (/boot, else /) will be installed (only if you want to chainload it from another bootloader; if any doubt, do NOT choose this)

From [here]("https://help.ubuntu.com/community/Grub2/Installing#GRUB_2_Initial_Installation"). You do not want to chainload Ubuntu from another bootloader (grub on the partition), you want to chainload Windows to grub (grub on the MBR of sda). You want option 1 above if that is the case, and appears it is. ;)

---


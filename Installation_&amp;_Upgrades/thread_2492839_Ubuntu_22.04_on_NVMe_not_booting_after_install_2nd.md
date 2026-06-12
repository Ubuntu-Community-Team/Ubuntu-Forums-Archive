---
title: "Ubuntu 22.04 on NVMe not booting after install 2nd ubuntu on SSD"
date: 2023-11-24
forum: Installation &amp; Upgrades
---

### Post by chrilei on 2023-11-24
Hello everyone, please help.
I had a working Ubuntu 22.04 (main partition encrypted with LUKS) installed on a NVMe. Now I wanted to install an additional Ubuntu 22.04 on a 2nd hard disk (SSD via SATA), which I wanted to use for backups instead of the live USB stick. Since this installation, I can no longer boot my Ubuntu on the NVMe. I get a GRUB terminal (minimal bash line) immediately after the bios. I have now created a report according to the instructions under Boot-Repair. Can someone please tell me if I can run the boot repair to fix the problem or what I should do best. Any advice on how to get the system up and running again would be appreciated.
Many thanks Chrilei

---

### Post by oldfred on 2023-11-24
Please post Boot-Repair report as link to paste bin as recommended.
Some here will not download unknown files for security reasons.

It looks like your default UEFI boot entry uses a GUID/partition UUID that is different than the ESP on NVMe drive.

Some systems change boot order when drive added. Depends on SATA port number. Not sure when mix of SATA & NVMe drives, which UEFI considers as first. My system shows NVMe drive as first, but Ubuntu shows it as last.

And many systems disable a SATA port to use NVMe drive. So if you plugged in new SATA drive into wrong port you may have disabled NMVe drive. Check manual and port actually used.

You may be able to use Boot-Repair's advanced mode to choose drive and full reinstall of grub.

---

### Post by chrilei on 2023-11-24
Thanks oldfred, for the quick feedback. I have again created a BootInfo summary including the SATA SSD and provide it via l[COLOR=#000000]ink to paste bin, as[/COLOR] suggested (thanks for the info).
I somehow have the feeling that the boot partition of the NVMe has been overwritten by the install and that now the boot partition is on the NVMe and the remaining partitions are used by the SATA. Can this be the case or does this make sense?

[https://paste.ubuntu.com/p/wDqDg6XDry/](https://paste.ubuntu.com/p/wDqDg6XDry/)

Thanks Chrilei

---

### Post by tea for one on 2023-11-24
> **chrilei said:**
> I had a working Ubuntu 22.04 (main partition encrypted with LUKS) installed on a NVMe. Now I wanted to install an additional Ubuntu 22.04 on a 2nd hard disk (SSD via SATA), which I wanted to use for backups instead of the live USB stick.
You really do not need a second full installation of Ubuntu 22.04 for backup purposes.

What do you want to backup?
Personal data in your user directory?
An image of your OS?

---

### Post by MAFoElffen on 2023-11-25
Dang... Your system is UEFI right? Your first report showed nothing in the MBR's of both disks, and booted as UEFI. This last one had Grub installed as Legacy Boot, and booted a Legacy. It, unfortunately, it just took a step backwards...

After you boot something on that via USB, please ensure it is booted in UEFI mode. If this is present
```

[ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"

```
then it is booted in UEFI mode, else Legacy Boot mode...

EDIT:
@oldfred --- I messaged Yann about adding another test for this in the Boot Repair disk. To add a prompt to indicated to the user which boot mode the disk is booted in, but also match it against if the installed system has an ESP present 'somewhere'... So later, if they go into advanced mode for a repair: If booted as Legacy, with a present ESP, throw a warning, asking the user if they really want to be there in that mode. 

This is coming up too often lately.

---

### Post by chrilei on 2023-11-25
Yes, the system is UEFI. I ran the code and it shows that it is booted in legacy mode.
Unfortunately I'm not available for the next few hours... will try to boot in UEFI later... thanks.


@tea for one, would like to clone the entire system. I know I don't need an installed version to do this. Just thought it would make it easier in the future. Thank you.

---

### Post by tea for one on 2023-11-25
> **chrilei said:**
> would like to clone the entire system
One advantage of cloning an entire Ubuntu system is that you can test it (without restoring it to its original disk)

Clonezilla live session
Device > device 
Partition > partition

nvme to nvme using usb-c
512M  ESP
30G part ext4  /System
31G part ext4  /home
3 partitions took about 12 minutes 
Remove source disk and check if cloned disk boots

I have also used Gparted (copy and paste partitions) via a live "Try Ubuntu" session.
After isolating the source disk, the target disk booted successfully.

The time will depend on your partition sizes and usb connection speeds

---

### Post by chrilei on 2023-11-25
I clone with dd. But that's off topic here...

---

### Post by oldfred on 2023-11-25
If you have booted live installer in UEFI mode, which you should always do, can you run Boot-Repair's reinstall of grub.
You may need to use its advanced mode to choose drive.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

I do not clone, nor suggest it normally. And almost never use dd as its nickname is "Data Destroyer", any typo in command totally erases data that then is not recoverable. 

I always suggest new clean install and restore from backup. Ubuntu is relatively easy to install. And rsync of data is also quick unless you have TB of data. For me, even with fast Internet download of apps is longest part of install and total time of install is about an hour.

With UEFI system, you always want to boot in UEFI mode. And most systems now are UEFI, since Microsoft required UEFI with gpt partitioning in 2012 with release of Windows 8. Older BIOS only systems and maybe low end early UEFI systems may be better with lightweight flavor as full Ubuntu with gnome expects a newer system.

---

### Post by chrilei on 2023-11-25
Had to laugh briefly because of the dd nickname... will think about this strategy again.

What I have done now.

1. "Compatibility Support Module" deactivated
2. Booted live installer and checked for UEFI mode
3. Unlocked LUKS partition
4. Started boot-repair with selected drives in advanced mode to reinstall GRUB. Followed the boot-repair instructions

At the end of the process I got the error.
Error: NVram is locked (Ubuntu not found in efibootmgr).
[https://paste.ubuntu.com/p/bJ84DZ2hGB/](https://paste.ubuntu.com/p/bJ84DZ2hGB/)

Than.

1. Deactivated the "Secure Boot"
2. Booted live installer in UEFI mode
3. Unlocked LUKS partition
4. Started boot-repair with selected drives in advanced mode to reinstall GRUB. Followed the boot-repair instructions

But again same error.
Error: NVram is locked (Ubuntu not found in efibootmgr).
[https://paste.ubuntu.com/p/Zc75FQw5W2/](https://paste.ubuntu.com/p/Zc75FQw5W2/)

Then I tried to boot the system and thanks to ubuntu forum community and boot-repair it started without any problems.

Should I make any further changes or adjustments because of the error?

Many thanks to everyone for the great support. It's not always the case that a newbie gets such good support. Thumbs up.
Now I'm going to treat myself to a beer...

---

### Post by oldfred on 2023-11-25
I think it is booting from the old UEFI entry?
But as long as it works that is great.

We are seeing more complaints about the locked NVRAM issue. 
And there does not seem to be one solutions. Varies by vendor.
Some have separate UEFI security settings to prevent changes to UEFI, others just see to change some setting somewhere & it works.

Locked-NVram
[https://askubuntu.com/questions/1488426/trying-to-reinstall-grub-after-windows-update-messed-it-up](https://askubuntu.com/questions/1488426/trying-to-reinstall-grub-after-windows-update-messed-it-up) & 
[https://ubuntuforums.org/showthread.php?t=2491460](https://ubuntuforums.org/showthread.php?t=2491460)  &
[https://ubuntuforums.org/showthread.php?t=2482909](https://ubuntuforums.org/showthread.php?t=2482909)
[https://ubuntuforums.org/showthread.php?t=2490084](https://ubuntuforums.org/showthread.php?t=2490084)
Locked NVRAM - turning on Secure boot & reset UEFI Dell XPS 9530
[https://ubuntuforums.org/showthread.php?t=2490359](https://ubuntuforums.org/showthread.php?t=2490359)
Locked UEFI/BIOS setting: Lenovo UEFI screen
[https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg](https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg)

---

### Post by chrilei on 2023-11-27
Will check the links and mark the thread as resolved.

oldfred, thanks for everything.

---


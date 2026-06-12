---
title: "Boot issue when removing SATA drive"
date: 2024-01-31
forum: Installation &amp; Upgrades
---

### Post by theslider on 2024-01-31
Hi,

My laptop has a dual boot linux + windows on the NVMe SSD and I've been trying to replace the secondary drive which is a Samsung evo 870 SSD in the sata port for a different one.
The issue is that the laptop refuses to boot if I either remove the SATA drive or replace it and starts displaying an empty grub menu.

If I dare change the boot order to the NVMe drive, the laptop restarts during boot with an error message. I'm suspecting an EFI issue but i'm not sure.
When I replace the old drive, It boots again with no problem and displays the proper grub menu.

Someone sugested using boot repair. I did so by booting off the USB drive : [http://*******.us/pw88Jz](http://*******.us/pw88Jz)
This report is without the SATA drive.

Regards,

---

### Post by tea for one on 2024-01-31
[COLOR="#000080"]Line 63-65[/COLOR] - 1 OS detected OS#1:   Windows 10 or 11 on nvme0n1p3
Only Windows is visible to boot-repair

[COLOR="#000080"]Line 185[/COLOR] - /dev/nvme0n1p5     907.2G   0% 
This is an ext4 partition with zero content 

No sign of Ubuntu on your nvme disk.

If you are still unable to boot the Windows OS on your nvme disk, you'll need to use Windows repair tools to fix the boot manager.

If you run the report again with both disks attached, it may yield more pertinent info?

---

### Post by theslider on 2024-02-01
Hi,

Thank you for taking the time to look at the report. I though that Linux was hidden in the EXT4 partition, I never thought it could be missing.
Here is the report with the original SATA drive inserted :
[http://*******.us/AANsF2](http://*******.us/AANsF2)

And just looking at that by myself I can see the mistake. It seems grub and Linux were installed onto the SATA drive instead of the NVMe. What a mess...
Is the perhaps a way to move them to the NVMe drive or should I bite the bullet and start over ?

Regards

---

### Post by tea for one on 2024-02-01
[COLOR="#0000FF"]Line 5[/COLOR] - Windows is installed in the MBR of /dev/nvme0n1.
[COLOR="#0000FF"]Line 6[/COLOR] - Windows is installed in the MBR of /dev/sda.
For a robust dual boot system, these lines should not appear in a boot-repair report.
They sometimes appear when Windows has been updated from an original legacy system.

[COLOR="#0000FF"]LIne 75[/COLOR] - Operating System:  Linux Mint 21.2
It would have better to have mentioned this in your original post
> Is the perhaps a way to move them to the NVMe drive or should I bite the bullet and start over ?
I wouldn't move anything, I would take more radical action for future-proofing and boot independence. 
Each OS on a separate disk with its own ESP

My advice is:-
Backup all your data
Install Windows 10/11 in UEFI mode on your preferred disk
Restore your Windows data and double check whatever you feel needs attention

Isolate, de-activate or remove the Windows disk.
Attach your virgin disk (as mentioned in post 1)
Boot into Ubuntu live session in UEFI mode
Create GPT partition table
Install Ubuntu (I know you use Linux Mint but you will have to indulge my flippancy - this is an Ubuntu forum)
Make sure that an ESP is created
Restore data and check all is OK

You can adjust Grub subsequently to pick up Windows if you wish

Each disk should now boot independently of the other.

---

### Post by theslider on 2024-02-02
Hi,

Thank you for the tips. I don't understand the Ubuntu/Mint thing. Are they so different that the boot repair tool wouldn't help ?
In any case I really can't have an OS take over the entire disk. I need them on the NVMe drive as I'll be frequently swapping SATA drives.

I guess I'll just remove it and reinstall the OS's which is a bummer.

Thanks for the help.

---

### Post by tea for one on 2024-02-02
> **theslider said:**
> Thank you for the tips. I don't understand the Ubuntu/Mint thing. Are they so different that the boot repair tool wouldn't help ?
I don't think that they are so different and I'm pretty sure boot-repair would be useful for Mint users.
It's just that, often when trying to help, details matter.
Ubuntu Forums have a dedicated page for Mint users here [https://ubuntuforums.org/forumdisplay.php?f=453](https://ubuntuforums.org/forumdisplay.php?f=453)
> In any case I really can't have an OS take over the entire disk. I need them on the NVMe drive as I'll be frequently swapping SATA drives.
Understood - just make sure that both systems are installed in UEFI mode with GPT
> I guess I'll just remove it and reinstall the OS's which is a bummer.
Yes, it can be a tortuous process, but, practice makes perfect ;)

---

### Post by theslider on 2024-02-07
Hey,

I just wanted to thank you again for taking the time to provide help.
I managed to get my system setup up as I needed and It's working fine now.

As for the forum use, I had just followed the link from the page here : help.ubuntu.com/community/Boot-Repair . I didn't think for a second that there would be sub forums but i'll make sure to specify the main distro next time.
Thanks again.

Regards,

---


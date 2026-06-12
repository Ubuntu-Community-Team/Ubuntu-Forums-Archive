---
title: "Solved - Installation problems - 20.04.1 LTS"
date: 2021-01-20
forum: Installation &amp; Upgrades
---

### Post by pbd1978 on 2021-01-20
Motherboard - ASUS Z97-Pro Wifi AC - [https://dlcdnets.asus.com/pub/ASUS/mb/LGA1150/Z97-PRO/E9062_Z97-PRO.pdf](https://dlcdnets.asus.com/pub/ASUS/mb/LGA1150/Z97-PRO/E9062_Z97-PRO.pdf)

I've been running Windows 7 on a 120 GB Samsung SSD with 4 x 4 TB WD HDD (RAID5) for my data drives. I decided to give Ubuntu a try so I attempted to boot from a USB flash drive. The installation would stall with the error message "AHCI Controller Unavailable". If I disable the ASmedia controller in the BIOS (which the Samsung SSD uses) I'm able to boot but I now I can't see the SSD I'd like to install Ubuntu on. Any idea how I can get around this?

Thanks

---

### Post by yancek on 2021-01-20
Just a couple of guesses as I haven't used windows 7 in years.  Do you have windows 7 hibernated or are you using Dynamic disks.  Do you see the other drives?  Also, you are not using the unsupported and insecure windows 7 on the internet??

---

### Post by pbd1978 on 2021-01-20
I see 2 of the 4 HDD. I don't recall using dynamic disks. I think it's a legit copy of Windows 7.

---

### Post by CelticWarrior on 2021-01-20
Windows 7 is out of support for quite some time now. Legit or not it doesn't matter, it shouldn't be used if connected to the internet, that was the point of the previous comment.
If you need Windows then install Windows 10 but before that change BIOS/UEFI settings, drive mode to AHCI, then install Windows 10 and Ubuntu in dual-boot or just Ubuntu. That's all.

---

### Post by pbd1978 on 2021-01-20
I don't need Windows. The entire point of the exercise is to get away from Windows because it's so old and running Ubuntu. I mentioned that I'm currently running Windows 7 just in case it was relevant to the problem I'm trying to solve. The box was an HTPC that hasn't been connected to the internet for at least a couple years. If anyone can help with the SSD problem I mentioned previously I'd really appreciate it.

---

### Post by CelticWarrior on 2021-01-20
> [COLOR=#000000]I don't need Windows.[/COLOR]
Great. Excellent news.
This being the case pretty much all you need to now I already explained in the previous post. Exactly which part didn't you understand?

---

### Post by pbd1978 on 2021-01-20
Unfortunately I've already changed the drive mode to AHCI. Unless I disable ASMedia controller I can't get Ubuntu to boot. The problem is that if I disable ASMedia in BIOS I can boot but I'm unable to see the SSD as an option to install to. Apologies if I'm being unclear on what I'm seeing.

---

### Post by CelticWarrior on 2021-01-20
The ASMedia controller is a SATA controller. It has nothing to do with booting external media. What happened (maybe) is whatever drive connected to it has the first boot priority so it does just that, it boots; in its absence (disabled) the next in line, the USB (maybe) then boots. Now, if you explicitly select to boot from the USB, either in the one-time boot menu or in the UEFI boot menu, it must boot. I suspect that you aren't doing that, are you?

---

### Post by pbd1978 on 2021-01-20
I'm setting the USB flash drive as the primary. I've removed all other secondary/tertiary options so only the USB drive is available. Unfortunately, despite doing that, every time I attempt to boot from the USB flash drive it fails with "AHCI Controller Unavailable" unless I disable the ASMedia storage controller in the BIOS.

---

### Post by CelticWarrior on 2021-01-20
First of all, your motherboard has UEFI. If you made the USB in Windows with Rufus then there's a very good chance that it only boots in Legacy/CSM mode and you don't want that. Typically, with Rufus, users have to explicitly select UEFI/GPT option before burning the ISO. Or, if you actually used those options it only boots in UEFI mode and your current settings, likely due to Windows 7, are set to Legacy/CSM.

So, please pay special attention to the bold parts ahead...

First thing is to redo the USB. Use Balena Etcher this time for a fool-proof result that boots in BIOS or UEFI mode, even if you actually want the latter only.

Then set SATA drive mode to AHCI (p. 3-38 of the user's manual). This may or may not imply undoing any RAID configuration you may have. **But if you have some RAID configuration already** then I'm sorry to say this, you need to know a lot more than what you're showing here to properly manage that system. If you have such configuration then **likely you have data in the array that you should backup, before anything else**.

Make sure Legacy USB support is enabled (p. 3-40)

Intel RST (p. 3-47) must be disabled. It isn't supported. **This likely impacts any RAID configuration**.

At the Boot menu disable Fast Boot (optional but prevents LOTS of problems when booting external media)
Set USB Support to **Full initialization **(p. 3-51, 52, etc.)
**Disable CSM** (p.3-54)
Secure Boot > OS type [Windows UEFI mode] > select [B]Other OS

[/B]
Lastly, you don't need to change the boot order in the UEFI settings. The Boot override (AKA the one-time boot menu) can be done with F8 when the ASUS logo is visible.

In conclusion, your fiurst priority should be to assure you have backups of whatever you need from the installed drives. Then you can even reset UEFI to defaults and start the aforementioned checklist.

---

### Post by pbd1978 on 2021-01-20
Thank you for this information. I've already backed up and destroyed the RAID volume so I'm good to go there. I'll give this a shot. Thanks again.

---

### Post by CelticWarrior on 2021-01-20
You can use softRAID in Ubuntu later if you want. It's a lot more solid.

---

### Post by pbd1978 on 2021-01-21
CelticWarrior,

Thanks for the info last night. I went through each of the steps you provided and I'm still stuck with...

ahci 0000:07:00.0: AHCI controller unavailable!

---

### Post by CelticWarrior on 2021-01-21
You may need to update the firmware (UEFI). Check ASUS website.

---

### Post by pbd1978 on 2021-01-21
I'm at the latest version as of noon yesterday.

---

### Post by pbd1978 on 2021-01-21
CelticWarrior,

It looks like the problem was the DVD drive. I unplugged it and I'm no longer hanging with AHCI controller unavailable. I appreciate you time and effort. Thanks again.

---

### Post by slickymaster on 2021-01-21
*Thread moved to **Installation & Upgrades**.*

---

### Post by CelticWarrior on 2021-01-21
Glad you found the problem. You're welcome.

---


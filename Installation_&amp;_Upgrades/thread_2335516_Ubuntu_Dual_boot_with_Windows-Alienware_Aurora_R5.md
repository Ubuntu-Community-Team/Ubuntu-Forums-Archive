---
title: "Ubuntu Dual boot with Windows-Alienware Aurora R5"
date: 2016-08-29
forum: Installation &amp; Upgrades
---

### Post by praveenlovely on 2016-08-29
Hi Pals,

I have got an Alienware Aurora R5 two days ago. It came with pre-installed Windows 10 in it in the 512 GB SSD. The BOOT mode is set to UEFI and safe boot is enabled.
I have got two HDD's. Once came with the desktop 2TB 2.5" and another(I had already) 3.5" 2TB.
I would like to install Ubuntu as an additional OS to the Windows.
So, I changed BOOT option to Legacy, disabled safe boot and installed Ubuntu in the 3.5" HDD. but however it boots Ubuntu but I dont get the GRUB option to choose between the OS's. 
I have to boot windows only by changing boot mode to UEFI and couple of erroneous restarts. 
In the boot manager, I dont have an option to set priority among the HDD's.(SSD or 2.5" HDD or 3.5" HDD) It only gives me options to select either HDD or CD or Removable drive.
Can you please help on how to get it set up?

---

### Post by Dennis N on 2016-08-29
Ubuntu will have to be installed in UEFI mode in order to detect and boot UEFI Windows from grub - they have to be installed in the same mode.

---

### Post by yancek on 2016-08-29
The link below is the official Ubuntu documentation on dual booting with windows using UEFI.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2016-08-29
If I have seen one, I have seen a 100 posts where users with UEFI systems immediately change to Legacy boot to install Ubuntu.
Where do new users get this idea? 
praveenlovely why did you think you had to do that, so we can train users not to do it?

If you have installed in UEFI boot mode or have gpt partitioning on second drive, post this:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by praveenlovely on 2016-09-01
Thanks for your prompt reply guys.
So now, as per the blogs and your advise, I have installed Ubuntu in UEFI mode.
A quick recap to my configuration.

[FONT=arial]
[/FONT]
[FONT=arial]Alienware Aurora R5.[/FONT]
[FONT=arial]1. 512 GB SSD (Came with the desktop)[/FONT]
[FONT=arial]2. 2 TB 2.5" HDD ( Came with the desktop)[/FONT]
[FONT=arial]3. 2 TB 3.5" HDD ( I have been using it since earlier)


My desktop came installed with Windows 10 in UEFI mode.
I tried deactivating the secure boot mode and created a partition in the 512 GB SSD and installed Ubuntu to the unallocated partition in the SSD.
Now,  GRUB screen loads with Ubuntu and Windows boot manager but windows does not load. 
A screen comes up saying startup failed.
When I turn the secure boot on, windows loads up and Ubuntu does not load up.
Can you help me solve the issue?
I used boot-repair software which re-installed the GRUB but still the same issue persists.
[/FONT]

Please help

---


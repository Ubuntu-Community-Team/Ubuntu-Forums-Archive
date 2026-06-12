---
title: "Device for bootloader and &quot;next&quot; button are grayed out in partitioning section"
date: 2023-09-23
forum: Installation &amp; Upgrades
---

### Post by riccd on 2023-09-23
Hi, I'm trying to install Ubuntu 23.04 on a system that has only one SSD and two other systems installed, Linux Mint and Windows. I want to try a triple boot. This is how the partitions are set:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292784&stc=1[/IMG]
I only managed to free those 166 GiB and allocate them for Ubuntu.
Then I run the USB pen installer (with acpi=off noapic commands or it won't start). When it comes to the partitioning part there are a few problems:
1-There is some kind of screen resolution problem as I can't see the format checkboxes. But this is just to tell.  
2-Most importantly, the dropdown "Device for bootloader installation" only shows my SDD but it is grayed out and also, If I select sda8, the NEXT button is grayed out. 

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292783&stc=1[/IMG]
My laptop is an old ASUS K53SV, but I don't think this is the problem. Any suggestion?

---

### Post by ubfan1 on 2023-09-23
I don't know what Ubuntu 23.04 does for a legacy install -- maybe since there is no choice, only one disk, the bootloader location location is greyed out.
Have you selected sda8, then change to make it root, ... then maybe the next button will work.

---

### Post by riccd on 2023-09-23
> **ubfan1 said:**
> I don't know what Ubuntu 23.04 does for a legacy install -- maybe since there is no choice, only one disk, the bootloader location location is greyed out.
Have you selected sda8, then change to make it root, ... then maybe the next button will work.

Yes I added / as mount point for sda8 in the Ubuntu partition manager, which, in my knowledge means root. Despite this I can't go ahead. I'm now trying with 22.04 to check.

---

### Post by Rubi1200 on 2023-09-23
I tried 3 times to install 23.04 with the new installer and each time the installation failed.

Try with the legacy installer, worked for me.
[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop) and scroll down the page to here [https://prnt.sc/COz5p_sRxPqP](https://prnt.sc/COz5p_sRxPqP)

Hope this helps.

---

### Post by tea for one on 2023-09-24
Your screenshot shows an unusual partition scheme.
It looks like older style mbr with extended partitions.
/boot/efi is in the extended section (sda6) - I've never seen that before.

Which Windows version do you have?
Is it installed in Legacy/Bios mode?

How did you install Linux Mint - Legacy or UEFI?

I think that your first priority is to make sure that you have data backups.

---

### Post by riccd on 2023-09-24
> **Rubi1200 said:**
> I tried 3 times to install 23.04 with the new installer and each time the installation failed.

Try with the legacy installer, worked for me.
[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop) and scroll down the page to here [https://prnt.sc/COz5p_sRxPqP](https://prnt.sc/COz5p_sRxPqP)

Hope this helps.

Thank you, yes after trying to install with the new installer many times I ultimately decided to use a legacy installer but I decided to install the 22.04 LTS version of Ubuntu as I was not really sure to install the 23.04. In the end I was successful. Do you think the 23.04 is worth trying?

---

### Post by riccd on 2023-09-24
> **tea for one said:**
> Your screenshot shows an unusual partition scheme.
It looks like older style mbr with extended partitions.
/boot/efi is in the extended section (sda6) - I've never seen that before.

Which Windows version do you have?
Is it installed in Legacy/Bios mode?

How did you install Linux Mint - Legacy or UEFI?

I think that your first priority is to make sure that you have data backups.

ahah  yes the fact is I install an OS at most once a year so I am not very  practical with all the tech details that go into the partition scheme so  it's well possible I installed in unusual ways maybe following some  sloppy tutorial or such on dual boot. Knowing this, I backed up my data  for good.
The laptop is very old, ASUS K53SV, It probably has more than 15 years, so the number of primary partitions allowed is 4.
According  to a few checks I made, it seems both Windows and Mint are  installed in legacy mode. I have to confess I wouldn't even know how to switch between the two installation modalities. 
At this time I was successful at installing Ubuntu  22.04 in sda8, which is in the extended partition sda3. I had to  manually prompt the grub that was previously installed to update itself  in order to recognize Ubuntu as the installer wasn't able to add a bootloader in sda8

---

### Post by Rubi1200 on 2023-09-25
> **riccd said:**
> Thank you, yes after trying to install with the new installer many times I ultimately decided to use a legacy installer but I decided to install the 22.04 LTS version of Ubuntu as I was not really sure to install the 23.04. In the end I was successful. Do you think the 23.04 is worth trying?

Stick with the LTS releases for more security and stability.

I was only testing 23.04 and also 23.10.

My main install is always the latest LTS release.

---

### Post by mikf9191 on 2024-09-15
I had this problem too, with the Ubuntu Mate 24.04.1 LTS installer. 

 I tried the solutions above (except for the legacy installer) but none of those work.

I solved it in the end.  My problem was that my hard-disk drive had no UEFI boot partition on it (/boot/efi).  The manual-partitioning page doesn't seem to allow you to add one. And it will not enable the "Next" button if it's not there!

The only way I could fix this was to back up my hard-drive, and then go through the standard install page (instead of manual partition), and this worked - and it added the missing UEFI boot partition for me.

Then I looked at the installer again, and now the manual-partitioning page was working correctly.  So it seems it gets stuck if it can't find a ready-made UEFI boot partition (/boot/efi) on there.  I've raised a bug report for this on launchpad.net

---

### Post by saint42 on 2024-10-03
You need to create a /boot/efi partition as VFAT first. 
Then you can add other partitions, and the drop down box won't be grayed anymore and will let you chose /boot/efi you just created.

---

### Post by grahammechanical on 2024-10-03
@ mikf9191

> I had this problem too, with the Ubuntu Mate 24.04.1 LTS installer.

> The manual-partitioning page doesn't seem to allow you to add one. And it will not enable the "Next" button if it's not there!

The purpose of the manual partitioning page is to allow the user to select partitions already created. The Try/Live Ubuntu session has on it GParted that we use to shrink/move/delete/create partitions before going into the Install Ubuntu session.

What you see as a problem is not a bug. The installer is that way by design. There is no need for the installer to be able to shrink/move/delete/create partitions when there is a program (GParted) that is part of the TRY/INSTALL Ubuntu ISO image.

Regards

---


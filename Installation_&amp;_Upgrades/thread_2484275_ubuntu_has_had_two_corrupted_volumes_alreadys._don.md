---
title: "ubuntu has had two corrupted volumes alreadys. dont know why"
date: 2023-02-21
forum: Installation &amp; Upgrades
---

### Post by d3vestator on 2023-02-21
he is the paste of the log info. 
[https://paste.ubuntu.com/p/RrZnB5R2XX/](https://paste.ubuntu.com/p/RrZnB5R2XX/)

---

### Post by yancek on 2023-02-22
Boot repair output information on boot and some system files and there is nothing related to corrupted volumes that I can see.  Where do you get the information that volumes are corrupted?  Did you have warning/error messages when booting Ubuntu? If so, post them. Can you successfully boot Ubuntu? Windows?

What do you mean by volumes?  Sometimes partitions are referred to as volumes but you have only one Linux/Ubuntu partition.

---

### Post by d3vestator on 2023-02-22
it says.. 
Failed to open /EFI/UBUNTU/grubx64.efi - Not found
Failed to load image /EFI/UBUNTU/grubx64.efi: Not found
start_image() returned Not Found, falling back to default load
Failed to open /EFI/UBUNTU/grubx64.efi - Not found
Failed to load image /EFI/UBUNTU/grubx64.efi: Not Found
start_image() returned Not Found

---

### Post by d3vestator on 2023-02-22
sorry maybe volumes was the wrong term, i thought i did see a corrupt volume in the message, but i guess not. maybe it was in the last error message i had with Ubuntu last time.

---

### Post by ajgreeny on 2023-02-22
You still have not said whether or not you can actually boot to either Ubuntu or Windows so please tell us in as much in detail as you can.

I am assuming you can't get to Ubuntu as those 
```
Failed to open /EFI/UBUNTU/grubx64.efi - Not found
Failed to load image /EFI/UBUNTU/grubx64.efi: Not found
start_image() returned Not Found, falling back to default load
Failed to open /EFI/UBUNTU/grubx64.efi - Not found
Failed to load image /EFI/UBUNTU/grubx64.efi: Not Found
start_image() returned Not Found 
```
messages seem to be saying that the boot files needed can not be found.

Are you certain that you are still booting to the correct device when you boot from cold?

---

### Post by d3vestator on 2023-02-22
my computer would dual boot before linux had an error, but now When I boot it up, it gives me that message and then boots to windows. There is not grub anymore

---

### Post by d3vestator on 2023-02-22
what i find odd though, is that the first time this happned which was sunday, i didnt think of the issue the first time around untill yesterday when it happened, but when i reinstalled it from a usb the first time,  the computer asked me if i wanted to overwrite the old partition for the new one. the old partition still existed, and was being recongized. It just wasnt working

---

### Post by ajgreeny on 2023-02-23
> **d3vestator said:**
> what i find odd though, is that the first time this happned which was sunday, i didnt think of the issue the first time around untill yesterday when it happened, but when i reinstalled it from a usb the first time,  the computer asked me if i wanted to overwrite the old partition for the new one. the old partition still existed, and was being recongized. It just wasnt working

So did you overwrite the old partition or not?

---

### Post by oldfred on 2023-02-23
You show both grub in MBR (gpt's protective MBR) for BIOS boot and in ESP for UEFI boot. 
Windows is UEFI boot on gpt drive.
You do not mix BIOS boot and UEFI boot on same drive, systems should be in same boot mode.

It looks like at some point you incorrectly installed or repaired Ubuntu in BIOS mode to get grub boot loader in MBR.
And also then installed in UEFI mode to have grub in ESP.
But only last way you installed or fixed grub will work. When you try to boot in other mode, it fails with the error messages or just grub>.

Make sure to boot Boot-Repair in UEFI mode and totally reinstall grub or reinstall in UEFI mode.
Make sure system is set to boot in UEFI mode.

While grub in MBR can be erased, it is more dangerous for new users than just leaving it and never booting in BIOS mode.

---

### Post by d3vestator on 2023-02-23
yes i overwrited the old partition the first tim around, i haven done anything this time yet

---

### Post by d3vestator on 2023-02-23
i have two questions. 1: do i have to shrink windows main partition size. I have enough space on the one drive for both and second question: can i delete the old linux partition before i reinstall Ubuntu,

---

### Post by MAFoElffen on 2023-02-23
From what you just said, it sounds as if you already shrank the partitions of windows to install Ubuntu (incorrectly) the first time, right? If so, then no to #1... Which affects #2.

With number 2, you have 2 options, either carefully delete the old Ubuntu partition and install the new Ubuntu into the free unallocated space... Or use "something else" to install into the existing Ubuntu partition. Deleting the old would be the preferred, but just be careful to get the correct partition.

My recommend would be to do it with gparted, so there is less change of confusion on which partition is the old Ubuntu partition (look at filetype present, ext4)...

---

### Post by d3vestator on 2023-02-24
how would the window parition size shrink. I didnt touch it. would that happen automatically when i installed Ubuntu? and can i check if the size shrunk

---

### Post by MAFoElffen on 2023-02-24
No. The Ubuntu installer will not shrink the Windows partition...

I'm confused... You did try to install Ubuntu previously right? Which meant you previously shrank the Windows partition from inside Windows to allow space for that previous install? (To allow Ubuntu to install "beside" Windows in the unallocated space of the disk?)

If not enough room there after deleting the existing, Ubuntu partition, then yes... Startup Windows and shrink it 'more'.

---

### Post by d3vestator on 2023-02-24
I did reinstall it before. Sorry, I didn't know that the windows parition would shrink automatticaly. I thought that if my drive had enough space to accommodate both os, then the windows pariton wouldn't shrink.

---

### Post by yancek on 2023-02-25
>  I didn't know that the windows parition would shrink automatticaly

I've never used an installer (Linux or windows) which would automatically shrink a partition.  In your case (output from boot repair in post 1), you have a primary windows partition of 247GB and a Linux partition of 228GB.  Best way to resize a windows partition is with their Disk Management tool.  No need to do that now as it has already been done.  Before installing Ubuntu, the drive partition with windows would have taken up the entire drive so it was shrunk somehow.

With the installs the way you have them, you need to make sure you boot in UEFI mode.  The boot files you have on   nvme0n1p1, the EFI partition, are correct for both windows and Ubuntu.

I would suggest you follow the suggestions made in post 10 above.

---

### Post by d3vestator on 2023-02-25
can you explain booting into UEFI mode, i know what that is but not sure how to do that. I have an Asus laptop, and what I originally do is boot to bios Utiliy, and boot to the installation usb from there. im not sure if bios utulity is uefi. It might be both bios and uefi. I cant find a serperate uefi option on my laptop to boot to.

---

### Post by yancek on 2023-02-26
There must be an EFI option as you have both windows and Ubuntu installed EFI as shown in your boot repair output in your first post.  It should be under Boot or Boot options in the BIOS firmware.

---

### Post by tea for one on 2023-02-26
> **d3vestator said:**
> can you explain booting into UEFI mode, i know what that is but not sure how to do that. 
The boot-repair report in your first post was produced while in EFI (or UEFI) mode.
[COLOR="#0000FF"]Line 90[/COLOR] - The firmware is EFI-compatible, and is set in EFI-mode for this live-session

If you are going to reinstall Ubuntu, you can check how you have booted the live installer session with a terminal command:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```

---

### Post by d3vestator on 2023-02-26
i installed Ubuntu, i made sure it was UEFI which it was and when i was in the process it asked me, to rewrite the exsiting partition that was already there, which i did. Wasnt sure if i suppose do that or not. If i sent a pastebin agian, could you check if it was installed correctly this time. I dont want to keep going though this, and i dont want keep doing stuff for it to keep deleting.

---

### Post by ajgreeny on 2023-02-27
I am certainly confused about your current situation so I think it may be helpful for you to run the boot-info script again, making sure you boot the system in UEFI mode before running it.

---


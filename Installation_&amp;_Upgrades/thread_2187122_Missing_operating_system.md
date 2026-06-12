---
title: "Missing operating system"
date: 2013-11-10
forum: Installation &amp; Upgrades
---

### Post by nibal on 2013-11-10
I have a 3-boot PC with Windows XP, Windows 7 and Ubuntu 12.04, all on different partitions on the same disk. Boot loader is grub for Linux/XP, and Windows XP has an MS boot loader for Windows XP/7. My XP partition had disk problems for some time now, but didn't bother with it, since I didn't use it much. My PC worked without any problems booting or otherwise. After missing for 1 week for business, I came back and found Windows 7 partrition crashed. Had to reformat and reinstall. After reinstall I can boot into Windows 7 fine. However cannot boot into Linux any more :-(

Used the Ubuntu live CD to mount my installation and check the partition table. Using fdisk I toggled the boot flag on the Linux /boot and reboot. I got from the BIOS "Missing Operating System". Verified partition table through fdisk, looks fine. Reconfigured grub, same problem. Even copied all files from /boot to a backup directory, to check for an fs problem (/boot is in its own partition). No problem.

I am now using the Ububtu Live CD, but I cannot keep using it. Each time I loose settings, bookmarks etc. Ran out of ideas. Can you suggest what to try next?

---

### Post by fantab on 2013-11-10
When you re-installed Windows7 it messed up the MBR for Ubuntu. Its normal. You will have to re-install GRUB. [**READ HERE**]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd"), for a how to.

If you still encounter any problems... post about them starting with the output of:

```
sudo parted -l
sudo fdisk -l
```

---

### Post by oldfred on 2013-11-10
Grub does not use boot flag. But Windows does, for Windows to work you have to have boot flag on the Windows partition with the boot files. If you have multiple installs of Windows, only one install will have all the boot files for all the Windows.

Follow fantab's suggestion or download Boot-Repair into you live Ubuntu installer in live mode or download a full Boot-Repair CD.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[URL="https://help.ubuntu.com/community/Boot-Repair"]https://help.ubuntu.com/community/Boot-Repair

      [/URL]
 Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

    [URL="https://help.ubuntu.com/community/Boot-Repair"]
[/URL]

---

### Post by nibal on 2013-11-18
Thx both of you. Sorry i didn't reply earlier, but was expecting an email notification from the forum :-(.
Fantab: I am aware of that, but I assumed that once I reconfigured grub, it overwrote the MBR. At least that was my experience with LILO, I am new to grub.

I will follow up with your suggestions, give boot-repair a try and post the results :-)

---

### Post by nibal on 2013-11-18
Yeap that worked :-). Didn't use boot-repair, since it had unmet dependencies. Instead, I monted my partitions from the liveCD and chroot into them. There I typed:

> 
grub-setup /dev/sda


and after making bootable the grub partition with fdisk, I got grub working again.

Thank you :-)

---


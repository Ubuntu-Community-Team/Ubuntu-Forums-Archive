---
title: "Unable to get fresh Ubuntu 18.04 install to boot"
date: 2018-07-22
forum: Installation &amp; Upgrades
---

### Post by ChildOfMana on 2018-07-22
Hi there,

I'm having a major headache trying to get Ubuntu installed. I'm trying to install to a blank, freshly formatted 120Gb SSD (sda) with a second 3TB HDD for /tmp, /home and swap (sdb).

Both disks are using a GPT partition table but the BIOS is set to Legacy, not EFI.

At first I went through the normal steps for a fresh install - used the 'Install' option from a Live CD and opted for manual partitioning. I set everything up as described above (with the entire SSD given over to /, 8Gb for /tmp on the HDD, 8Gb for swap and the rest all /home). Installation was a breeze but when I came to reboot I was met with a black screen saying: 
```

error: attempt to read or write outside of disk hd0.
Entering rescue mode...
grub rescue> _ 

```

I did a bit of googling and found [this]("https://askubuntu.com/questions/397485/what-to-do-when-i-get-an-attempt-to-read-or-write-outside-of-disk-hd0-error"). I tried the accepted solution but to no avail. I just got exactly the same error message again.

So, going back to the drawing board I found another possible solution which was to create a 1Gb /boot partition at the start of the disk. I re-installed and this time created the suggested 1Gb /boot partition on the SSD, then the rest of that drive to / with /tmp, /home etc on the HDD. I rebooted after installation and this time just got a black screen with a blinking cursor (that wouldn't respond to keyboard input) and nothing else. No error message. Same thing happened after a few restarts and a cold boot.

I re-read the article (I'm sorry I can't find it again to link to it now) and noticed that I'd missed one important step of the suggested solution - pointing the boot manager installation to sda1 (the /boot partition) instead of the root of the sda drive. So, I did it all over again making that one change but again it didn't work. However this time something new happened on reboot - I was met with a purple screen with the following error message:
```

error: failure reading sector 0x9f600 from 'hd0'.
press any key to continue..._

```

But no matter what keys I pressed it failed to respond... except once - just once - when I left it sitting at that screen for a good 5 minutes or so whilst I was doing some research from my laptop it all of a sudden decided it was going to boot! I was able to log in and mess around with no obvious problems. Just a nice fresh Ubuntu install seemingly working perfectly. Feeling brave I rebooted to see what would happen... and got the same purple screen with the same error message again. Except now it won't even boot after leaving it sitting at that screen for over 20 minutes! It just booted that once and never since.

Does anyone have any idea what might be going on or how I can get this installed?

If it matters the SATA controller is set to AHCI in the BIOS and, as mentioned earlier, the BIOS is in Legacy mode, not EFI. The SSD is relatively new and was taken out of my Windows 10 rig after a recent upgrade. It was working perfectly fine in that rig and I had a look at the SMART data just before I removed it and it was reported as being in excellent health, so I doubt it's a problem with the drive.

Oh, almost forgot! I also read about creating a Legacy BIOS Boot (or words to that effect) partition on the drive so I tried that but I didn't get the option to create on of those on the SSD, only on the HDD. I decided there was nothing to lose by giving it a go so I created it on the HDD, pointed the boot loader installation to that drive and tried again (but still with / on the SSD and the rest of the HDD partitioned as before, except for the new addition) but again no joy, not unexpectedly. I can't remember if I got any specific error messages or not that time though, sorry.

Anyways, sorry for the lengthy post. Wanted to give as much info as I could. Let me know if you need any more details.

Thanks in advance!

---

### Post by ubfan1 on 2018-07-22
With gpt partitioning on a disk, to boot it in legacy mode  you will need to add a small (2M), unformatted,  bios-grub flagged partition.  Don't confuse this with a /boot partition.  This gives grub a place to dump it's binary file, which used to fit between the partitions on an MSDOS partitioned disk.  While you're at it, maybe add a 300M FAT partition for future use if you ever want to use a UEFI boot.

---

### Post by ChildOfMana on 2018-07-22
> **ubfan1 said:**
> With gpt partitioning on a disk, to boot it in legacy mode  you will need to add a small (2M), unformatted,  bios-grub flagged partition.  Don't confuse this with a /boot partition.  This gives grub a place to dump it's binary file, which used to fit between the partitions on an MSDOS partitioned disk.  While you're at it, maybe add a 300M FAT partition for future use if you ever want to use a UEFI boot.

Thanks for the reply ubfan1, I appreciate it.

I'll give it a go but (and sorry if this is obvious) I can create a 2MB unformatted partition no problem, but how do I add a bios-grub flag? Also, presumably this partition should go at the start of the disk, right? And do I point the boot loader install to that partition specifically (e.g. sda1), or leave it at the default setting (sda) and let it find it's own way?

**Edit:** And should the 2MB partition be *instead* of a /boot partition, or extra to it?

---

### Post by ChildOfMana on 2018-07-24
Got it working. I used GParted from the Live CD to create a 2MB unformatted partition and then added the bios_grub flag (you'd think the partition manager in Ubuntu's installer would allow you to manage flags!!!). I left the bootloader installation pointed at the root of the drive and now we're up and running, finally!

Thanks for the advice ubfan1.

Now I've just got an ABSOLUTE NIGHTMARE trying to get the damn thing to recognise my WiFi adapter ](*,), but that's another thread for another day in another section... at least I can boot it now :D

---


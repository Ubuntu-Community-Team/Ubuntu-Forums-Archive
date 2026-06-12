---
title: "Boot repair did not fix my issue"
date: 2022-07-22
forum: Installation &amp; Upgrades
---

### Post by jbol2 on 2022-07-22
Hi,

I'm having a weird boot issue, logs from Boot-repair can be viewed here: [https://paste.ubuntu.com/p/5r3sv9bZXC](https://paste.ubuntu.com/p/5r3sv9bZXC)

After running a sudo apt-get update my system doesnt boot up, and I see the following error messages:

Gave up on waiting for root file system device. Common problems:
- Boot args (cat /proc/modules)
   - Check rootdelay= (did the system wait long enough?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! UUID=xxxxxxxxxxxxxxxxxx does not exist. Dropping to a shell!

When I boot into a live USB and try to reinstall the latest Ubuntu LTS the main SSD of the laptop doesnt even show up in list of drives. I havent done anything weird with this laptop other than install Ubuntu LTS. Any thoughts?

I would greatly appreciate any help on this!

---

### Post by oldfred on 2022-07-22
Paste does not exist.

Sometimes an UEFI update, resets many settings to defaults.
Did it turn UEFI Secure boot on, or reset drives to RAID from AHCI? Any other settings you normally changed.
My old Asus motherboard had 7 or so settings, & I had to keep a list. But it was not in Linux fwupdate nor did I have Windows which would possibly update UEFI automatically.

---

### Post by jbol2 on 2022-07-25
sorry I posted the wrong URL, here is the correct one - [https://paste.ubuntu.com/p/5r3sv9bZXC/](https://paste.ubuntu.com/p/5r3sv9bZXC/)

---

### Post by oldfred on 2022-07-25
No drives shown?

Did update include an update to UEFI?
That often resets UEFI settings to defaults.
That may turn Secure Boot on and change back to RAID/Intel RST.
You may need to turn Secure boot off, turn AHCI back on and often other settings in UEFI.

---

### Post by yancek on 2022-07-25
Check your BIOS firmware to see if your SSD shows.

>   ALERT! UUID=xxxxxxxxxxxxxxxxxx does not exist. Dropping to a shell!


Boot the USB  and from a terminal, run the command:  blkid
Compare the output to the UUID that shows in the output above, the error message.  It may be looking for a partition UUID that does not exist.  I don't know why that would happen with a simple update.

---

### Post by jbol2 on 2022-07-25
I've verified that Secure Boot is OFF and UEFI First boot is selected, so those settings dont seem to be the issue here. Are there any other settings I should double check?

SSD appears in BIOS firmware.

When I boot into a live USB version of Ubuntu and enter the command 'blkid' in the terminal it only lists /dev/sda1: BLOCK_SIZE="2048" (which is the USB drive, it's not detecting the internal 500GB SSD).

Any other thoughts?

---

### Post by oldfred on 2022-07-25
Did youcheck the drive setting for AHCI?

---

### Post by tea for one on 2022-07-26
> **jbol2 said:**
>  Are there any other settings I should double check?

According to the boot-repair report, you have a Lenovo PC/Laptop and there may be other security UEFI settings.
Can you double-check these:-

TPM (Trusted Platform Module)
PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module)
Optane memory and storage
Device Guard (some Lenovo devices)
OS Optimised Defaults (some Lenovo devices)

If relevant, disable them and see if your drive appears?

---

### Post by jbol2 on 2022-07-26
Thanks for the quick replies.

I found the security chip type is TPM 2.0 and I disabled that in the Security section of the BIOS. I also set the Sleep mode optimization to Linux instead of Windows.

I was unable to find the following settings in the BIOS menu:
- [COLOR=#000000]PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module)
[/COLOR]- [COLOR=#000000]Optane memory and storage[/COLOR]
[COLOR=#000000]- Device Guard (some Lenovo devices)

[/COLOR]Would it be helpful if I run boot-repair again now that I've changed some bios settings? And gather a new set of logs?

Another thing I noticed, in my Grub v2.04 boot menu I'm seeing the following options when I startup:
- Ubuntu
- Advanced options for Ubuntu
- UEFI Firmware settings

Does that mean anything? Why is the UEFI Firmware settings option visible?

---

### Post by #&amp;thj^% on 2022-07-26
> **jbol2 said:**
> 
 Why is the UEFI Firmware settings option visible?

It is a direct link to your Bios is all, I find it a nice feature.

---

### Post by tea for one on 2022-07-26
> **jbol2 said:**
>  I also set the Sleep mode optimization to Linux instead of Windows.
That's a new one for me.
UEFI settings have infinite choices..........
> Would it be helpful if I run boot-repair again now that I've changed some bios settings? And gather a new set of logs?
Your drive is still invisible?
What about AHCI setting, mentioned by oldfred?

Another boot-repair report may certainly help.

---


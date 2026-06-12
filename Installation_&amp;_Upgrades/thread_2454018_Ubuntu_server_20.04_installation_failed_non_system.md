---
title: "Ubuntu server 20.04 installation failed: non system disk error"
date: 2020-11-21
forum: Installation &amp; Upgrades
---

### Post by briant789 on 2020-11-21
have found similar questions but wasn’t able to solve so far. I installed Ubuntu server 20.04 on an old HP laptop. After successfully installing it and I reboot, I get the error message: “non-system disk or disk error”.

I installed Ubuntu server from an USB. Tried it with a different USB, same result.

Tried boot-repair but again same result. 
Https://paste.Ubuntu.com/p/F2MPB7pDqh

Laptop is a HP probook 6540b

Prior to trying to install I had Ubuntu desktop running. This worked fine. I used all default settings during set-up.

The laptop had no usb and no cd/dvd in the drive. If any info is missing please let me know.

Used Gparter on Ubuntu desktop to see partitions, is this the problem?

Partition File System Mount Size Flags
 /dev/sda1 Grub2 core. 1.0MiB bios_grub 
/dev/sda2. Ext4. 1.0GiB 
/dev/sda3. Lvm2 pv Ubuntu-vg. 297GiB Unallocated unallocated. 1.3MiB

Appreciate your help!

---

### Post by oldfred on 2020-11-21
What brand/model system?
Post the link that Boot-Repair gives for its Summary Report.

---

### Post by briant789 on 2020-11-21
[Https://paste.Ubuntu.com/p/F2MPB7pDqh](Https://paste.Ubuntu.com/p/F2MPB7pDqh)

Laptop is a HP probook 6540b

---

### Post by oldfred on 2020-11-21
Do you have UEFI/BIOS set to boot in BIOS/Legacy/CSM boot mode?
It looks like grub is correctly installed to MBR using bios_grub partition and /boot partition.

But I do not know LVM nor BTRFS. 
But why /boot as BTRFS? Grub may need extra drivers for that, or insmod files.

---

### Post by briant789 on 2020-11-22
Thanks. As this is my first Ubuntu installation I am not entirely sure how to proceed right now. I guess I need to install Ubuntu desktop first and then run some updates? How do I do that?

---

### Post by oldfred on 2020-11-22
While many suggest LVM for its flexibility and it is required if you want full drive encryption, it is like jumping into the deep end of the pool to learn to swim.
LVM often used on servers, but is more complex.
If you want LVM, you need to review many of the instructions that are available.

What do you want in the way of configuration.

Default desktop install is just / (root). But with UEFI it also then has an ESP - efi system partition.
Everything beyond that is optional, many suggest separate /home or data partition(s).
Do you need or want full drive encryption?

---

### Post by briant789 on 2020-11-22
Thanks. Disk encryption not needed. I tried installing without LVM but get the same message after reboot (non system-disk error). Do I need to change something in BIOS or is the problem in the installation procedure itself? I am about to give up :-(

---

### Post by oldfred on 2020-11-22
Could be either.
What brand/model system.
Some like Acer need "trust"
Some like HP are difficult, but several work arounds, depending on configuration.

If installing in UEFI mode, do you have UEFI set to boot in UEFI mode. 
My motherboard only worked with UEFI only setting, not UEFI or CSM(BIOS) mode.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by briant789 on 2020-11-22
Link to boot-info report:
[Https://paste.Ubuntu.com/p/Ghfyk9R7sX/](Https://paste.Ubuntu.com/p/Ghfyk9R7sX/)

---

### Post by oldfred on 2020-11-22
You are booting in BIOS mode from gpt partitioned drive with bios_grub partition.
So configuration looks normal for a BIOS boot.

What brand/model system?
May need settings in UEFI/BIOS. Or boot parameter in grub.

---

### Post by briant789 on 2020-11-22
Laptop is a HP probook 6540b.

---

### Post by oldfred on 2020-11-22
Looks like it may be a very early UEFI based system.
But for those, generally a BIOS install just works.

Do you have some setting in UEFI/BIOS on boot mode.
Is it the most current UEFI, but still probably pretty old.
Some HP needed UEFI/BIOS settings. See if any of these apply as vendors often do similar settings across multiple models. And look for others that relate to boot mode or drive.
HP Elitebook 840 G5 gpt issues - 
HP put a fail-safe gpt recovery into the UEFI Settings,  go into the UEFI Menu in Security -> Hard Drive Utilities -> Uncheck "Save/restore GPT System of Hard Drive"
[https://ubuntuforums.org/showthread.php?t=2436271](https://ubuntuforums.org/showthread.php?t=2436271)
HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216)

---

### Post by briant789 on 2020-11-23
There is no secure boot option in my bios. I also tried to see if there is a bios update available from HP for a probook 6450b, but no.
I see one setting where I can check / uncheck UEFI Boot Mode. Tried both options, no result.

---

### Post by CelticWarrior on 2020-11-23
Secure Boot settings should be at Security.
If Legacy is selected it's very likely that setting won't show up because not applicable.

---


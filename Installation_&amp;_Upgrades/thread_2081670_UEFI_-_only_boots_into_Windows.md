---
title: "UEFI - only boots into Windows"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by zengeos on 2012-11-07
I've tried Boot Repair and still cannot seem to fix my drive in Windows 8. ONLY boots into Windows 8. Please advise.

Here is my boot repair info

[http://paste.ubuntu.com/1340112](http://paste.ubuntu.com/1340112)

---

### Post by coffeecat on 2012-11-07
Moved to own thread.

@zengeos, please start your own threads.

---

### Post by zengeos on 2012-11-07
Thanks for moving the post coffeecat. I didn't want to overpopulate message threads so added to  closest sounding existing thread.

---

### Post by oldfred on 2012-11-07
Did you copy your efi partition or something?

You can only have one efi partition and you have two. Both sda2 & sda4 are flagged as efi partitions and both are in the fstab in  sda8. Only one is in the fstab of the install in sda11.

Boot-Repair may have duplicated the entries in fstab if it saw two efi partitions which it would not expect to see.

Are you getting a grub menu when you try to boot Ubuntu? 

Are you booting Windows directly from the UEFI menu?

---

### Post by zengeos on 2012-11-07
Thanks for your response. No Grub menu comes up. Should I force Grub Repair to use sda2 then?  If so, should I NOT format it?
sda 2 is l;isted as boot, hidden. Can I still use it or do I need to make it unhidden somehow?


I think the hidden flag caused Boot Repair to prompt me to create a boot partition. If I remove that flag, will that fix things?

I am totally unfamiliar with efi and Win 8 as you can see :/

---

### Post by oldfred on 2012-11-07
You should only have one boot flag which in gpt partitioning means the efi partition.

In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT! (just the one efi partition).

---

### Post by zengeos on 2012-11-07
> **oldfred said:**
> You should only have one boot flag which in gpt partitioning means the efi partition.

In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT! (just the one efi partition).


OK I am flailing in EFI land here, so I removed the boot flag on sda4. I unhid sda 2 and re-ran boot repair. 

Unfortunately, this did not fix things and Windows actually ran Windows Repair. Here is the new log

[http://paste.ubuntu.com/1340584/](http://paste.ubuntu.com/1340584/)

---

### Post by oldfred on 2012-11-07
If you go into UEFI does it not give several boot choices like ubuntu, windows?

And if you boot ubuntu does it not give a grub menu?

Or it then could be video issues.

---

### Post by zengeos on 2012-11-07
> **oldfred said:**
> If you go into UEFI does it not give several boot choices like ubuntu, windows?

And if you boot ubuntu does it not give a grub menu?

Or it then could be video issues.

Yes, uefi gives several options including 2 Ubuntus. If I select the first it goes into Windows. If I select the 2nd Ubuntu item it flashes up a message that Ubuntu has been blocked, then continues to Windows Repair.

---

### Post by oldfred on 2012-11-07
Is this the new secure boot that only lets you boot Windows?

You can either turn off secure boot, and maybe some other settings in UEFI. Or install the very new grub2 2.00that supposedly works with secure boot.

Secure Boot
[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/](http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/)
[http://www.linuxfoundation.org/publications/making-uefi-secure-boot-work-with-open-platforms](http://www.linuxfoundation.org/publications/making-uefi-secure-boot-work-with-open-platforms)

---

### Post by zengeos on 2012-11-07
Yes, this is a new Windows 8 Lenovo laptop. I installed Ubuntu 12.10 and decided to try out E17. Ubuntu got hosed, apparently, so I tried reinstalling it. That's where the boot problem started. I will try reading through the two links you provided above, to hopefully educate myself a bit more on things. Thanks for your help and advice once again.

---

### Post by zengeos on 2012-11-07
> **oldfred said:**
> Is this the new secure boot that only lets you boot Windows?

You can either turn off secure boot, and maybe some other settings in UEFI. Or install the very new grub2 2.00that supposedly works with secure boot.

Secure Boot
[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/](http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/)
[http://www.linuxfoundation.org/publications/making-uefi-secure-boot-work-with-open-platforms](http://www.linuxfoundation.org/publications/making-uefi-secure-boot-work-with-open-platforms)

Thanks for the links, etc. Found step by step to access UEFI and BIOS and disabled Secure boot

Lots extraneous Grub entries, but I wil work on those eventually.

---

### Post by oldfred on 2012-11-07
If your chain load entries are in 40_custom or 25_custom, you can turn off os-prober. If you need it again you then can turn it back on with false or re-enable execution bit.

In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober

I always include a copy of my 40_custom in my backups. I just copy it into /home so when I backup /home it is included.

---


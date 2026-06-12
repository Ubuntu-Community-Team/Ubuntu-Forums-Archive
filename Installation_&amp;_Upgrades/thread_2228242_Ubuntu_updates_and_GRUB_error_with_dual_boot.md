---
title: "Ubuntu updates and GRUB error with dual boot"
date: 2014-06-06
forum: Installation &amp; Upgrades
---

### Post by riccardosl45 on 2014-06-06
Hello, I have this strange behaivior with Ubuntu 13.10 and Windows 7 in dual boot:

everything is running fine but when I need to install ubuntu updates related to kernel or system files I always lost the GRUB boot loader after reboot.

After the reboot Grub it's empty and I have to fix it using boot recovery tools.

My latop has an hybrid disc with 32 GB SSD + 500 GB disk, is this happening also to other users? is there a solution to avoid re-install GRUB every time?

I can provide more info, just ask me

Thanks a lot!

---

### Post by oldfred on 2014-06-06
Is this UEFI or BIOS?
Is SSD part of Intel SRT, if that is on, grub may not reinstall correctly.

Post link to BootInfo report:
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by riccardosl45 on 2014-06-06
> **oldfred said:**
> Is this UEFI or BIOS?
Is SSD part of Intel SRT, if that is on, grub may not reinstall correctly.

Post link to BootInfo report:
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Hi Olfred, settings are in Legacy mode not UEFI, and yes it's Intel SRT, I used to remove DMRAID during installation but at every update I have to repeat the procedure?

Following output from boot repair
[http://paste.ubuntu.com/7604447/](http://paste.ubuntu.com/7604447/)

---

### Post by oldfred on 2014-06-06
I do not think I have seen others with the issue. Not sure how many actually kept Intel SRT working?

May be related to the reported overlap issues in the mapper volumes?

Also 14.04 seems a bit better at recognizing Intel SRT, but I think grub still has issues as it does not know if really RAID or not. Some have reported just changing UEFI/BIOS to AHCI they can reinstall grub. I do not think they remove the RAID meta-data.

Also not that with 32GB on SSD that the SRT only uses about half. My / is 11GB used, so you could have / inside the SSD and make Ubuntu quick also. One or two users posted that they were able to configure it that way.

       Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)

User in one of these threads does say to disable RAID each time you update.

 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

---

### Post by riccardosl45 on 2014-06-12
> **oldfred said:**
> I do not think I have seen others with the issue. Not sure how many actually kept Intel SRT working?

May be related to the reported overlap issues in the mapper volumes?

Also 14.04 seems a bit better at recognizing Intel SRT, but I think grub still has issues as it does not know if really RAID or not. Some have reported just changing UEFI/BIOS to AHCI they can reinstall grub. I do not think they remove the RAID meta-data.

Also not that with 32GB on SSD that the SRT only uses about half. My / is 11GB used, so you could have / inside the SSD and make Ubuntu quick also. One or two users posted that they were able to configure it that way.

       Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)

User in one of these threads does say to disable RAID each time you update.

 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)


Hello,
thanks to your links I tried to upgrade ubuntu to last 14 version without the issue on GRUB, I did these steps:

- in windows on Intel SRT I disabled the SSD+HDD Raid
- on Bios set boot to AHCI insted of RAID mode
- on ubuntu I removed metadata raid  ([FONT=Courier New]sudo dmraid -E -r /dev/sdb[/FONT])

Upgrade worked succesfully !
Riccardo

---


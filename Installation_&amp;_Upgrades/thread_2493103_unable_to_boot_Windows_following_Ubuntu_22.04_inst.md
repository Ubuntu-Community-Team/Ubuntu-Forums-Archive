---
title: "unable to boot Windows following Ubuntu 22.04 install"
date: 2023-12-03
forum: Installation &amp; Upgrades
---

### Post by mrmeadows on 2023-12-03
I recently installed Ubuntu 22.04 on my computer which originally had only Win 7 operating system. This new installation resulted in a complete inability to boot up the Win 7. Previous to this latest installation, I had a dual boot machine with Unbuntu 20.04 running nicely with Win 7. At that time, Win 7 was the default OS which would boot up automatically. When I wanted Ubuntu, I would hit the Esc key during startup and select the drive on which the Ubuntu existed, and the Ubuntu would boot up. Currently Ubuntu seems to be the default OS during startup. There is a startup menu which offers to boot Win 7, but when that is selected, Windows looks for files, can't find any and ... basically crashes.

     I have spent an inordinate amount of time following various suggestions to fix this unacceptable situation, including boot-repair but none solved the problem. Most recently, I've poked around looking at the various grub files that are associated with startup. I found the following which appears to be an error which is associated with the problem

     In /boot/grub/grub.cfg there is this section about the Windows 7 OS which is on a different drive from Ubuntu.


### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (on /dev/sdc3)' --class windows --class os $menuentry_id_option 'osprober-chain-5EF0008AF0006B1B' {
    insmod part_gpt
    insmod ntfs
    set root='hd2,gpt3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt3 --hint-efi=hd2,gpt3 --hint-baremetal=ahci2,gpt3  5EF0008AF0006B1B
    else
      search --no-floppy --fs-uuid --set=root 5EF0008AF0006B1B
    fi
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

There seem to be a bigtime error in this, but I'm not sufficiently knowledgeable to know for sure. The menuentry line shows the Win 7 on /dev/sdc3. But according to the Ubuntu system app Disks, the Win 7 boot partition is /dev/sdc1, while /dev/sdc3 is the data partition on that drive. Also the UUID number 5EF0008AF0006B1B is associated with /dev/sdc3, while the /dev/sdc1 has UUID 5AE9-6E04. The entire Disks info shows
    Size 105MC(104,857,600 bytes)
    Contents FAT(32-bit version) - Not Mounted
    Device /dev/sdc1
    UUID 5AE9-6E04
    Partition Type EFI System (No Automount)

While I could change the two errant entries, it is not clear that that would solve the problem. Probably would just make matters worse by conflicting info elsewhere in the system. But this situation will perhaps tell someone more knowledgeable than I what needs doing to restore the ability to boot either Ubuntu or Win 7. I would greatly appreciated help from such a someone.

Thank you.
      --- Mike

---

### Post by oldfred on 2023-12-03
If you used Boot-Repair, post link to the summary report it can create.

Windows 7 used to be installed in BIOS mode. later versions could also be installed in UEFI boot mode, but with UEFI Secure Boot off as Windows 7 does not support Secure Boot.
UEFI boots via the ESP - efi system partition which is FAT32 with esp,boot flags. If drive is gpt then Windows has to be UEFI boot. Or if it was BIOS, then drive has to be MBR(msdos).
UEFI boot stanza for Windows is different than the old chainloader stanza for BIOS boot into Windows NTFS boot partition with boot flag.

---

### Post by yancek on 2023-12-04
>  The menuentry line shows the Win 7 on /dev/sdc3

That would be the windows 7 system partition, what is usually referred to a the C:\ drive.  From the other information you posted, it seems that sdc1 was created or was originally and EFI partition.  The UUID shows it is a vfat partiiton.  The UUID for sdc3 shows it is ntfs.  I would guess that you installed Ubuntu in EFI mode while windows 7 was Legacy and the installer create the EFI partition on /dev/sdc, the windows drive, or perhaps it was already there?  

>  I have spent an inordinate amount of time following various suggestions to fix this unacceptable situation,

Bad idea.  Did you read the page at the boot repair site where it specifically suggests not to do reparis but to run the script and post the link to a forum where users more knowledgeable might review it?  Always a better option.

I don't know why the Ubuntu installer used an EFI partition on sdc unless it was there already and the drive is gpt which we don't know (boot repair output would have told us).  If your windows disk had been disconnected or you had been able to create an EFI partition on whichever disk you have Ubuntu on, it should have booted the Legacy windows 7 on another drive.

---


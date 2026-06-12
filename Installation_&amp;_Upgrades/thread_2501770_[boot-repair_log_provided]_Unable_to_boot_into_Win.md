---
title: "[boot-repair log provided] Unable to boot into Windows 10 after installing Ubuntu 22"
date: 2024-10-20
forum: Installation &amp; Upgrades
---

### Post by anaypat on 2024-10-20
I recently replaced Ubuntu 16.04 with Ubuntu 22.04 in my dual boot setup. I basically formatted the Ubuntu 16.04 partition, and used that space to create root, home, and swap partitions for 22.04. Ubuntu works fine and the Grub screen appears normal, but when I try to boot into Windows from Grub, I just get a blank screen. The system has a SSD and HDD, the Windows system files are located in SSD, and Linux system as well as data files are located in the HDD. I ran boot-repair and I'm reaching out for advice from forum member as suggested in [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) . 

The boot-repair log can be found here [https://paste.ubuntu.com/p/d9yHVD29rs/](https://paste.ubuntu.com/p/d9yHVD29rs/)

Thanks!

---

### Post by tea for one on 2024-10-20
Does Windows 10/11 boot from the PC boot menu?

---

### Post by yancek on 2024-10-20
Boot repair shows the proper files for both systems so if you can boot windows by selecting its drive in the BIOS boot options, you might then try running:  sudo update-grub again from Ubuntu.  Or post the windows menuentry from the /boot/grub/grub.cfg file.

---

### Post by anaypat on 2024-10-20
@tea for one : The same issue persists when I boot into Windows from the PC boot menu. I checked advanced BIOS options, and observed that the "Enable Legacy Option ROMs" is set to true. Also the secure Boot option is disabled. See the attached images.

---

### Post by anaypat on 2024-10-20
@yancek : I tried booting windows from BIOS boot options, it doesn't work. Here is the code for windows menuentry from [COLOR=#000000]/boot/grub/grub.cfg file.

[/COLOR]### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sdb1)' --class windows --class os $menuentry_id_option 'osprober-efi-2832-741B' {
insmod part_gpt
insmod fat
set root='hd1,gpt1'
if [ x$feature_platform_search_hint = xy ]; then
search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt1 --hint-efi=hd1,gpt1 --hint-baremetal=ahci1,gpt1 2832-741B
else
search --no-floppy --fs-uuid --set=root 2832-741B
fi
chainloader /efi/Microsoft/Boot/bootmgfw.efi
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

---

### Post by tea for one on 2024-10-21
Enable Legacy Option ROMS - Remove tick from checkbox
Boot Sequence Ubuntu - Remove tick from checkbox (You still have Ubuntu as priority, which will then display Grub)

Does Windows boot now?

---

### Post by yancek on 2024-10-21
>  I tried booting windows from BIOS boot options, it doesn't work

Doesn't work!!  That's not useful.  If you haven't resolved this problem with the changes suggested in the post above, explain exactly what happens when you select the drive on which you have windows installed in the BIOS.  Both your installs (Ubuntu/windows) are EFI and have EFI partitions on their respective disk so should boot when you select the respective drive.

---

### Post by anaypat on 2024-10-21
> **tea for one said:**
> Enable Legacy Option ROMS - Remove tick from checkbox
Boot Sequence Ubuntu - Remove tick from checkbox (You still have Ubuntu as priority, which will then display Grub)

Does Windows boot now?

Yes! I'm writing this message from Windows. I use Linux all the time, but now I've the peace of mind that I can still use esoteric Windows apps when required. Thank You!

As suggested, I removed the tick from checkbox for "Enable Legacy Option ROMS" from the PC boot settings. I didn't have to change the "Boot Sequence Ubuntu" option. Then I checked if I could boot into Windows from PC boot menu (not Grub yet). After confirming that, I tried using Grub to boot into Windows, and everything worked out fine.

As I'm a new user of this forum, how can I upvote your answer? I'll mark my issue as solved.

---

### Post by anaypat on 2024-10-21
> **yancek said:**
> Doesn't work!!  That's not useful.  If you haven't resolved this problem with the changes suggested in the post above, explain exactly what happens when you select the drive on which you have windows installed in the BIOS.  Both your installs (Ubuntu/windows) are EFI and have EFI partitions on their respective disk so should boot when you select the respective drive.

Sorry, I should have been more detailed, I meant that the same issue persisted. Disabling the "Enable Legacy Option ROMs" from BIOS boot menu as suggested by @tea for one did the trick. Thanks for your insights too!

---


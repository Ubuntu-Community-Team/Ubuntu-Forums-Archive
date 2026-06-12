---
title: "GRUB Rescue Error: unknown file system"
date: 2019-10-26
forum: Installation &amp; Upgrades
---

### Post by SpikeLS6 on 2019-10-26
Did the upgrade to 19.10 on my laptop with no issues. However, after install and reboot my PC gives me an error of "grub _file_filters" not found.
Entering rescue mode.

At the "grub rescue>" prompt I used 'ls' to identify which drive had Ubuntu on it which for mine is (hd0,msdos1).

At the prompt I typed: set prefix=(hd0,msdos1)_boot/grub.

At the next prompt I typed: insmode_normal. It returned an error of 'unknown command'.

At the next prompt I typed: normal. It again returned an error of 'unknown command'.

What command is it looking for?

---

### Post by yancek on 2019-10-26
Not sure exactly what you did here but there is no letter 'e' in the command nor an underscoree:  insmod normal

---

### Post by SpikeLS6 on 2019-10-26
I misspelled insmod and put to underscore to indicate a space.
I went back in typed: insmod normal. It returned an error: 'guub_file_filters' not found.

---

### Post by SpikeLS6 on 2019-10-26
Ugh, laptop keyboards. the error is 'grub_file_filters' not found.

---

### Post by oldfred on 2019-10-26
No spaces either:

If you're in the GRUB rescue shell the commands are different, and you have to load the normal.mod and linux.mod modules:
grub rescue> set prefix=(hd0,1)/boot/grub
grub rescue> set root=(hd0,1)
grub rescue> insmod normal
grub rescue> normal
grub rescue> insmod linux
grub rescue> linux /vmlinuz root=/dev/sda1
grub rescue> initrd /initrd.img
grub rescue> boot

If not:
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by SpikeLS6 on 2019-10-26
Followed the following commands:
   grub rescue> set prefix=(hd0,1)/boot/grub
grub rescue> set root=(hd0,1)
grub rescue> insmod normal. Gave error of: 'grub_file_filters' not found.

Tried to boot the PC with the Boot Repair disk, but  screen comes up to:
   error: symbol 'grub_file_filters' not found.
   Entering rescue mode...
   grub rescue>

Rebooted the PC and the Grub  Loader came  up, clicked on Ubuntu and the normal desktop screen came up.

Next did shut down. Tried turning on the PC and got the same 'grub_file_filters' not found error. Had to get into the BIOS, find the SSD Linux is on, and it came up through the Grub loader and operated normally.

Tried to use the Grub Repair tool, but it did not work. Does this need to be done in Terminal?

---

### Post by SpikeLS6 on 2019-10-26
Followed the following commands:
   grub rescue> set prefix=(hd0,1)/boot/grub
grub rescue> set root=(hd0,1)
grub rescue> insmod normal. Gave error of: 'grub_file_filters' not found.

Tried to boot the PC with the Boot Repair disk, but  screen comes up to:
   error: symbol 'grub_file_filters' not found.
   Entering rescue mode...
   grub rescue>

Rebooted the PC and the Grub  Loader came  up, clicked on Ubuntu and the normal desktop screen came up.

Next did shut down. Tried turning on the PC and got the same 'grub_file_filters' not found error. Had to get into the BIOS, find the SSD Linux is on, and it came up through the Grub loader and operated normally.

Tried to use the Grub Repair tool in Terminal. The Repair common problems tab gave me a screen saying the Grub problem is fixed. I created a Boot Info Summary: [https://paste.ubuntu.com/p/yqSvWjC352](https://paste.ubuntu.com/p/yqSvWjC352)

I can now have either Ubuntu or WIN 10 on a separate SSA load from the Grub Loader. Think this problem can be considered SOLVED.

Thank you1

---

### Post by oldfred on 2019-10-26
You may have had two different grub installed in each MBR and only one was valid.

Better with Windows 10 to have Windows boot loader in Windows drive & grub boot loader in Ubuntu drive.
Grub only boots working Windows, so sometimes you may have to directly boot Windows and see if you can get into its repair console. But still good idea to have a Windows repair disk or installer with repair console.

---

### Post by SpikeLS6 on 2019-10-27
Thank you for the information. I'll look for a Windows 10 Repair Console Disk or perhaps download one on USB.

---

### Post by oldfred on 2019-10-27
Windows 10 repair disk
[https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795](https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795)
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)
Rescatux live cd with a grub restore option (through rescueapp) fixed it!
Will now repair Windows BIOS & UEFI
[https://askubuntu.com/questions/1058806/tried-to-install-both-windows-and-ubuntu-now-neither-will-boot](https://askubuntu.com/questions/1058806/tried-to-install-both-windows-and-ubuntu-now-neither-will-boot)

---


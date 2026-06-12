---
title: "ZFS not activated correctly and Windows not start anymore."
date: 2022-05-10
forum: Installation &amp; Upgrades
---

### Post by semprini2 on 2022-05-10
Hi,

I have the mobo that boot in cms mode. 
Windows start only if i select the uefi boot entry "Windows boot manager" and Ubuntu start (with grub) only if i select ahci disk.
Grub doesn't start windows. If i select windows the pc restart itself.

[LIST=1]
[*]I am not sure if boot-repair can set up grub correctly. Especially with windows. What do you think?
[*]I have an zfs pool where i store my nextcloud data. It was created with nexclod-vm script. Further i have attach another drive as mirror. Grub-repair report that ZFS is not activated correctly. What does it means?
[/LIST]

[https://paste.ubuntu.com/p/q4RkyDBZ9c/](https://paste.ubuntu.com/p/q4RkyDBZ9c/)

Thank you  anyone in advice.):P

---

### Post by yancek on 2022-05-10
Lines 18-29 in boot repair show the contents of the EFI partition which have the windows AND ubuntu efi boot files so you need to have the BIOS firmware set to EFI boot.  From Ubuntu, run the command:  sudo efibootmgr -v.  You should see the entries for windows and ubuntu there.

>   [FONT=fixedsys]1) I am not sure if boot-repair can set up grub correctly. Especially with windows[/FONT]

Yes, it can.  If you look at the /boot/grub/grub.cfg file in Ubuntu, you will see several entries for Ubuntu.  In each, there will be a line beginning with the word "linux" which points directly to the kernel.  In the windows entry, you will not see this but will see a line beginning with the word ' chainloader".  This means Grub directly boots the Linux kernel while the chainloader command simply points to where the windows boot file should be and turns the boot over to the windows bootloader.  If your windows boot files are corrupted, you cannot repair it with boot-repair or any other Linux tool but need to use windows tools to do that.  Since you can boot windows when set to UEFI, that is not a problem in your case.r

Does windows boot if you have ahci enabled in the BIOS?

I can't help with the ZFS problem, never used it.

---

### Post by vifen on 2022-05-15
Hey, do you still have this problem ? Maybe I could help.

[COLOR=#000000][FONT=Arial][COLOR=#a9a9a9][SIZE=1]______________________________
[/SIZE][/COLOR][[COLOR=#a9a9a9][SIZE=1]ShowBox[/SIZE][/COLOR]]("https://showbox.red/") [[COLOR=#a9a9a9][SIZE=1]Tutuapp[/SIZE][/COLOR]]("https://tutuapp.win/") [[COLOR=#a9a9a9][SIZE=1]Mobdro[/SIZE][/COLOR]]("https://mobdro.onl/")[/FONT][/COLOR]

---


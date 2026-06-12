---
title: "A way around grub rescue to Live USB? Is there one?"
date: 2022-02-13
forum: Installation &amp; Upgrades
---

### Post by ozark_hillbilly on 2022-02-13
After installing Ununtu 20.04 LTS from a Live USB I did
the dumbest thing I have ever done on a computer.
I did not realize pulling out the Live USB from the port
BEFORE hitting the Reboot prompt displayed at the end of the install
 caused a series of characters to scroll quickly up the screen!

Bad news for me. It jacked the bootloader sideways as a result.
Is there away around this? I select boot off USB after stopping it
but the grub rescue prompt still happens after that.

error: file boot /boot/grub/i386-pc/normal.mod not found. 

Way to go me!!!!!

edit - i went thru all the grub commands: set boot/set prefix hd0 hd1 choices with various errors:

unknown filesystem, unknown command 'normal', not an assignment,
error: file /boot/grub/i386-pc/normal.mod not found.

I bricked this thing but good.....lol

---

### Post by oldfred on 2022-02-13
Usually the last thing is installing grub and deleting apps (those you do not now need, but I often have to reinstall like gparted).
You can try reinstalling grub.
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)         

If some apps are half uninstalled you may need other repairs.

---


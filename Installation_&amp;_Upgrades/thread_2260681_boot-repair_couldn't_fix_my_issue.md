---
title: "boot-repair couldn't fix my issue"
date: 2015-01-13
forum: Installation &amp; Upgrades
---

### Post by ashu2 on 2015-01-13
I have HP Envy 700-430QE desktop with Window 8.1. Ubuntu is installed successfully. I am facing issues with the GRUB or boot loader. GRUB2 is also installed but i am facing some strange behavior:
1) If i select Ubuntu in GRUB2 screen - it loads successfully. After restart-it comes back to GRUB2 screen only. Ubuntu is my default choice.
2) But if i load Windows 8.1-it also loads successfully but after restart from the windows - Windows simply changes the boot loader order in my BIOS(it's AMI BIOS). Then i have to manually move Ubuntu higher than Windows boot loader...but anytime if i go into Windows - Windows simply changes the bootloader order and moves Windows Bootloader above ubuntu.

This is a OEM-windows 8.1 pre-installed PC. I have done manual partitions for ubuntu-"/" and one for swap.
Then i tried boot-repair and the pastebin URL is:
[http://paste.ubuntu.com/9736330/](http://paste.ubuntu.com/9736330/)

boot-repair couldn't change this behavior too....As of now - anytime i need to load ubuntu-i need to go into BIOS...change the bootloader and then go to ubuntu.

Any help - would be highly appreciated. I am using live USB to install ubuntu desktop.It's 64 bit version.
Snapshot of my BIOS bootloader screen
[IMG]https://plus.google.com/u/0/107935990403047532803/posts/ABh9sEpK3Dr?pid=6103972550387111010&oid=107935990403047532803[/IMG]

---

### Post by ashu2 on 2015-01-13
It's fixed now.:p
I had forgotten to read these lines in my boot-repair report:
[FONT=arial]If your computer reboots directly into Windows, try to change the boot order in your BIOS.[/FONT]
[FONT=arial]If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.[/FONT]
[FONT=arial]For example you can boot into Windows, then type the following command in an admin command prompt:[/FONT]
[FONT=arial]bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi

[/FONT]After executing 
[FONT=arial]bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
[/FONT]'in my Windows 8.1 command prompt - it's been fixed now....and everything is working as expected.

---


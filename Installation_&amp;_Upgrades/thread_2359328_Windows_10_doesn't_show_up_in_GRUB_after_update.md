---
title: "Windows 10 doesn't show up in GRUB after update"
date: 2017-04-22
forum: Installation &amp; Upgrades
---

### Post by icedrunk on 2017-04-22
I have a laptop (Dell Inspiron 14R 3540) which has dual boot with Windows 10 and Ubuntu 14.04. Last week, I left it updating my Windows during the night, but in the next day, I couldn't boot Windows like I used to. When I turned my laptop on, it booted Ubuntu automatically, and when I opened Grub, it only showed Ubuntu on the list.

Also, whenever I turn on my laptop, a Dell splash screen shows up (it showed up since I dual-booted my laptop, but it used to function without any problems) and any button I press doesn't do anything but directly boot Ubuntu, unless I press F1, which opens Grub sometimes. That means that I can't even open the BIOS even if I press the usual button to access it (which used to be F2). And, for some reason, I can see all my Windows files while using Ubuntu, accessing a device called "OS".

I ran Boot Info Script and got this: [https://pastebin.com/SXXE8X7j](https://pastebin.com/SXXE8X7j)

Does someone know how can I solve this? *sudo update-grub *got me nothing.

---

### Post by oldfred on 2017-04-22
It looks like you have an UEFI system with Windows & Ubuntu in UEFI boot mode.
But you now have grub installed to MBR for BIOS boot.  

The old bootinfoscript has not been maintained. There is a new fork and the newer fork is included in Boot-Repair's summary report.
       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
    
 Updated fork  as original bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

---

### Post by icedrunk on 2017-04-23
Hello, sorry for the late reply.

Here is the pastebin generated with Create Boot-Info: [http://paste.ubuntu.com/24443801/](http://paste.ubuntu.com/24443801/)

---

### Post by oldfred on 2017-04-23
It is not showing all the normal Windows boot files in the NTFS partition(s). At least it is not showing the /Boot/BCD.
But if hibernated it may not show all the files.
But you have Windows installed in UEFI boot mode.
And you have Ubuntu installed in BIOS boot mode.

UEFI & BIOS are not compatible. Once you start booting in one mode, you cannot switch.
Or from grub menu you can only boot other systems in same boot mode.
But you should be able to dual boot from UEFI boot menu. With BIOS/CSM/Legacy on, it should boot grub/Ubuntu. But with only one install as boot options, it may not show grub menu.
And if you have UEFI on, does Windows boot?

You also have a separate /boot partition for Ubuntu. With most standard desktop installs that is not required. Often used with LVM or encrypted drives.

---

### Post by icedrunk on 2017-04-23
I used to boot Windows through a separate boot selection menu, accessible through the Dell splash screen. This menu showed a list of possible devices to boot in Legacy mode (like hard drive, USB stick, etc) and systems I could boot in UEFI mode. By choosing to boot via the Hard drive, I was able to boot Ubuntu, and there was also an option to boot Windows in UEFI mode (somewhat similar to the boot order selection menu avaliable in BIOS). But now I can't access this menu anymore, and now I can only boot Ubuntu through Grub.

Should I reinstall Ubuntu, now in UEFI mode? What should I do?

---

### Post by oldfred on 2017-04-23
You were using the UEFI boot menu.
Whenever Windows does updates and turns on fast start up, you have to directly boot Windows.
If fast start up is off, & grub/Ubuntu is in UEFI mode you can also boot Windows.

If drive is gpt, you can use Boot-Repair's advanced mode to convert Ubuntu from BIOS/CSM to UEFI boot.
You have to boot Ubuntu installer in UEFI mode and use ppa to add Boot-Repair.
All it really does is uninstall grub-pc(BIOS) and install grub-efi-amd64(UEFI).

---


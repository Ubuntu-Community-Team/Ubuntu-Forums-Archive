---
title: "Windows fails to boot at GRUB menu, Windows 8 + Ububtu 14.04"
date: 2014-07-29
forum: Installation &amp; Upgrades
---

### Post by briansfractal on 2014-07-29
Hi

I have a windows 8 desktop and I want to be able to dual boot windows 8 and Ubuntu.

I followed the installation steps listed by [Rodrigo Martins]("http://askubuntu.com/users/21195/rodrigo-martins") at this link: [http://askubuntu.com/questions/302680/how-do-i-install-ubuntu-alongside-uefi-enabled-windows-8](http://askubuntu.com/questions/302680/how-do-i-install-ubuntu-alongside-uefi-enabled-windows-8)
When I choose Ubuntu at the GRUB menu, Ubuntu starts and seems to work fine but 
if I instead select "Windows boot manager" (the only option related to loading windows), the following appears
/EndEntire
filepath: /ACPI(a0341d0,0)/PCI(2.1f)/Sata(0,fff,0)/HD(1,800,fa000,a29e6e0869105d43,2,2)
/File(\EFI\Microsoft\Boot)/File(bootmgfw.efi)/EndEntire
error: cannot load image

press any key to continue...

and then goes back to the GRUB menu

Then I installed BootRepair using the 2nd option from: [https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)
and used the recommended repair. Yet the problem persists.

I also got a URL from BootRepair, paste.ubuntu.com/7892022

If you can help me out, that would be SUPER COOL :D

---

### Post by ubfan1 on 2014-07-29
Looks like bug 1091464 if you have secure boot enabled.  Turn off secure boot and see if grub can then boot Windows.

---

### Post by briansfractal on 2014-07-29
I disabled secure boot in the BIOS and still has the same problem :-|

---

### Post by oldfred on 2014-07-29
Boot-Repair tells you this:

> Windows is hibernated, refused to mount.
Failed to mount '/dev/sda5': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume


You cannot leave Windows 8 hibernated and if fast boot is on, it is always hibernated.

       WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked

You also show parts of XP boot files (ntldr) in both the efi partition and your Windows. XP will not work on gpt partitioned drives. Did you copy install from an old XP install?

---

### Post by briansfractal on 2014-07-29
[COLOR=#ff8c00]Did you copy install from an old XP install?
[/COLOR]Nope. I bought this desktop with windows 8 pre-installed.
The fast startup and hibernate options are already unchecked. 
(I double checked and they still are)

---

### Post by briansfractal on 2014-07-29
So I was reading other forums and trying stuff. In GParted, I accidentally turned all of my partitions into unallocated space. I then restored Windows 8 to the factory image with my back up USB stick,
then followed the instructions for installing Ubuntu here: [http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
and now i can dual boot Windows 8 and Ubuntu 14.04 from GRUB. Problem solved ^_^

---


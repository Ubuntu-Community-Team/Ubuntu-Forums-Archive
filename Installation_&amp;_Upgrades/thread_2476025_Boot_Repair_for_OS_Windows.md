---
title: "Boot Repair for OS Windows"
date: 2022-06-14
forum: Installation &amp; Upgrades
---

### Post by andrewkim001 on 2022-06-14
I am inexperienced with Ubuntu and decided to dive in to a Odin Project Full Stacks Javascript course for the summer but when installing Ubuntu, I encountered problems with dual booting Ubuntu and Windows. After installing Ubuntu I was unable to reboot Windows and I have been using the boot repair systems in Ubuntu to try and get the original operating system back. I also tried to use the command prompt to open the Ubuntu boot repair and &#8220;repair the windows OS&#8221; in advanced settings, but the option remained grayed out. I don't mind if I have to lose all the data within my hardware, Im just stuck in an OS I don't know how to operate and I cant even figure out how to hard reset. :(

Thank you, I really appreciate any help right now.

Boot Repair:

[https://paste.ubuntu.com/p/MwHPVP7rJG/](https://paste.ubuntu.com/p/MwHPVP7rJG/)

---

### Post by TheFu on 2022-06-14
I cannot help with Windows stuff, except to say that you really should have used a virtual machine, not a dual boot install.  We do installfests at the local university and always, always, push for people new to Unix/Linux to use a virtual machine for the first 6 months.  There are too many reasons to list for this recommendation, but the main one is that inside a virtual machine, you won't screw your host OS up and your hostOS won't screw up a dual boot config a few times a year as commonly happens with any MSFT stuff.

Some other people will need to look at your paste. I don't have a login to see it.

---

### Post by andrewkim001 on 2022-06-14
I will definitely install Ubuntu through a virtual machine. I didn't realize how complex and compromising, installing a dual boot system can be to the initial operating system. I guess I just need to figure out how to set the system back to Windows to be able to set that up.

---

### Post by oldfred on 2022-06-14
You show no Windows install on sda. Do you have another drive with Windows?
You have an UEFI system and now have UEFI Secure Boot enabled. 
And you have installed Ubuntu to entire hard drive in the old BIOS/MBR configuration which erased drive.
How you boot install media, UEFI or old BIOS is then how it installs.

Installer would have given you warning that you were erasing entire drive. 

Since you have UEFI hardware, you need to create a new Windows UEFI installer. Best to do that from another Windows system as Windows .wim file is over 4GB and does not fit on a FAT32 partition. But you have to have a FAT32 partition with esp flag & Windows boot files. Windows tools take ISO and split the .wim file into two parts. A very few Linux tools can be used with newest instructions, but any older instructions from when .wim file was smaller will not work. 
Your Windows product key is now stored in UEFI, you to have a legal Windows install, you must use UEFI, if Windows was pre-installed.

If you turn off UEFI Secure Boot, you should be able to boot Ubuntu in old BIOS mode. But I would plan on just reinstalling in UEFI mode after you reinstall Windows in UEFI mode and convert drive to gpt partitioning.
Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drives since 2012 or for last 10 years. BIOS mode should not be used. 

You did have good backups of your data? 
If not some with Windows have said Windows recovery tools work better.

---

### Post by yancek on 2022-06-15
Boot repair can simply add a chainloader line to the menu in the grub.cfg file on Ubuntu and can't really repair the windows proprietary system boot files.  As oldfred has pointed out, you appear to have made an incorrect choice in the installer and have no windows boot files so even this simple step cannot be done by boot repair.

Are you familiar with UEFI?  If not, read up on it.  Did you do an online search for dual booting windows and Ubuntu?  There are literally hundreds of tutorials such as the one at the link below explaining the process.  I'd suggest reading through it and maybe finding a few more sites with explanations and reading them before reinstalling.

>  I didn't realize how complex and compromising, installing a dual boot system can be to the initial operating system.

It can be, but as pointed out above, the problem here is making the wrong choice with the installer.  Based on the output of boot repair, you will not be able to get back the original windows system due to this choice but need to reinstall both windows and Ubuntu.

---

### Post by pbear42 on 2022-06-15
To answer your question, the way one reinstalls the Windows boot loader is by getting to a command prompt, e.g., with a recovery or installation drive, then running [COLOR=#ff0000]bcdboot C:\Windows[/COLOR] (assuming C: is the system drive) ([about]("https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/bcdboot-command-line-options-techref-di?view=windows-10")).  This copies the boot loader files from backup on the system drive and, on a UEFI system, moves Windows to the top of the boot list.  That's not going to work, though, if you inadvertently uninstalled Windows.

By the way, the only times I've seen a UEFI-capable computer with Windows installed in BIOS mode is when the original OS was Win7.  Is that your case?

---

### Post by bingodingo on 2022-06-21
Hi Andrew,

If you have access to a Windows computer the easiest way to reinstall Windows is to create a Windows media creation usb (follow directions at e.g. [https://www.microsoft.com/en-au/software-download/windows10ISO](https://www.microsoft.com/en-au/software-download/windows10ISO)), restart your target computer booting from the usb and follow the prompts.
(Pay attention to oldfred's comments above, there's some detail there you need to follow.)
Then, Ubuntu on a virtual machine.

Alternatively, abandon the dark side altogether and learn to use your shiny new Ubuntu computer. 

Good luck

---

### Post by TheFu on 2022-06-22
> **bingodingo said:**
> Hi Andrew,

If you have access to a Windows computer the easiest way to reinstall Windows is to create a Windows media creation usb (follow directions at e.g. [https://www.microsoft.com/en-au/software-download/windows10ISO](https://www.microsoft.com/en-au/software-download/windows10ISO)), restart your target computer booting from the usb and follow the prompts.
(Pay attention to oldfred's comments above, there's some detail there you need to follow.)
Then, Ubuntu on a virtual machine.

Alternatively, abandon the dark side altogether and learn to use your shiny new Ubuntu computer. 

Good luck

Or install Ubuntu first, have it take the entire HDD (backup anything you don't want to lose), then use the extremely stable hypervisors that are available on Linux to run Windows inside a VM.  I've been running Windows inside a VM about 15 yrs. Even had Windows Media Center running in a VM.  But ... if you are a Windows gamer or need to earn your living using Adobe video or photo tools, then you'll want to setup dual boot or Windows directly on the hardware.  There are methods to run Windows inside a Linux hosted VM, but when it comes to high-end graphics or graphics performance, this stuff is still a bit of a black art to get working and requires dedicated GPUs for the host and the VM.

For just putting your toes into Linux and keeping Windows, then create a virtual machine for Linux systems using Virtualbox.  You'll want to allocate 40G at a minimum for the current 22.04 Gnome desktop install. That doesn't leave much room for lots and lots of extra data files (especially huge media files), but it will be fine if you just work with typical office files, emails, and web surfing.

---


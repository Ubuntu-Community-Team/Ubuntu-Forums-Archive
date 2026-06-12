---
title: "Trying to boot EFI system"
date: 2014-08-05
forum: Installation &amp; Upgrades
---

### Post by rxt on 2014-08-05
I have a new laptop with UEFI. I want to boot into Ubuntu from the harddisk. The harddisk is empty, and can be partitioned in any way to get it working. 

This is what I did:

* Startup Live stick with Ubuntu
* Install Ubuntu on the ssd
* Reboot - but that doesn't work
* Startup the Live stick one more time (12.04)
* Install and run Boot-repair
* When this "succeeded", rebooted again, to see the following message: 

Windows Boot Manager boot failed
Default Boot Device Missing or Boot Failed.

Then I enter the Boot Manager, with one option, which goes back to the first message about "Windows Boot Manager boot failed".

You can see the following Pastebin from Boot-repair.

[http://paste.ubuntu.com/7964206/](http://paste.ubuntu.com/7964206/)

This is a Lenovo Ideapad Flex 10 which is a 64 bit system, but needs a 32 bit EFI. That 32 bit EFI is needed to get the live stick working. Today I started reading a Grub manual, but that was a manual that mentioned Ubuntu 6.10, so that is eight years old, and EFI was not an issue back then. 

So I'm a bit stuck. What can I do to get this computer to boot into Ubuntu directly?

---

### Post by sudodus on 2014-08-05
I'll have a look at your pastebin link.

Meanwhile you can have a look at this link (aiming at a USB pendrive, but general enough to help you find what might be missing in your system. By the way, do you have Windows in your computer?
[URL="http://ubuntuforums.org/showthread.php?t=2213631"]
Portable installed system that boots in UEFI as well as in BIOS mode[/URL]

---

### Post by sudodus on 2014-08-05
Why did you install LVM? And why did you install in UEFI mode?

And can you please tell us exactly the name of the Ubuntu iso file, that you used?

For example:
ubuntu-14.04-desktop-i386.iso or ubuntu-14.04-desktop-amd64.iso
ubuntu-14.04.1-desktop-i386.iso or ubuntu-14.04.1-desktop-amd64.iso

You can also have a look at the following links

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389") post #2

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[URL="http://ubuntuforums.org/showthread.php?t=2147295"]
UEFI Installing - Tips[/URL]

---

### Post by grahammechanical on 2014-08-05
> [COLOR=#000000]This is a Lenovo Ideapad Flex 10 which is a 64 bit system, but needs a 32 bit EFI. [/COLOR]

You might want to read this thread from last year and the link that it points to. Do not get your hopes up.

[http://ubuntuforums.org/showthread.php?t=2193622](http://ubuntuforums.org/showthread.php?t=2193622)

[http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)

> [COLOR=#3E3E3E][FONT=Trebuchet MS]A 64-bit OS can only boot on 32-bit UEFI if it has very ugly compatibility hacks, including having to rewrite structures and register state every time it makes a UEFI call.[/FONT][/COLOR]

> [COLOR=#3E3E3E][FONT=Trebuchet MS] Having looked into what it'd take to implement it in Linux, I decided that hammering rusty nails through my feet would be a preferable use of time. Thankfully, I went drinking instead.[/FONT][/COLOR]

> [COLOR=#3E3E3E][FONT=Trebuchet MS]32-bit UEFI. Just say what on earth were you thinking, please, no, can't you find a solution that doesn't involve me getting tetanus jabs.[/FONT][/COLOR]

And that is from the Linux developer that did a massive amount of work to make it possible to install and run Linux on a machine with secure boot enabled. He knows his stuff.

Regards.

EDIT: I found this

> [COLOR=#252525][FONT=sans-serif] As of version 3.15, [/FONT][/COLOR][Linux kernel]("http://en.wikipedia.org/wiki/Linux_kernel")[COLOR=#252525][FONT=sans-serif] supports booting of 64-bit kernels on 32-bit UEFI implementations running on[/FONT][/COLOR][x86-64]("http://en.wikipedia.org/wiki/X86-64")[COLOR=#252525][FONT=sans-serif] CPUs, with [/FONT][/COLOR]*UEFI handover support from a UEFI boot loader as the requirement.*

[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

[http://kernelnewbies.org/Linux_3.15#head-e6cf8178e4d5eafc23b0abda81974d2b71ffecf4](http://kernelnewbies.org/Linux_3.15#head-e6cf8178e4d5eafc23b0abda81974d2b71ffecf4)

[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)

Try again with Ubuntu 12.04.5 or 14.04.1.

---

### Post by rxt on 2014-08-08
Thanks for the replies. Time for an update. 

**@****sudodus**: I've reinstalled without LVM, so I guess that is not a problem anymore. When I enter the BIOS, I only see UEFI, and I cannot select another option. I can disable secure boot, which I have done. On this disk I don't have Windows installed. It's a new disk. I can reformat it if needed and have done so several times. I have another disk with Windows 8.1 installed, which I can put back if that makes it easier. 

Today I tried to get it working, but no success yet. What I did is the following:

I reformatted the disk following this guide, with sda2 as EFI partition, sda3 for the installation. 
[http://phillw.net/isos/linux-tools/uefi-n-bios/UEFI-n-BIOS-installed-system.txt](http://phillw.net/isos/linux-tools/uefi-n-bios/UEFI-n-BIOS-installed-system.txt)

Then I installed Ubuntu 14.04.1 on sda3. I rebooted the usb stick, this time 12.04 to use boot-repair, which doesn't install on 14.04. If it's better to install 12.04 that's fine and I will do that, but I guess that boot-repair can do its work on 14.04 as well. 

I ran boot-repair. First I tried with WinEFI, resulting in this pastebin. This didn't boot.
[http://paste.ubuntu.com/7964206/](http://paste.ubuntu.com/7964206/)

I tried another time, without WinEFI. See [http://paste.ubuntu.com/7992134/](http://paste.ubuntu.com/7992134/)

For the livestick I use the following 32 bit EFI: [https://github.com/jfwells/linux-asus-t100ta/blob/master/boot/bootia32.efi](https://github.com/jfwells/linux-asus-t100ta/blob/master/boot/bootia32.efi)

**When I copy this to /EFI/BOOT on the livestick, it works. So why can't this work on the normal disk? **

I started the livestick, started the diskmanager, mounted sda2 (EFI), copied the EFI folder to EFI-BACKUP (which is what you see in the pastebin), removed the Microsoft folder inside, removed the bootx64.efi and copied the bootia32.efi file to /EFI/Boot/bootia32.efi. Then I rebooted, and entered grub. That is not so strange as this is probably the result of the boot-repair, but still I wonder how I can get to use this working 32 bit EFI on the normal harddisk. I can remove that EFI-BACKUP or put it back. 

**Can I instruct GRUB to use the bootia32.efi? How do I do that? **

---

### Post by rxt on 2014-08-09
Yesterday I didn't realize that I got it working. The grub commandline loaded, and that meant that I was able to boot. I booted from the grub commandline today, so I'm just a small step away from having the system booting normally. I guess I will get that working as well. 

Thanks for the input. The formatting guide was the key. Well that and the fact that last week I realised that I needed to learn what grub did, so I read a manual, and those two combined helped me out.

---


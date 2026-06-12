---
title: "Partitioning for 5-way boot (3x Windows, OSX, Ubuntu) on single HDD?"
date: 2011-11-26
forum: Installation &amp; Upgrades
---

### Post by XSaenen on 2011-11-26
Sorry if this is in the wrong section, but I couldn't think of any other that might suit it.  I'm also aware that this is not strictly an Ubuntu-related question either.  
However it does involve Ubuntu, and I'd prefer to ask it here because people here tend to use other OSses and multiboot as well.

I'm preparing to put Ubuntu, XP, Vista, Win7 and OSX on my netbook in a 5-way boot configuration.  Ubuntu would be the main OS.
Installation order would be XP, Vista, Win7, OSX, then finally Ubuntu.  Right now XP is installed on a 30GB partition, the rest of the HDD is still unallocated.

If memory serves me right, you can only create 4 primary partitions on a HDD.  MS systems requre a primary partition.
That means 3 primaries are taken.  

What do I do with the rest of the partitions?  How do you suggest to set those up?  Keep in mind that I would like one more partition for data.

---

### Post by oldfred on 2011-11-26
We cannot help on OSX as that is against the ToS unless this is a Mac.

Why would you want Vista & 7?

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Ubuntu works just fine from logical partitions and Windows will read NTFS logical partitions. If you install a second copy of Windows to a logical partition, it will have to have its boot files in a primary as shown in the Multibooters site.

Windows will not boot from a gpt drive unless you boot with UEFI. I use gpt with Ubuntu but have windows on a separate msdos drive.

---

### Post by kurt18947 on 2011-11-26
The boot manager I use will do what you want but it's shareware/have to buy it.  If you google 'terabyteunlimited bootitbm' you'll find it.  It'll support over 100 partitions and each is isolated unless you choose otherwise.

---

### Post by XSaenen on 2011-11-26
My apologies Oldfred, I should have read the ToS first.  :oops:

It looks like the OSX route is not going to happen anyway, as it requires way too much work to get the OS to accept this chipset.

Quad boot it is then, and that is working out just fine so far.
In fact I have all 3 MS versions working and just finished the Ubuntu install.  Looks like Grub is telling me to choose between Ubuntu and Win7.  I presume the latter choice will load the Windows bootloader.  

As to why I need Vista and Win7 : For some reason I'm the guy my friends come to when they have a Windows-related problem.  Seeing as I don't know all the subtle differences between them from the top of my head, it can be handy to have both on the same machine.
And besides, I actually like Vista.

---

### Post by oldfred on 2011-11-26
Actually grub skips the Windows boot loader and jumps to the PBR - partition boot sector, just like the Windows boot loader would. The Windows boot loader knows which partition to jump to by the boot flag (active partition in Windows).  Grub's os-prober looks for boot files and sets up a grub boot stanza to boot into that system.

If you installed all three Windows, then each extra install added its boot files to the active partition. Since you have Vista/7 it updates the BCD with all the choices in Windows that you can boot. Do not ever delete the active partition or you will lose all the capability to boot the other installs.

---

### Post by XSaenen on 2011-11-26
Thanks for the warning.  

I'm currently running it in quad boot.  3x windows and Ubuntu.

Here's the current HDD layout (single 250GB disk) :

```

/dev/sda1 - NTFS - XP partition - 30GiB - Flags : boot
/dev/sda2 - NTFS - Vista partition - 30GiB
/dev/sda3 - NTFS - Win7 partition - 30GiB
/dev/sda4 - Extended - 29.56GiB
 /dev/sda5 - Linux-swap - 976MiB
 /dev/sda6 - ext4 - Ubuntu partition - 28.61GiB - Mount Point : /
```

That leaves me with 113.32GiB unallocated, which will become my actual data partition.  
The idea is to tell each OS to save pictures, music etc in specific folders there, so that when I save a picture in one OS it'll show up in the pictures folder in any other OS.  
I'll look into that when the time comes, first I have some other stuff to sort out.  Like all the updates for 4 operating systems, installing applications, etc.

On boot I now get the following options in GRUB2 :

```
Ubuntu, with Linux 2.6.32-35-generic
Ubuntu, with Linux 2.6.32-35-generic (recovery mode)
Ubuntu, with Linux 2.6.32-33-generic
Ubuntu, with Linux 2.6.32-33-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)
```

If I click the latter, I get a new screen (titled : Windows boot manager) with the following options :

```
Earlier version of Windows
Windows 7
Microsoft Windows Vista
```

The first would be the XP, the 2 others allow me to specify advanced options via F8 (Repair, safe mode, etc)

The only real quirk is that both Vista and Win7 use the Vista boot screen, but I already did my homework on that.  Apparently it's the lack of a 7 locale in the Vista BCD, but that seems to be an easy fix.

As for GRUB2 : I'm looking into the scripting tutorials.  Maybe I can tell it the location of each OS so I can boot them all from the same menu, or maybe I made a mistake somewhere and will have to start over.  
Apparently Grub2 should show all systems if I install one, then take its boot flag away, then install the next, etc etc until I reach Ubuntu.  It's too late in the evening to try that now, so maybe another time.

Either way, it's a steep learning curve.  Then again I plan on dualbooting (or triplebooting) my other machines as well, so this one is an excellent testcase.  I only really use this netbook to mess about with anyway.

---

### Post by bluexrider on 2011-11-26
> **XSaenen said:**
> My apologies Oldfred, I should have read the ToS first.  :oops:

It looks like the OSX route is not going to happen anyway, as it requires way too much work to get the OS to accept this chipset.

Quad boot it is then, and that is working out just fine so far.
In fact I have all 3 MS versions working and just finished the Ubuntu install.  Looks like Grub is telling me to choose between Ubuntu and Win7.  I presume the latter choice will load the Windows bootloader.  

As to why I need Vista and Win7 : For some reason I'm the guy my friends come to when they have a Windows-related problem.  Seeing as I don't know all the subtle differences between them from the top of my head, it can be handy to have both on the same machine.
And besides, I actually like Vista.

I would have solved the problem by using VM ware like Oracle. But that's me

---

### Post by oldfred on 2011-11-26
You may be able to copy the BCD & bootmgr to Vista & Windows 7. Not sure of the differences between bootmgr & BCD in each. Move boot flag to each and then repair the install. You may need to edit BCD, run fixBoot & chkdsk to update PBR so it is a bootable partition.

I have used a Windows 7 64 bit repair USB to run chkdsk on my XP install but it wrote a Windows 7 PBR. But it still booted even though PBR said bootmgr when for XP it is ntldr. I was able to then run some more windows commands from the repair USB and reinstall a XP PBR.

Even though you may be able to get to repairs from Vista or 7's boot, it is always best to have a repairCD or USB for every system you have installed.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---


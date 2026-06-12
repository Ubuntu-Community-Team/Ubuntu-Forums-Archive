---
title: "remove Windows 7 loader from Grub2"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by ieee488 on 2011-04-28
I had a laptop with Windows 7 and Windows XP dual booting.

I installed Ubuntu 11.04 to the Windows 7 partition.

Now, Grub2 shows Ubuntu and Windows 7 loader as the option.
When I click on Windows 7 loader, I get the choice of booting to Windows XP or Windows 7.

What I want is to have the choice to boot to either Ubuntu or Windows XP directly in Grub2.

How do I do this?

---

### Post by oldfred on 2011-04-28
Are both of your windows installs in primary partitions? Or at least is the XP the only one in a logical? If so then you should be able to do it. 

You need to understand how windows works.
To get each MS to have its own boot loader make a primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

These are new installs, but you may be able to repair XP, but moving boot flag or just copy ntldr, boot.ini & NTDETECT.COM back to your XP install.
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Boot WinXP from extended partition - Herman
[http://ubuntuforums.org/showthread.php?t=1192147](http://ubuntuforums.org/showthread.php?t=1192147)

How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)
Vista Win7 missing boot files meieifra
[http://ubuntuforums.org/showthread.php?t=813628#4](http://ubuntuforums.org/showthread.php?t=813628#4)
meierfra. - How to fix XP when the boot files are missing
How to fix Vista/Window 7 when the boot files are missing post4
[http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4](http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4)

---

### Post by ieee488 on 2011-04-28
Yes, Windows XP is installed on the primary partition. It was the first OS to be installed. Then Windows 7 was installed.

But now, during the install Ubuntu 11.04 detects the Windows 7 bootloader. I don't want the Windows 7 bootloader, since Windows 7 is no longer on the laptop.

How do I get Grub to show only Ubuntu and Windows XP?

---

### Post by oldfred on 2011-04-28
You probably still have the win7 boot files in the XP partition.

XP boot files:
/boot.ini /ntldr /NTDETECT.COM
Win7/Vista boot files:
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

You may want to copy the win7 files somewhere else just in case, but I think you can just delete them. The Partition boot sector may have been converted to a win7 version that looks for bootmgr. XP NTFS boot sectors look for ntldr, so you may have to run fixboot from your XP disk.

---

### Post by ieee488 on 2011-04-28
No, I have the XP boot files.

I had used my XP disk to boot into recovery console, and I executed the fixmbr and fixboot commands. That was fine, and it caused the laptop to boot directly into Windows XP.

So, I rebooted and did the Ubuntu install again. And, again, Ubuntu is picking up the Windows 7 bootloader. I don't get it. The Windows 7 partition was deleted and is being used for Ubuntu.

Where is Ubuntu picking up that Windows 7 bootloader is still around, and how do I get rid of it?

this is my fdisk -l shows
> /dev/sda1   *           1        2941    23623551    7  HPFS/NTFS
/dev/sda2            2942        7296    34980931    f  W95 Ext'd (LBA)
/dev/sda5            2942        4640    13647186    7  HPFS/NTFS
/dev/sda6            4641        6829    17576960   83  Linux
/dev/sda7            6829        7296     3755008   82  Linux swap / Solaris


---

### Post by oldfred on 2011-04-28
Have you done this to update the grub menu?

```
sudo update-grub
```

If that does not work post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by ieee488 on 2011-04-28
I did two things. One was install EasyBCD and use it to install XP bootloader to MBR, and I moved Bootmgr file in C:\ to a different directory based on one of your earlier responses to me. Maybe Ubuntu installer was seeing the Windows 7 bootmgr file and using it instead of using the XP boot files which were also there.

Don't know which one of the actions I took was what fixed the problem - my guess is the moving the Bootmgr file was the one which fixed the problem, but now at the start of the installation, Ubuntu reports seeing Windows XP as it should.

Thank you for your help.

---


---
title: "Ubuntu headaches, grub,debian and the EFI"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by AlienCoffee on 2012-04-30
hello everybody,
I upgraded to precise recently and had so many issues that I would like to share with you my headaches.
My computer is an Acer Aspire 5560 laptop with an amd A4-3300M processor and a built in radeon 6480 graphic card.
Before the upgrade I had Mint 12 installed in dual boot with windows 7.

The First time I installed Precise I went into custom partition mode, formatted the existing linux partition and simply installed Precise there. After reboot I get a black screen that says something like ELF magic error, grub rescue mode. I didn't panic, and I used the live cd to install grub through the command line. The terminal confirmed that grub was successfully installed. I rebooted and got again the ELF error and grub rescue.
The Second time I thought that maybe I had done something wrong, and reinstalled all over again from a different ubuntu spin. Same grub rescue error.
The Third time I tried with another distro. Debian testing installed fine with netinstall. And after installation I even got the grub menu, But the distribution actually couldn't load because of an issue with my GPU (LOL), giving me just a black unusable screen.
The Fourth time I decided that to better understand what was the matter I had to completely clean up my HDD. So, from the ubuntu live cd I destroyed the 3 partitions I had on my HDD: the linux partition, the windows partition, and the windows boot partition. I made just one big partition for ubuntu and I installed it.
This time I got this message that was saying "No Operating System Found".
The Fifth time I reinstalled ubuntu with the option "Install Ubuntu using the whole HDD". Installation went fine and now i even get grub sometimes (this is actually very puzzling, as I get it only every now and then).
 What Ubuntu did that I did not is that it created an EFI partition. So, I'm asking, what do I need an EFI partition for? I have been using linux for years and I never had the need for an EFI partition.
I hope someone will have some explanation for me, or at least some theory XD.

---

### Post by AlienCoffee on 2012-04-30
If anybody is interested, now I got the UBUNTU boot option on BIOS O_O

---

### Post by oldfred on 2012-04-30
BIOS has been the standard since the first PC in the 1980's. The new version is UEFI and UEFI will boot in BIOS mode (at least most systems).
Windows will only boot in UEFI mode with gpt partitioning and UEFI requires the first partition to be the efi (or system boot) partition. It is used by both Windows & grub for a boot file.
Ubuntu will boot with gpt whether BIOS or UEFI. gpt is the new partitioning system replacing MBR(msdos). gpt is required if drive is over 2TiB and recommended for  SSDs.

Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

I do not have UEFI, but am using gpt on smaller drives with BIOS mode. To get grub2 to install correctly with gpt partitioning a small bios_grub partition is required. If booting with UEFI you do not need the bios_grub but have to have the efi partition. 

Someone posted that how you start your install CD or DVD makes the difference on whether you get UEFI install or BIOS install for both Windows & Ubuntu. 

> Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 


Just about everyone that installed correctly with UEFI partitioned in advance.

How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)
efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)
> So, in short: create the partitions on a non-EFI system, mkdir 2 folders and install. If I only knew from the start that it was this simple.


---

### Post by Sda1986 on 2012-04-30
Same here, and I have no idea how delete it.

---

### Post by AlienCoffee on 2012-05-01
ok, interesting. Is this problem related? [http://ubuntuforums.org/showthread.php?t=1969769](http://ubuntuforums.org/showthread.php?t=1969769)
My computer boots up only every second attempt I make. And can't properly shut down :s
Has this anything to do with EFI, etc. and, mostly important, how can I be sure that my computer works with UEFI? Installing Linux Mint either Ubuntu or Debian Edition gave me no problems of any kind, grub installed and worked like a charm, and my computer could start and shutdown...

---

### Post by oldfred on 2012-05-01
If you are not booting with UEFI do not worry about it.

If it is not shutting down properly that is why you may have to boot twice. 

If it hangs on shutdown remember the elephants.

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
Another
sudo init 0

Generally pressing and holding Ctrl+Alt and
then PrintScr, R, E, I, S, U, B (Raising Elephants Is So Utterly Boring)
should do a clean reboot.
R gives back control of the keyboard, S issues a sync, E sends all processes but init the term singal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system

then go back into log files and see if it says why it is not shutting down correctly.
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

### Post by AlienCoffee on 2012-05-03
REISUB didn't work. My computer still hangs on shutdown/reboot. I get only a backlighted black screen.

---

### Post by oldfred on 2012-05-03
Do log files give any clue as to what is not working?

---

### Post by AlienCoffee on 2012-05-03
I know it's embarassing, but I don't know what log I should be looking for... :oops:

any hints? XD

---

### Post by oldfred on 2012-05-03
I thought it wrote shutdown info like it does on startup but now I cannot find it in my system. I do not have any issues, so that may be why?

I would look in /var/log/syslog and dmesg. Look at a few others in /var/log to see if anything looks strange.
The log file viewer only has a couple of files shown.

---

### Post by thomascube on 2012-11-23
Hi,

I've bought too an Acer 5560 and want too dual boot on it. I've got these problems too, such as can't shutdown and can't install a normal grub2 on the same way to an another computer.

My workaround is the following:
I've got a HP G6-1306SH too, which has the same architecture, as the Acer 5560. So, i've put the Acer's HDD into the HP G6 and install first the Windows 7. After that I install the Kubuntu 12.04.1. In the HP both works. After that i've put back the Acer's HDD in the Acer. I've got grub menu at least and the kubuntu starts finally whitout errors. The Windows 7 crashes by the classpnp.sys -> rename it with win7 recovery disk's console to classpnp.sys.old. After that crashes it by disk.sys. Fortunately this can fix by the Win7 repair tool on the install disk. 
And now - after 3 days of probing install - I can use both of OS in the Acer 5560. I think, this is the difference between Acer and HP (no more Acer - for me).

Partitions are the following:
/dev/sda:
sda1 - primary - ntfs - 60GB (boot flag enabled)
sda2 - primary - ntfs - 300GB
sda3 - extended - 105GB :
------ sda5 - logical - ext4 - mount on / - 30GB
------ sda6 - logical - ext4 - mount on /home - 70GB
------ sda7 - logical - swap

With the same technique - just use on Acer - it can't boot. Hopefully i helped you.

---


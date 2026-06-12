---
title: "Fatal error during boot loader installation."
date: 2017-02-09
forum: Installation &amp; Upgrades
---

### Post by gamelord122 on 2017-02-09
I've got a dual drive setup, SSD ~250 GB (where Windows is installed) and HDD 3 TB (just data, mostly game installs).  The SSD is already partitioned from the attempted Ubuntu install, allocating about 55 GB of its total space for my future Ubuntu installation.  I already have Windows 10 installed on this machine, and as much as I hate it, I still need it for a handful of things.  It's important that I don't ruin that Windows install, because it would take me a very long to get it back to the way it is now off of a fresh install, even with everything backed up to my external drive.  Unfortunately, every time I try to install Ubuntu 16.10, either from USB or DVD, I get a fatal error during the boot loader install.  The error prompt that comes up gives me the option to choose another drive, continue without a boot loader, or cancel the installation.  This error window is completely unresponsive; no matter what I choose, the OK button does nothing.

I know I'm not the first person with this issue.  I Googled the problem and saw what others have suggested.  Secure boot is turned off, I'm running the installer in BIOS mode instead of UEFI (because apparently Windows is installed in BIOS mode or something), using a disc instead of a flash drive didn't help, etc.  The only thing I haven't tried is doing the "other installation" option in the installer, because I'm not 100% sure of what I'm doing with those partitions, and like I said, I don't want to mess up my Windows install.  I tried using Boot Repair after it errored out on the boot loader, assuming that the installation may have finished everything except for the boot loader and otherwise been usable.  Boot Repair only really served to destroy my Windows boot loader (which I did manage to restore, so I'm back on Windows as I write this).  If anyone can decipher anything useful from the Boot Repair logs, the url is [http://paste.ubuntu.com/23962022/](http://paste.ubuntu.com/23962022/).

I'd really appreciate any help you guys can offer, because Ubuntu is a much more pleasant OS than Windows 10 once it's up and running, and I look forward to having Windows as far out of my life as possible.  Right now though, I kind of feel like this...

[IMG]https://imgs.xkcd.com/comics/success.png[/IMG]

---

### Post by oldfred on 2017-02-09
Some basics.
Windows only boots from MBR(msdos) in BIOS mode.
Windows only boots from gpt(GUID) with UEFI mode.

Linux will boot from gpt with either UEFI or BIOS boot mode, but requires an ESP on sda to boot in UEFI mode or a bios_grub on any gpt drive where grub is installed.

Boot-Repair's auto fix will try to install grub to every drive. Often with multiple drives that is not best choice, and better to use Boot-Repair's advanced mode to only install one system's boot loader to one drive. You probably want Windows boot loader on Windows drive, & grub installed to MBR of gpt partitioned drive.

You only get a choice on where to install grub(which drive's MBR) with Something Else install option. And if in UEFI mode choice is there, but does not do anything, it just installs to ESP on sda.

So if your system is using BIOS/Legacy/CSM to boot, you need a bios_grub partition on the gpt drive.
I normally when first partitioning a drive put both an ESP & bios_grub as neither is really large & adding an ESP later can be difficult when drive is full of data. UEFI suggests ESP be first, but not absolutely required. But not sure if at end of multi-TB drive if UEFI could find it.

If you want both installs on SSD, you can do that. And just have grub boot and offer to also boot Windows. But Windows 8 & 10 have fast start up or always on hibernation. You have to turn that off, as grub will not boot hibernated Windows. And Windows may turn it back on with updates. So if Windows turns that on, you have to restore Windows boot loader to boot.

You could leave Windows boot loader in SSD, and manually choose to install grub to data drive. Since data drive is gpt, it just needs the bios_grub partition which can be anywhere on drive. It must be 1 or 2MB unformatted with bios_grub flag if using gparted to create it. If using gdisk it is code ef02. 
Once you add bios_grub partition to 3TB drive, and if install is otherwise ok, Boot-Repair's advanced mode will let you choose an install an a drive to install boot loader into. Just select the 3TB drive.

Since data partition is NTFS, the Windows hibernation will also keep that mounted. And if in hibernated state you cannot use Linux NTFS driver to read/write into it. So you may need fast start up off, if wanting to use NTFS with Linux.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by gamelord122 on 2017-02-09
Thanks for your help so far, but I could still use a bit more if you don't mind.

> [COLOR=#000000]If you want both installs on SSD, you can do that. And just have grub boot and offer to also boot Windows.[/COLOR]

That is what I want, and I've got that same setup on two other machines, but they both only have a single storage drive each, plus I set them up that way on fresh installs, so I didn't risk losing any data.

My fear is that if I pick the "Something Else" install option and try to aim GRUB somewhere, it might erase an entire partition rather than just making a few MB of space for a boot loader.  Do you have simple step-by-step instructions for making sure that I get GRUB on my SSD using the Something Else option without overwriting a partition that I need to keep intact?  I followed your link and turned off fast boot, so I should be good to go from that perspective.

---

### Post by oldfred on 2017-02-09
You just in Something Else install grub to sda, if sda is SSD.

Do not install grub to a partition, that is almost always wrong as BIOS systems can only boot from MBR. So never install to sda1, or sda2 etc.
And the only way you can damage Windows is if you select to install grub to a Windows partition's boot sector. 
Windows has essential boot code in the partition boot sector.

       Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by gamelord122 on 2017-02-09
Thank you so much!  That's exactly what I needed, and it all appears to be working now.  It's a shame that boot loader fatal error window is unresponsive; hopefully that gets fixed so that others like me can avoid this headache in the future.

---

### Post by oldfred on 2017-02-09
You can change to [Solved].

Glad you got it working. Not sure what issue is with grub not installing correctly..

---


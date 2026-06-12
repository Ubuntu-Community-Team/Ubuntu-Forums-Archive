---
title: "Installer does not detect SSD and HDD: Ubuntu 16.04 LTS on Lenovo Legion Y520-15IKBN"
date: 2017-04-21
forum: Installation &amp; Upgrades
---

### Post by marie@idiomatic on 2017-04-21
I am trying to install Ubuntu 16.04 LTS on a brand new Lenovo Legion Y520-15IKBN I7-7700HQ 16GB DDR4 512GB M.2 PCIE SSD + 1TB HDD which has Windows 10 pre-installed. I boot from a dvd and get as far as the dialog "Preparing to install Ubuntu" but then get the message "You need at least 8.6 GB disk space to install Ubuntu. This computer has only 0.0 B." Apparently, the installer simply does not find the computer's internal disk space.

I would like to install Ubuntu on the SSD.

If possible, I would also like to keep the pre-installed Windows 10 (dual boot), but this is mainly as a safety precaution in case I cannot get Ubuntu to work properly. If I do get Ubuntu to work perfectly, I won't need Windows 10, so if the only solution involves removing Windows, that would be okay too, as long as I can then be sure that Ubuntu is actually going to work.

I have tried to look for a solution in this forum and elsewhere in the internet, but given my limited technical understanding, I am not sure what to try first or how to go about things. I found a similar question in another forum where one answerer says, "If the installer is not detecting any drives at all, it is because the installer doesn't have a driver for the RAID controller you've got in the system." I have no idea whether this could perhaps be my problem (I don't even know what a RAID controller is), but maybe someone in here can tell me how to check and what to do. It might also be about something completely different, of course.

Any help would be much appreciated! I should mention that my technical understanding is limited, so I would appreciate if answerers could explain everything in sufficient detail. I am not afraid of using the terminal if instructed to do so, but I don't always quite understand what I am doing! I have used Ubuntu for some years now, but it is my first time trying to install it myself.

---

### Post by oldfred on 2017-04-21
Are drives set for RAID, IDE or AHCI. Should be AHCI.
Some systems used various tools like Intel SRT to provide a partition for Windows hibernation. That usually looks like RAID to Linux.

Most brands are consistent with issues across multiple models. Maybe changing some with AMD vs. Intel or new generation of chips.
But Lenovo seems to have different issues for just about every model.

See if any of these apply, but they may not since yours is so new.
       Lenovo rename files
[URL="http://ubuntuforums.org/showthread.php?t=2302170"]http://ubuntuforums.org/showthread.php?t=2302170
[/URL]
 T540 works but UEFI settings critical or it may brick reset w/ Switching "OS Optimized Defaults
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)
Installing GNU/Linux on a 2014 Lenovo Thinkpad X1 Carbon UEFI/BIOS suspend to RAM issue
[http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon](http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon) 
      
 Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[http://ubuntuforums.org/showthread.php?t=1911972](http://ubuntuforums.org/showthread.php?t=1911972) 
    [URL="http://ubuntuforums.org/showthread.php?t=2302170"]
[/URL]

---

### Post by marie@idiomatic on 2017-04-22
> **oldfred said:**
> Are drives set for RAID, IDE or AHCI. Should be AHCI.

How do I check? I'm afraid I need everything explained in great detail.

As far as I can see, the other threads you refer to are about other issues, though I haven't looked closely at them all. Maybe for someone with a good technical understanding, it would be possible to to find something useful there, but I don't understand much of it, so I don't really know what to look for.

---

### Post by marie@idiomatic on 2017-04-22
According to answerer 2 in this thread:
[https://www.quora.com/What-is-the-reason-behind-not-being-able-to-see-any-disk-partitions-while-installing-Ubuntu-12-04-on-a-laptop-with-two-hard-disks-SATA-+-SSD-both-of-which-are-in-RAID0-configuration](https://www.quora.com/What-is-the-reason-behind-not-being-able-to-see-any-disk-partitions-while-installing-Ubuntu-12-04-on-a-laptop-with-two-hard-disks-SATA-+-SSD-both-of-which-are-in-RAID0-configuration)
if you disable the Intel RST in Windows, this will unjoin your 2 drives, meaning that you lose your hybrid drive. I am not sure exactly what that implies - will I only be able to access one of the drives, or is it just that they will be treated as two separate drives?

Answerer 1 says that the "change RAID to ACHI" is only a solution in a situation where you aren't trying to maintain the existing Windows installation. He continues, "If the installer is not detecting any drives at all, it is because the installer doesn't have a driver for the RAID controller you've got in the system.  Not knowing exactly which one you've got, I'm not able to suggest which driver (or possibly, newer version of Ubuntu) you'll need to get that fixed."

Could this mean that I might just have more luck with Ubuntu 17.04? Or might it perhaps be possible to somehow kind of add such a driver to Ubuntu 16.04?

From what these two answerers say, it would for several reasons be best if I could stick with RAID (which I assume is what I have, though I still don't know how to check).

---

### Post by oldfred on 2017-04-22
If Intel SRT, that looks like RAID, then you also have to remove meta data from drives.
But if true RAID and some systems are RAID 0 which uses two identical drives with half of data on one & half on other. And then you have to backup & restore all data to one drive. 
But either way you still must have good backups.

Post these from live installer's terminal:
sudo parted -l
sudo gdisk -l /dev/sda
sudo gdisk -l /dev/sdb

---

### Post by marie@idiomatic on 2017-04-22
Sorry about taking so long. Here are the results:

---

### Post by marie@idiomatic on 2017-04-22
All it seems to find is the dvd drive and the dvd, isn't it?

---

### Post by oldfred on 2017-04-22
It shows only sr0 or DVD drive.

Did you change to AHCI?
Does UEFI/BIOS show drive(s)?

---

### Post by marie@idiomatic on 2017-04-23
> **oldfred said:**
> Did you change to AHCI?

I wasn't sure how to, but now I managed, and I now get a very different result:
[ATTACH=CONFIG]274728[/ATTACH][ATTACH=CONFIG]274727[/ATTACH][ATTACH=CONFIG]274726[/ATTACH]

I also made a screenshot of the entire workspace to show that the drives now appear in the launcher to the left. On mouse-over, one says "Windows", the next one "LENOVO" and the last one "DATA".

[ATTACH=CONFIG]274725[/ATTACH]

> **oldfred said:**
> Does UEFI/BIOS show drive(s)?

This is what I found (before changing to AHCI):

[ATTACH=CONFIG]274729[/ATTACH]

---

### Post by oldfred on 2017-04-23
I might turn secure boot off, but you may not have to.

You now show two drives, sda as 1TB and a NVMe which is SSD at 512GB.
Not sure if grub will install correctly is 1TB is sda. It supposedly works with NVMe, but grub wants to install to an ESP - efi system partition on sda. If issues with grub installing add an ESP on sda.

Please post terminal output, just by copy & paste, not screen shots. If longer output use code tags which are easy to add with Forum's advanced Editor and # icon.

Be sure to use Windows tools to shrink the Windows NTFS partition and reboot immediately so it can run chkdsk.
Make sure Windows fast start up is off and in UEFI its fast boot is off. Once system is well configured, you can possibly turn UEFI fast boot on. 
Issue with UEFI fast boot is that it is so fast you do not have time to press a key to get into UEFI or choose boot option from UEFI boot menu. It assumes you only get into UEFI from Windows, but when Windows breaks you cannot get into UEFI. Some have reset, some require cold boot (not warm reboot) or other work arounds. 

You do need to install in UEFI boot mode. If Secure boot off, you may get two boot options in UEFI boot menu.
For more details see link below in my signature.

---

### Post by marie@idiomatic on 2017-05-02
I managed to install Ubuntu after changing Intel RST Premium to AHCI.

However, I decided to forget about keeping Windows, partly in order to save time and because I didn't understand all the instructions, partly because I don't actually need Windows as long as Ubuntu runs well, which it finally does now.

Also, before installing Ubuntu, I noticed that Windows would no longer boot after I had changed Intel RST Premium to AHCI. When I changed back to Intel RST Premium, I could start Windows again. So if I had decided to go for dual boot, I might have had to enter UEFI every time I wanted to switch OS in order to change back and forth between Intel RST Premium and AHCI. 
Or maybe when you said, "backup & restore all data to one drive", you meant somehow forcing Windows to put itself on one drive only so that it would no longer need Intel RST? This was one part of the instructions that I did not understand, and I am only now realizing that this was perhaps what you meant.
In any case, I will leave this thread open for a few more days in case you want to add something that might be useful for others who want dual boot. But otherwise, thank you very much for your help, oldfred!

---

### Post by oldfred on 2017-05-02
If you have not done backups, you need to do them.
My Dell wanted me to do a Dell backup, a Windows backup & then I did a full image backup with Macrium.
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp) 


I do not have Intel SRT.
But have seen some other threads where they re-enabled it and dual booted. I think the issue is/was the installation, particularly of grub boot loader. Not sure if then turned on, that major updates have issues and to get them to install, you have to turn it off again or not.

Intel SRT seems to be the same across various vendors. But these now are older systems, so maybe not exactly the same.
 Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

---

### Post by ajinkyav on 2017-06-04
I faced similar issues with my Lenovo Leigon Y520 (256GB SSD + 2TB HDD). 256GB SSD had windows installed on it. I can confirm that I am able to dual boot Ubuntu 16.04.2 with Windows 10 after following below guide.
[http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html](http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html)

Please check the comment by Zack (pasted below) which provides a link showing how to change Intel RST Premium to AHCI and successfully boot in windows:

[FONT=arial][SIZE=4]"Same thing happend to me. The first answer on this site helped me get ubuntu to recognize my local SSD. http://askubuntu.com/questions/764353/ubuntu-16-04-lts-unrecognized-hard-drive-not-enough-disk-space-to-install"[/SIZE][/FONT]

---


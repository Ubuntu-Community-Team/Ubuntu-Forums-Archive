---
title: "I have a multi-boot system, but cannot reach one of the Xubuntu installs"
date: 2023-02-05
forum: Installation &amp; Upgrades
---

### Post by kogorman-pacbell on 2023-02-05
I have a number of installs, including Mint, Xubuntu and Fedora.  I've had a couple of recent disasters, aggravated by trying to fix things while battling medical issues -- and I'd guess not doing it well but I don't know that.

This is just one of the problems: an Xubuntu 20.04.5 partition (sda10) that is listed in the GRUB menu, but that I cannot reach because GRUB actually sends me to sda9, which is also Xubuntu 20.04.5.  I've tracked down a probable reason: when I tap "E" in GRUB, I see that the UUID for the two installs is listed as the same one, which is the one on /dev/sda9.

I have verified that the actual UUID on sda10 is different (I changed it with tune2fs).
In SDA9 I have done a grub-update, and install-grub to both SDA and SDB (the two that my BIOS can use).  This does not change the UUIDs that GRUB shows during boot.

What else should I do to get GRUB working properly, or test to make sure I've diagnosed it right, and that I've fixed it right

---

### Post by oldfred on 2023-02-05
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

You probably will not want any auto fix from Boot-Repair. It defaults to first install and installing to first drive.
Be sure to boot in same boot mode as installs, or BIOS if BIOS installs or UEFI if UEFI installs as repairs need to be in same mode as install is.

Advanced mode allows you to choose an install & choose a drive to install boot loader into.

---

### Post by yancek on 2023-02-06
I'd suggest following the suggestions in post 2 by oldfred, particularly with regard to the boot repair script.  It's important to know whether you are using UEFI or Legacy/CSM boot option.  One possibility, based on what you reported is that you are actually booting from another OS install and not sda9 and you need to repair and update grub from that OS.  If you installed Xubuntu on sda10 after sda9, it may be in control of booting.  Boot repair should show all this info.

---

### Post by kogorman-pacbell on 2023-02-06
@oldfred thanks for the reply.  Sorry at my age and condition it takes a while to do stuff, but I was able to follow your instructions.  From partition sda12, I was able to get this pastebin report: [https://paste.ubuntu.com/p/KxWjHD93mr/](https://paste.ubuntu.com/p/KxWjHD93mr/)

As you'll see there's a bunch of stuff, partly because I have more disk space than I need and I'm lazy.  Part of it is new stuff I put in trying to figure out this and some other problems.  For the moment I'd be happy to get GRUB doing something sane with sda9 and sda10.

I would add that I can control which disk the BIOS boots from, but I get the same results whether I boot to SDA or SDB.  I do not boot from SDF and until I saw the report I didn't remember that SDF was ever bootable.

---

### Post by oldfred on 2023-02-06
I thought I had a lot of old installs. But I have overwritten the real old ones with new obsolete versions.
I control grub by turning off os-prober (makes os-prober work a lot faster) and only copy into 40_custom the boot stanza for current installs.

It looks like you have a /boot partition, sda6. But searching report on that UUID says it is in fstab for both sda9 & sda10. 
That is then part of issue, as they will conflict, each may update or delete files needed by the other. 
Better just not to have /boot as a partition. Only may be required with LVM or other server configurations. And then separate one for every install.

You also show  UEFI boot as ESP is mounted for both sda9 & sda10. But sda is MBR(msdos). MBR partitioning is required for Windows in BIOS boot mode, and Windows requires gpt partiitoning for UEFI boot. Ubuntu will boot in either mode from either partitioning, but really should only use gpt for UEFI and can use gpt for BIOS, with a bios_grub partition. So only place for MBR partitioning is for Windows boot in BIOS mode. And Microsoft has required UEFI/gpt boot install by vendors since 2012. Even Windows 7 can be installed in UEFI boot mode, just not with Secure Boot on.

You only get one Ubuntu entry in UEFI for ubuntu, but then grub can boot all other installs.
The grub installs in MBR, is not used with UEFI boot. 

Back up grub.cfg in your installs, so you have copies of boot stanza, if not sure how to create one yourself.

May be best to rerun report with UEFI boot mode. It will also then show UEFI boot entries.
Turn on UEFI boot. You may be able to boot one of the installs.

I might edit fstab in sda9 & sda10 to remove (comment out first as test). Make sure Advanced mode of Boot-Repair has not mounted /boot partition.
Then do total reinstall of grub in UEFI boot mode and check to include kernel, so files then installed to /boot folder in install, not /boot partition.
Choose one you want as default second to fix, so its grub is the one in UEFI and ESP as default boot.

40_custom example
[https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive](https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive)
How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Mega thead, before above help site. Read first page, and then jump to end & work backwards for latest examples.
[https://ubuntuforums.org/showthread.php?t=2076205](https://ubuntuforums.org/showthread.php?t=2076205)
[https://ubuntuforums.org/showthread.php?t=2076205&page=54&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&page=54&p=13787835#post13787835)

---

### Post by santiargo on 2023-02-07
> **oldfred said:**
> I thought I had a lot of old installs. But I have overwritten the real old ones with new obsolete versions.
I control grub by turning off os-prober (makes os-prober work a lot faster) and only copy into 40_custom the boot stanza for current installs.

It looks like you have a /boot partition, sda6. But searching report on that UUID says it is in fstab for both sda9 & sda10. 
That is then part of issue, as they will conflict, each may update or delete files needed by the other. 
Better just not to have /boot as a partition. Only may be required with LVM or other server configurations. And then separate one for every install.

You also show  UEFI boot as ESP is mounted for both sda9 & sda10. But sda is MBR(msdos). MBR partitioning is required for Windows in BIOS boot mode, and Windows requires gpt partiitoning for UEFI boot. Ubuntu will boot in either mode from either partitioning, but really should only use gpt for UEFI and can use gpt for BIOS, with a bios_grub partition. So only place for MBR partitioning is for Windows boot in BIOS mode. And Microsoft has required UEFI/gpt boot install by vendors since 2012. Even Windows 7 can be installed in UEFI boot mode, just not with Secure Boot on.

You only get one Ubuntu entry in UEFI for ubuntu, but then grub can boot all other installs.
The grub installs in MBR, is not used with UEFI boot. 

Back up grub.cfg in your installs, so you have copies of boot stanza, if not sure how to create one yourself.

May be best to rerun report with UEFI boot mode. It will also then show UEFI boot entries.
Turn on UEFI boot. You may be able to boot one of the installs.

I might edit fstab in sda9 & sda10 to remove (comment out first as test). Make sure Advanced mode of Boot-Repair has not mounted /boot partition.
Then do total reinstall of grub in UEFI boot mode and check to include kernel, so files then installed to /boot folder in install, not /boot partition.
Choose one you want as default second to fix, so its grub is the one in UEFI and ESP as default boot.

40_custom example
[https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive](https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive)
How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Mega thead, before above help site. Read first page, and then jump to end & work [backwards]("https://kohiclicks.com/") for latest examples.
[https://ubuntuforums.org/showthread.php?t=2076205](https://ubuntuforums.org/showthread.php?t=2076205)
[https://ubuntuforums.org/showthread.php?t=2076205&page=54&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&page=54&p=13787835#post13787835)

thank you so mcuh share detial.

---

### Post by kogorman-pacbell on 2023-02-07
Thank you SO much.  But I have questions before I even try to follow instructions.  The one thing I will probably do immediately is to separate the /boot partitions for /sda9 and sda10, as I can easily make backups to restore any damage I do.

> **oldfred said:**
> I thought I had a lot of old installs. But I have overwritten the real old ones with new obsolete versions.
I control grub by turning off os-prober (makes os-prober work a lot faster) and only copy into 40_custom the boot stanza for current installs.
How to turn off os-prober?  Where would I find 40_custom (I vaguely remember it from a decade or two ago but have forgotten when or why)?  What is a boot stanza?

> **oldfred said:**
> It looks like you have a /boot partition, sda6. But searching report on that UUID says it is in fstab for both sda9 & sda10. 
That is then part of issue, as they will conflict, each may update or delete files needed by the other. 
Better just not to have /boot as a partition. Only may be required with LVM or other server configurations. And then separate one for every install.
I had been wondering about those /boot partitions, and whether it would be best to have one per install.  I had been doing that because the OS Installer created them -- at least once in the past.  I had presumed that GRUB knows where these things are, and was worried that my occasional reworking of partition positions would cause trouble, so planned to keep /boot small and close to the start of its drive.  I'm not sure if my configuration with multiple OS partitions qualifies as a server.  But I agree that a new plan seems to be called for -- I am just not sure what would be best.

> **oldfred said:**
> You also show  UEFI boot as ESP is mounted for both sda9 & sda10. But sda is MBR(msdos). MBR partitioning is required for Windows in BIOS boot mode, and Windows requires gpt partiitoning for UEFI boot. Ubuntu will boot in either mode from either partitioning, but really should only use gpt for UEFI and can use gpt for BIOS, with a bios_grub partition. So only place for MBR partitioning is for Windows boot in BIOS mode. And Microsoft has required UEFI/gpt boot install by vendors since 2012. Even Windows 7 can be installed in UEFI boot mode, just not with Secure Boot on.
I am confused.  I am not sure how to turn on UEFI boot mode.  I do not understand the difference or connection of UEFI and Secure Boot.  And most important, I'm not sure if you are recommending any particular change.

> **oldfred said:**
> You only get one Ubuntu entry in UEFI for ubuntu, but then grub can boot all other installs.
The grub installs in MBR, is not used with UEFI boot. 
I am not sure if you are recommending a change.

> **oldfred said:**
> Back up grub.cfg in your installs, so you have copies of boot stanza, if not sure how to create one yourself.
Will do.

> **oldfred said:**
> May be best to rerun report with UEFI boot mode. It will also then show UEFI boot entries.
Turn on UEFI boot. You may be able to boot one of the installs.
I will see if this is a thing I can do in my BIOS.  If that is not the way, please explain how to do that.

> **oldfred said:**
> I might edit fstab in sda9 & sda10 to remove (comment out first as test). Make sure Advanced mode of Boot-Repair has not mounted /boot partition.
Then do total reinstall of grub in UEFI boot mode and check to include kernel, so files then installed to /boot folder in install, not /boot partition.
Choose one you want as default second to fix, so its grub is the one in UEFI and ESP as default boot.
What is it I should remove / comment out?  My guess is that you want me to remove the /boot entry from fstabs, and re-run update-grub and maybe grub-install.  Is that right?
I'm not clear how to do the UEFI part of this -- I would probably need a more step-by-step instruction, but I'll investigate the 40_custom_example you posted below to see if that clears things up for me.

> **oldfred said:**
> 40_custom example
[https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive](https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive)
How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Mega thead, before above help site. Read first page, and then jump to end & work backwards for latest examples.
[https://ubuntuforums.org/showthread.php?t=2076205](https://ubuntuforums.org/showthread.php?t=2076205)
[https://ubuntuforums.org/showthread.php?t=2076205&page=54&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&page=54&p=13787835#post13787835)
I will be reading this.

I'm sorry about all the questions, but this is a lot to take in all at once.

---

### Post by oldfred on 2023-02-07
Since Microsoft required UEFI/gpt starting in 2012 all hardware since then has been UEFI. Vendors often still called it BIOS, but it really is UEFI.
And then some large customers of Microsoft had older BIOS only systems and still wanted the newer Windows, so they allowed BIOS boot. Microsoft back then did not want any BIOS. Now new systems starting in 2020 are often UEFI only, no BIOS mode at all.
How you boot install media is then how it installs or repairs. In UEFI/BIOS boot menu, you should get 2 boot options for Ubuntu live installer. One is clearly UEFI as UEFI : XXXX where XXXX is name or label of flash drive. Mine often says PMAP, not sure if that is flash drive label as it is an OEM/Store flash drive. You also then have a BIOS install as XXXX with same label. If full USB support on in UEFI settings, then both options are normally shown. A few installers to create flash drive may make UEFI only or BIOS only flash drives. You always want UEFI or both.

And then in UEFI settings (not UEFI boot menu) you have a setting for UEFI or BIOS/CSM/Legacy boot. You may have UEFI only or UEFI or BIOS or CSM. UEFI then has two settings, one Secure boot on or off. This sets the default boot mode for installed systems. Most UEFI try first choice and may try other choices but post various types of errors like boot not found, but enter then tries other boot mode.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

You want to first change UEFI boot mode to UEFI. And see if one of your installs then boots ok.
You want to go into UEFI boot menu and see if your flash drive is UEFI (it should be) and if you have UEFI : XXXX boot entry.

Links I posted show boot stanza and 40_custom.
New versions of Ubuntu now want to turn off os-prober. Some security issue on having it scan all partitions. You probably have to do this in every install. And with multiple installs, updates to grub will change boot order to make that install the new default. You just need to reboot into preferred install and reinstall grub.
sudoedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
I also like to change distributor, so I have different descriptions for each install. Comment out default & add my own. Labels have to be added to partition for using label to boot.
[FONT=monospace][COLOR=#000000]#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
[FONT=monospace][COLOR=#000000]GRUB_DISTRIBUTOR=jammy[/COLOR]

Two examples of my 40_custom boot stanzas
sudoedit /etc/grub.d/40_custom
[/FONT][/COLOR][/FONT]```
[FONT=monospace][COLOR=#000000]menuentry "Ubuntu 22.04 jammy /dev/nvme0n1p4" { [/COLOR]
    search --set=root --label jammy 
    configfile /boot/grub/grub.cfg 
} 


menuentry "Ubuntu 22.04 jammy /dev/sda10)" { 
    search --set=root --label jammy_b 
    #search.label jammy_b root -hint hd1,gpt10 
    configfile /boot/grub/grub.cfg 
}

[/FONT]
```[FONT=monospace][COLOR=#000000][FONT=monospace]
[/FONT]
[/COLOR]
[/FONT]

---

### Post by kogorman-pacbell on 2023-02-07
@oldfred I tried something simple, and did not get what I wanted.

This was the plan:
  - Change fstab in sda10 by commenting out the /boot entry
  - I'll back up sda9 and sda10 again, as well as the /boot
  - Boot into sda9 and do an update-grub then grub-install /dev/sda
  - See if I can no boot into sda10

The answer was no: sda10 appeared in the output of update-grub, but not in the grub menu on bootup.  I'm guessing that was because sda10 had an empty /boot partition, and while update-grub could see that it was Linux, it could not find a kernel and other startup files.

Ideas?

---

### Post by oldfred on 2023-02-07
If commenting out /boot you either have to reinstall kernel & grub or copy everything in /boot partition to /boot folder. 

So sda9 did boot ok in UEFI mode?

---

### Post by kogorman-pacbell on 2023-02-10
> **oldfred said:**
> If commenting out /boot you either have to reinstall kernel & grub or copy everything in /boot partition to /boot folder. 

So sda9 did boot ok in UEFI mode?

sda9 booted OK, but not in UEFI mode (using either sda or sdb boot sectors.
And after copying all of /boot partition to sda10's /boot directory, and redoing update-grub and grub-install, I can boot to sda10.

That solves this issue.  Thank you very much, oldfred.

---

### Post by kogorman-pacbell on 2023-02-10
> **oldfred said:**
> If commenting out /boot you either have to reinstall kernel & grub or copy everything in /boot partition to /boot folder. 

So sda9 did boot ok in UEFI mode?

I marked this as SOLVED.

After copying all of the /boot partition to SDA10 /boot directory,  and re-doing grub-update and install-grub, SDA10 boots.  From both SDA and SDB it boots in Legacy mode, judging from the lack of 'efi' in /sys/firmware.

The same is true of SDA9.

---

### Post by kogorman-pacbell on 2023-02-10
> **oldfred said:**
> If commenting out /boot you either have to reinstall kernel & grub or copy everything in /boot partition to /boot folder. 

So sda9 did boot ok in UEFI mode?

I marked this thread SOLVED before answering this, so I'm adding it now. (Oddly this is my third or fourth try).

I copied the /boot partition ot sda10's /boot folder, and all seemed well.

Both sda9 and sda10 boot just fine, but not in UEFI mode, judging by the lack of 'efi' in /sys/firmware.

---

### Post by oldfred on 2023-02-10
Since fstab had the mount of the ESP, I thought your install was UEFI.
But if it works that is great. 

Note that sda as MBR(msdos) allows grub to install without issue as there is a bit of room between MBR & first partition for more grub code (core.img)
But all your other drives are gpt, most commonly used with UEFI, but you can use grub in BIOS mode. But with gpt there is no space after gpt's protective MBR & start of gpt partition table. So for BIOS boot with gpt drives you must have a tiny 1 or 2MB unformatted partition with bios_grub flag.
then you can have different grub installs in each drive's MBR. 

But I still think since system is UEFI, probably better to convert to UEFI boot.
And eventually convert sda to gpt. But that will erase drive, so good backups required.
I converted all drives to gpt starting in 2010, but only when totally redoing drive or replacing drive.

Grub will only boot other installs in same boot mode as once you start booting in one mode UEFI or BIOS you cannot switch to other boot mode.

---


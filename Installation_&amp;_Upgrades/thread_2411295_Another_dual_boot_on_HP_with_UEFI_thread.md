---
title: "Another dual boot on HP with UEFI thread"
date: 2019-01-28
forum: Installation &amp; Upgrades
---

### Post by jsundqui on 2019-01-28
I have lots of experience installing Linux on dual boot machines - my first time was in 1996, installing Slackware 3.0 (from floppies!) along side a Win95 install!

I have also installed on a few machines with UEFI, but not dual boot.

This is my first time for dual boot with UEFI (dual with Windows 10) and it looks like from much searching on this forum that it was bad choice to get an HP.

I install OK, but the problem is only booting into Windows.

As a digression, for the install, I followed all the advice I could fund, including disabling secure boot, fast start up, etc. etc.  One piece of advice I did not find anywhere was to create a separate partition for /etc/efi.  The first time I tried the install it failed because it couldn't write the efi files.  So I had to create that partition separately (I did manual partitioning since I didn't want to installer to nuke the Win10 install, and the only default options with Ubuntu 18.04 was to pretty much nuke the Win10 install).

end digression.

Rebooting gave me no option to select Ubuntu.  I tried all sorts of ESC F9, F10, etc. during boot, but the only boot options I ever saw were which device (HD or USB stick) to boot from.  I tried running "bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi" from an admin account windows command line, but no luck.

More searching showed me this thread: [https://ubuntuforums.org/showthread.php?t=2392797](https://ubuntuforums.org/showthread.php?t=2392797) which said that HP just hard codes the windows-only boot into the BIOS, but provides a work around.  OldFred gives a great list of links in [reply #2]("https://ubuntuforums.org/showthread.php?t=2392797&p=13770426#post13770426") to that thread.

I also ran boot-repair and got this print out: [http://paste.ubuntu.com/p/YZGxXJf7gT/](http://paste.ubuntu.com/p/YZGxXJf7gT/)

I am posting for two reasons.

The first is I am trying to decide which option to run first.  boot-repair seems like a well-respected utility so it seems I should just click the repair button.  So I was thinking of doing hte file rewrites first.  However, before I do this, I have a question about these EFi files.  As I mentioned, I created a separate FAT32 partition mounted at /etc/efi or wherever it is supposed to be (I am not at that machine right now).  But I can't imagine why windows booting would look to that partition when booting.  So which files are which?  In OldFred's list of links to HP dual boot problems, one thread puts it this way:  "replaced the EFI/Microsoft/boot/bootmgfw.efi with the grub64.efi".  Can someone point more specifically to where these files are to make sure I am copying the right ones?

Second reason: I suppose I could just have boot-repair do its thing and cross my fingers, but I would at least like to know what it is doing.  From that pastebin text (note it was run from a live-USB session running off the USB install media, sda is the machine, sdb is the USB stick).  boot-repair's "suggested repair" is:

```
The default repair of the Boot-Repair utility would purge (in order to unsign) and reinstall the grub2 of sda7 into the MBR of sda.
Grub-efi would not be selected by default because: no-win-efi
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot
```

None of this sounds like moving and renaming efi files.  So not sure why this would work instead.

Any suggestions?  I don't mind mounting partitions and renaming files.

---

### Post by oldfred on 2019-01-28
Forget UEFI.
Your Windows install is BIOS on MBR partitioned drive. So better to just install Ubuntu in BIOS boot mode.
(Unless you really want to re-install Windows in UEFI boot mode, after major backups.)

But if UEFI hardware, vendors are required to install Windows in UEFI boot mode. So you must have installed or reinstalled Windows?
Windows product key is now in UEFI, so you have to have a separate license to install in BIOS boot mode.

Boot-Repair's auto fix usually works, but there are configurations where better to use its advanced mode and select install & drive to install boot loader into, especially those with multiple drives.
How you boot install media, UEFI or BIOS for both Windows and Ubuntu is then how it installs. And then system needs to be in that boot mode, which is a separate setting.

The renaming of "Windows Boot Manager" UEFI boot entry was an old workaround as HP and others would only boot by description and only valid description was "Windows Boot Manager". But Windows updates overwrote that entry, so not best.
Then we found that almost all UEFI systems will boot the fallback or hard drive entry at /EFI/Boot/bootx64.efi. This is how UEFI boots external drives & it was updated to use same type of entry as boot. Boot-Repair now auto copies shimx64.efi to be a valid fallback file, but UEFI may not have entry to use it.

It looks like Boot-Repair is installing the BIOS version of grub or grub-pc. Since BIOS installs, best to always boot in BIOS mode, so Boot-Repair will do BIOS fixes. It used to only do fixes for mode booted UEFI or BIOS, but seems to see install and know which version of grub to use.

You will not need and generally do not want an ESP on MBR partitioned drives. It can be used, but UEFI really wants gpt. And Windows absolutely requires gpt partitioning for UEFI boot. Ubuntu is more flexible, but gpt still preferred. And converting Windows to UEFI, would require repartitioning drive, erasing it.

You do not have to have swap partition either. New versions of Ubuntu now use swap file. But if swap partition found, it will use it.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by jsundqui on 2019-01-28
Thanks OldFred.

I had just assumed everything was UEFI.

This is a [refurbished machine]("https://www.newegg.com/Product/Product.aspx?Item=N82E16834270252") I bought from newegg.com.  It's actually the third one of these small form factor former-office-machine boxes I've gotten over the last couple of years and I have really liked them.  One was no-OS box that is currently serving as my MythTV machine (mythbuntu installed without a hitch) while the other one came with Win10 which my wife uses single-boot.

I needed to replace my main linux box and the best featured one I found for the price came with Win10, and I figured I would keep that install just in case I needed to run something that needed Win10. Why throw away a fully-activated Win10 license, especially since the machine came with a 2 TB hard drive - plenty of room for two OS's?

So the Win10 install was put on there by the refurb company.  They must have had whatever license was needed to install Wi10 in BIOS mode.  I did notice it was MBR rather than GPT which I thought was strange.  But that explains it.

So you are saying that if I just run the fix that boot-repair recommends I should be good to go?   I don't recall selecting "UEFI" during install or anything so I don't think I need to do the installation process again, or do I?  I would note that my first install failed because it couldn't write EFI files because I didn't create an EFI partition.

So run boot-repair fixes?  Or do I have to reinstall?

About the swap partition - good to note.  Just created that out of "habit".  I've been installing Linux since 1996, but that doesn't mean I do it every day ;-)  Good to know that that isn't needed anymore.

---

### Post by oldfred on 2019-01-28
Both Ubuntu & Windows installers are both UEFI and BIOS.
The only place you select which mode your install, is when in UEFI you select a boot mode for the installer flash drive or DVD.
UEFI normally presents UEFI:flash or flash where flash is name or label of flash drive.  And one just with name is BIOS boot.

You do not need to reinstall Ubuntu, but just total reinstall of grub. Grub has two versions grub-pc for BIOS and grub-efi-amd64 for UEFI boot and that and a few minor settings that grub changes will convert your install to BIOS boot.
So Boot-Repair fix should install grub-pc and make Ubuntu BIOS boot.

One of the disadvantages of BIOS, now is that Windows 10 wants to turn fast start up or hibernation on. Then the Linux NTFS driver will not see it and grub will not boot it. And with BIOS, you have to temporarily reinstall a Windows boot loader to boot Windows, then restore grub to dual boot. Or with any versions of Windows needs chkdsk or is hibernated, then grub will not boot it.
Best to keep both a Windows repair disk, or installer with repair console and Ubuntu live installer flash drive handy, so when Windows has issues, you can easily repair it.

With UEFI, you just have to use UEFI to choose to boot Windows. The ESP has separate folders for every installed system (somewhat like multiple MBRs) as then you can choose what to boot without repair disks (if system will boot).

Just noticed you have nVidia.
And issues, often you have to use nomodeset boot parameter to boot live installer & first boot or until you install the nVidia driver from Ubuntu  repository.

---

### Post by jsundqui on 2019-01-28
> **oldfred said:**
> Both Ubuntu & Windows installers are both UEFI and BIOS.

You do not need to reinstall Ubuntu, but just total reinstall of grub. Grub has two versions grub-pc for BIOS and grub-efi-amd64 for UEFI boot and that and a few minor settings that grub changes will convert your install to BIOS boot.
So Boot-Repair fix should install grub-pc and make Ubuntu BIOS boot.

OK, I will give the boot-repair utility a go with its recommendations tonight and then report back

> **oldfred said:**
> One of the disadvantages of BIOS, now is that Windows 10 wants to turn fast start up or hibernation on. Then the Linux NTFS driver will not see it and grub will not boot it. And with BIOS, you have to temporarily reinstall a Windows boot loader to boot Windows, then restore grub to dual boot. Or with any versions of Windows needs chkdsk or is hibernated, then grub will not boot it.

It seems to me that boot-repair would do this, no?  The last line of the recommendations is

```
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot

```

> **oldfred said:**
> Best to keep both a Windows repair disk, or installer with repair console and Ubuntu live installer flash drive handy, so when Windows has issues, you can easily repair it.

With UEFI, you just have to use UEFI to choose to boot Windows. The ESP has separate folders for every installed system (somewhat like multiple MBRs) as then you can choose what to boot without repair disks (if system will boot).

Just noticed you have nVidia.
And issues, often you have to use nomodeset boot parameter to boot live installer & first boot or until you install the nVidia driver from Ubuntu  repository.

I didn't make a windows recovery disk, unfortunately.  I am loath to reboot back to windows, though, because rather than nVidia, I am having troubles with the USB WiFi adaptor that came with this machine.  It works, except when it doesn't.  sometimes access just comes to a halt.  It was a miracle I was able to get boot-repair installed, as the apt-updates ground to halt.

I didn't have any issues with the nVidia driver with the live installer, and I did check the option to install proprietary drivers during the install so when/if I get it to boot on its own I should be all set.

---

### Post by jsundqui on 2019-02-02
I ended up having to travel for work this week, so didn't get to run repair-boot until today, the weekend.

The system now boots into Kubuntu and everything works.  

However, I now have no option to boot into windows.  Pressing F9 just gives me options as to what media to boot from, not what OS to boot.

The report from repair-boot after the repair is [http://paste.ubuntu.com/p/GqK8RYtmtZ/](http://paste.ubuntu.com/p/GqK8RYtmtZ/)

---

### Post by oldfred on 2019-02-02
Grub only boots working Windows.

Os-prober never saw Windows.
And with BIOS installs of Windows 10, you have a bit of a hassle since Window updates will turn on fast start up which sets hibernations flag. And then grub will not boot it on a reboot. With UEFI you would only have to directly boot Windows from UEFI, but with BIOS and only one MBR, you have to temporarily reinstall a Windows or Windows type boot loader to MBR. Repair  Windows or turn off fast start up. Then restore grub to dual boot. You may need:
sudo update-grub.

Best to always have Windows repair flash drive and Boot-Repair handy as you will sometimes need them.
Not sure if Boot-Repair will let you in advanced options install a Windows type boot loader or not if it does not see the NTFS partition. You may need your Windows repair flash drive or installer with a repair console and run fixMBR command.

---

### Post by jsundqui on 2019-02-02
Thanks again for your assistance in my problems.

I was thinking that boot-repair saw windows since part of the suggested fix was "Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot"

I did make a windows repair flash drive, but I am thinking that running that will make it boot Windows, but windows only.

I can handle turning off fast start for the rare times I boot into windows and it gets updated.  So that's not a problem.  

I am wondering if having that EFI partition confused boot-repair.  I don't need that, do I?  I wonder if I unformatted that partition and ran boot-repair again if that would do anything.

If I understand correctly, you are suggesting I

- boot with my windows repair flash drive
- repair windows from that boot (I am not sure what it will present me when I boot with that, but I can google it)
- then restore grub

But I am confused how I would do the third step if booting after the windows repair only lets me boot into windows.

it seems like I should be able to manually edit /boot/grub/grub.cfg  But actually, looking at that I probably would be chasing a dead end since it lists three boot options (Ubuntu, Ubuntu, with Linux 4.15.0-29-generic, and Ubuntu, with Linux 4.15.0-29-generic (recovery mode)) but I never see these options when I boot.

---

### Post by ubfan1 on 2019-02-02
grub puts a number of addiitonal options under a sub-menu under the "advanced..." menu option.  After the Windows repair, you would boot from an Ubuntu install media to fix grub.

---

### Post by jsundqui on 2019-02-07
I just to run boot-repair again and now I see the grub menu when I boot, with options for both Ubuntu and Windows.

Thanks for everyone's help.

---


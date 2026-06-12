---
title: "How do I keep Win10 install and Ubuntu Separate? (No Dual-Boot!)"
date: 2018-05-25
forum: Installation &amp; Upgrades
---

### Post by cubdukat1968 on 2018-05-25
I want to install Ubuntu on my system, but I don't want it to interfere with my Windows 10 install, because I have had really bad luck with dual-boot installs. The last one I attempted turned one of my NTFS volumes into an LVM, and I'm still trying to fix that (nothing's been written to it, so all the previous data and folders are all still there).

What I want to end up with is a system where I have to go into BIOS to switch between drives to boot Ubuntu, I need the Ubuntu drive to be completely self-contained. 

Would I install the boot loader to the drive the system will be going on?

---

### Post by oldfred on 2018-05-25
If you choose full drive encryption which uses LVM or LVM, those erase entire hard drive. 
LVM is an advanced volume management system, often used with servers, but is required for full drive encryption. 
But LVM is not really recommended for newer users.

Always better to use Something Else install option, rather than any of the auto install options. But then you need to understand partitions, both all the ones Windows has and the one (or more) that Ubuntu must have.

Is system UEFI or BIOS?

Best way to keep them separate is to disconnect Windows drive and install to a separate drive. If laptop with one drive, you can use external drive, but USB ports not as fast as internal SATA ports. And even newer NVMe drives are still faster than SATA. But USB3 can be functional if you really want separation.

But installing to an external drive in UEFI mode requires a bit more work. You must partition in advance to have an ESP - efi system partition on external drive.

What brand/model system? What video card/chip?
UEFI or BIOS install?
Multiple drives or only one drive?

---

### Post by cubdukat1968 on 2018-05-25
Unfortunately, I had no say in the LVM matter. Apparently you have to tell Fedora's installer NOT to use LVM. Fortunately, no other data got written to it, and I've actually been able to see the previous NTFS info. I think it would be a simple matter of releasing it from the volume group, right?

The main drive in my system is a Samsung 960 EVO 1TB. I was originally going to attempt a dual-boot with it, but the Ubuntu installer can't even see it. That's why I decided to do a self-contained install: because GRUB can't see the drive and I don't have to worry about it borking the Win10 install. Ever since UEFI came around, making dual-boot has been a nightmare for me. The drive the new system is going on is a 850 250GB, which previously held the Fedora install which borked that NTFS drive.

My setup is a self-built one:

ASUS Z370-A Prime w/ latest BIOS
Core i7-8700K
32GB DDR4-2400
Samsung 960 EVO (Boot), Toshiba 4TB x2 (Data and video [LVM]), Seagate 1TB (Misc., to be replaced w/Samsung 850 EVO for Ubuntu Install)

---

### Post by QIII on 2018-05-25
Hello!

If you are under some misapprehension that Fedora is anathema here, please disabuse yourself of that and use the name properly.

Thanks.

---

### Post by oldfred on 2018-05-25
The main reason a drive is not seen is Windows fast start up or hibernation.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
The Linux NTFS driver will not mount NTFS partitions that are hibernated. And Windows default is hibernation. It even turns it back on with updates, so if you cannot see NTFS from Linux check that first.

There are other reasons a drive may not be seen. 
If you use Windows to convert a gpt drive to MBR, it does it incorrectly leaving drive as MBR from Windows, but backup gpt partition table is still there and Linux tools do not know if MBR or gpt. 
Some systems have RAID set on for drives, even if just one drive. You need to have drives set to AHCI in UEFI settings. But add Windows AHCI driver before converting. You can change back and Windows will boot, but then Linux will not.

Have you updated UEFI to latest version?

I have an older Z97, but UEFI settings probably are similar. But my drive is standard SATA.
[https://ubuntuforums.org/showthread.php?t=2258575&page=2](https://ubuntuforums.org/showthread.php?t=2258575&page=2)

---

### Post by cubdukat1968 on 2018-05-25
The 960 EVO's not being seen by the installer because it seems that Ubuntu doesn't recognize NVMe drives like the EVO without you having to jump through a few hoops first. This is a known issue not only with Ubuntu, but most other distros too, I suspect. From what I gather, you need to switch over to the "AHCI" option instead of "Intel RST w/Optane" in order to get it to see it, but I'm just going to leave it alone because I don't need or want a dual-boot system. Until they invent something more Linux-friendly than UEFI, no more dual-boot systems for me. 

I disabled both hibernation and Fast Boot the minute I first turned the system on.

---

### Post by cubdukat1968 on 2018-05-25
Understood. But yeah, Fedora messed up that drive, and hopefully once Ubuntu's up and running, I may be able to correct the problem there, but that's for another post...

I probably should have stuck with Ubuntu in the first place. It was the distro which made me want to get serious about Linux, and I always seem to come back to it anyway...

---

### Post by QIII on 2018-05-25
> **cubdukat1968 said:**
> ... it seems that Ubuntu doesn't recognize NVMe drives like the EVO without you having to jump through a few hoops first ...

I'm not sure what hoops those are, unless they are related to Windows fast start/hibernation.

I have my primary desktop machine installed in UEFI mode with three NVMe Evo 960s (one as the OS drive, two for storage) without any issues at all.  UEFI works fine, so long as you have a small EFI partition on the drive -- which is common to both Linux and Windows.

---

### Post by monkeybrain20122 on 2018-05-25
I have dual booted Ubuntu with Fedora for a few years, always found its installer somewhat confusing, so I paid extra attentions to check every option to make sure that I didn't accidentally mess anything up. Yeah it makes no sense to default to LLVM but you can easily choose ext4 instead (but then Fedora doesn't aim for beginners)

---

### Post by hrsetrdr on 2018-05-25
Whether Ubuntu or Fedora I always do a manual partitioning just so I'll get what I prefer.  ;)   

Regarding the thread topic- Romtec Trios used to have a hard drive selector.  But that was the early 2000s. I guess a person could install W10 then Ubuntu each on seperate drives, then use F-11(or F-12) to select which drive to boot to.

---


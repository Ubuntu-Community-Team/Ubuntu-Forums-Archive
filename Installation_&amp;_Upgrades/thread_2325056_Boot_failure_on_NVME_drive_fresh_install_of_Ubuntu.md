---
title: "Boot failure on NVME drive fresh install of Ubuntu 16.04"
date: 2016-05-18
forum: Installation &amp; Upgrades
---

### Post by Alex_Dunkel on 2016-05-18
I have and Asus Z97-Deluxe/USB 3.1 motherboard, and just installed a Samsung 950 Pro on an Asus Hyper M.2 X4 Mini expansion card, which I inserted it into the 2nd PCIEX16 slot (PCIE 3.0) on the motherboard.  I unplugged all of my HDDs and booted to the Ubuntu installer on a USB thumb drive.  The installer saw the disk, allowed me to set partitions (which included a 200MB efi partition, which I pointed the boot loader to), and began to install.  During the first attempt, everything went smoothly, but when I went to reboot, it failed to boot at all.  It didn't even to a GRUB screen, let alone the Ubuntu splash screen.  I then reattached my HDDs, booted to Windows 10, used diskpart to clean this NVME drive, and then tried again.  This time the Ubuntu installer gave the error:


[INDENT]Unable to install GRUB in /dev/nvme[/INDENT]
[INDENT]Executing 'grub-install/dev/nvme' failed[/INDENT]
[INDENT]This is a fatal error[/INDENT]


Also, I tried setting CSM (Compatibility Support Module) to [Disabled] in the BIOS before the install.  Although it installed cleanly this time, upon reboot I get the follow error from the BIOS:


[INDENT]Notice[/INDENT]
[INDENT]The current BIOS setting do not fully support the boot device.[/INDENT]
[INDENT]Go to Advanced > Boot > CSM Parameters, and adjust the CSM (Compatibility Support Module) setting to enable the boot device.[/INDENT]


If I re-enable CSM, the system fails to boot (without loading GRUB).


Any ideas?  I didn't have these problems with the same NVME drive when connected directly to the motherboard's M.2 slot.  In fact, I used to see "ubuntu" listed in the boot options in the BIOS under that setup.

---

### Post by lukeiamyourfather on 2016-05-18
I suspect the motherboard doesn't support booting from a PCI Express device like NVMe unless it's from the slot dedicated for it. I would try reaching out to the motherboard manufacturer and reporting the issue. Or there might already be a BIOS update to resolve this with the specific hardware.

---

### Post by LostFarmer on 2016-05-18
You may need a newer version of 'grub'.  

A user over at Debian has the same problem. [http://forums.debian.net/viewtopic.php?f=17&t=128212](http://forums.debian.net/viewtopic.php?f=17&t=128212)

debian grub version 2.02~beta2-22+deb8u1 did not work but version 2.01~beta2-36 does.
I do not know what version Ubantu 16.04 uses.

---

### Post by Alex_Dunkel on 2016-05-19
> **lukeiamyourfather said:**
> I suspect the motherboard doesn't support booting from a PCI Express device like NVMe unless it's from the slot dedicated for it. I would try reaching out to the motherboard manufacturer and reporting the issue. Or there might already be a BIOS update to resolve this with the specific hardware.

This can't be it.  I just installed Windows 10 (in UEFI mode) on the same drive, and it boots fine.  So apparently it's not a motherboard problem.

> **LostFarmer said:**
> You may need a newer version of 'grub'.  

A user over at Debian has the same problem. [http://forums.debian.net/viewtopic.php?f=17&t=128212](http://forums.debian.net/viewtopic.php?f=17&t=128212)

debian grub version 2.02~beta2-22+deb8u1 did not work but version 2.01~beta2-36 does.
I do not know what version Ubantu 16.04 uses.

This may be it.  Unfortunately I'm too inexperienced with Ubuntu (or any Linux distro) to know how to fix it.  I did see this on the link you provided:

[https://wiki.debian.org/EFIStub](https://wiki.debian.org/EFIStub)

Could someone please translate this to work with the Ubuntu live installer?  And after I get Ubuntu to load without a bootloader, I'd like instructions for installing grub version 2.01~beta2-36... or whatever works.  I'm just not sure how to install a beta app.

I'm ultimately going to be running Ubuntu from the PCIE M.2 drive and Windows 10 from another NVME SSD on the motherboard's built-in M.2 connector.  In the past, grub automatically created a boot screen allowing me to choose between Ubuntu and Windows, and I'd like to have that again.

---

### Post by LostFarmer on 2016-05-19
It looks like ubuntu 16.04 does use the updated grub.  Alto grub could have been updated after its release.  I do not know how to check the version with a live linux.  I also do not currently have ubuntu installed nor have the 16.04 ISO.

  [http://packages.ubuntu.com/search?keywords=grub-efi&searchon=names&suite=xenial&section=all](http://packages.ubuntu.com/search?keywords=grub-efi&searchon=names&suite=xenial&section=all) **Package grub-efi-arm64**

    
[LIST]
[*][xenial]("http://packages.ubuntu.com/xenial/grub-efi-arm64") (admin):     GRand Unified Bootloader, version 2 (ARM64 UEFI version)             2.02~beta2-36ubuntu3 [**ports**]: arm64 
[/LIST]


added:  you could try in a terminal and run "apt-cache policy grub-efi " .   When you installed , was you online ?

---

### Post by Alex_Dunkel on 2016-05-19
> **LostFarmer said:**
> It looks like ubuntu 16.04 does use the updated grub.  Alto grub could have been updated after its release.  I do not know how to check the version with a live linux.  I also do not currently have ubuntu installed nor have the 16.04 ISO.

  [http://packages.ubuntu.com/search?keywords=grub-efi&searchon=names&suite=xenial&section=all](http://packages.ubuntu.com/search?keywords=grub-efi&searchon=names&suite=xenial&section=all) **Package grub-efi-arm64**

    
[LIST]
[*][xenial]("http://packages.ubuntu.com/xenial/grub-efi-arm64") (admin):     GRand Unified Bootloader, version 2 (ARM64 UEFI version)             2.02~beta2-36ubuntu3 [**ports**]: arm64
[/LIST]


added:  you could try in a terminal and run "apt-cache policy grub-efi " .   When you installed , was you online ?

No, unfortunately I'm not online when I install.  Ubuntu Live seems to fail to load the 3rd party drivers for my WiFi adapter, and it's a fight to get it working on an install.  I haven't tried tethering over Bluetooth with my phone in Live, but that's what I usually do later on the system when I'm trying to get WiFi working.

Keep in mind that this is not just a NVME issue with grub.  It installs fine when the same drive is plugged in to the M.2 connector on my motherboard.  It just doesn't seem to work when it's attached via a PCIE adapter.  It could possibly be a new bug.  What I may try doing is temporarily putting the card on my motherboard, install Ubuntu, then move it to the PCIE card... assuming that would work.

However, if it is a bug with either grub or the Ubuntu installer, I feel I should investigate and report it.  Where can I see the logs for the install, and how can I check what did get installed if I can't even boot to the OS?

---

### Post by oldfred on 2016-05-19
My 16.04 shows this:
apt-cache policy grub-efi-amd64
grub-efi-amd64:
  Installed: 2.02~beta2-36ubuntu3
  Candidate: 2.02~beta2-36ubuntu3

Never used efi stub to directly boot, but Ubuntu kernel parameters would have to be like Ubuntu not Debian.

       gparted should be at least version 0.24.0-1 to recognize NVMe devices
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)
Filesystem support
[http://ubuntuforums.org/showthread.php?t=2318570](http://ubuntuforums.org/showthread.php?t=2318570)

Vendors only test with Windows. So I also think it may be Asus and the extra add in card and how it is supported in UEFI.

But was the NVMe drive seen as sda? Ubuntu's grub only installs to the ESP - efi system partition on sda, so if drive not sda or if sda does not have ESP it fails to install. Or if a BIOS install and you have gpt partitioning on sda, but no bios_grub partition grub will fail to install in BIOS boot mode.

---

### Post by Alex_Dunkel on 2016-05-20
> **oldfred said:**
> Vendors only test with Windows. So I also think it may be Asus and the extra add in card and how it is supported in UEFI.

But was the NVMe drive seen as sda? Ubuntu's grub only installs to the ESP - efi system partition on sda, so if drive not sda or if sda does not have ESP it fails to install. Or if a BIOS install and you have gpt partitioning on sda, but no bios_grub partition grub will fail to install in BIOS boot mode.

The NVMe drive is not seen as sda; it had nvme in the name.  But then again, it was the same when installed on the motherboard's M.2 connector, and it booted then.  As you said, it may be a UEFI issue with the add-in card which was worked out for Windows only.  I doubt Asus will be releasing a new BIOS update.

I haven't figured out how to do a BIOS install because I can't find a way to disable Secure Boot on the motherboard. I'll try a few more things and report back if I have any luck.  Otherwise I might try my luck with CentOS (though I'm not feeling hopeful), and if I continue to have problems, I may just give up on Linux for now.

I'll be watching this post for any new ideas or detailed fixes.  I'm sure someone has managed to install Ubuntu on a Samsung 950 Pro M.2 SSD using an Asus Z97 motherboard.  I can't be the only one.

---

### Post by LostFarmer on 2016-05-20
On my Ausu laptop, the firmware has a very easy to use function to add a EFI boot entire.  If you motherboard also has the function, install on the M2 connector and put the hdd on the add-in card and try comps firmware 'add boot entire'.

We do not know if the problem is only the grub install or also booting grub from the M2 connector.

---

### Post by oldfred on 2016-05-20
On my Asus-AR which I would expect UEFI to be similar has Windows & "Other OS" which is really the secure boot setting. They say if installing Windows 7 you have to use "Other" as Windows 7 is not secure boot.

I also turned off fast boot until fully configured. Left normal boot on full cold boot or power on. That way I can get into UEFI if needed. Otherwise fast boot is too quick to use any key while booting. I also put 3 sec delay on reboot, 3 sec delay on grub menu so I can get into grub. But system boots faster than my delays, so I have greatly slowed reboot time. :)

I think screen shot shows UEFI first on USB or external, but I had to use UEFI only to get flash drive to boot in UEFI mode.

---

### Post by Alex_Dunkel on 2016-05-21
I figured it out.

The short story is that Universal USB Installer 1.9.6.4 was consistently corrupting 2 files when creating the USB boot device from the Ubuntu 16.04 ISO.

The first time I installed Ubuntu, I apparently created the USB installer using Rufus.  Everything worked fine then.  When I wanted to try out the other Linux distros, I also downloaded Universal USB Installer and grew to like its interface, so I never thought anything of it.  I became suspicious of the USB drives when install options changed with every reboot.  Before I tried going back to Rufus, I checked two USB drives I had been using, and both had the same two corrupted files, and no bad sectors.  Anyway, using Rufus 2.9, the USB installers I made checked out fine, and the install went fine, just as before.  The big difference was that I could boot from the fresh install.  NVMe and the add-in card were not issues.  Neither was UEFI or any of the BIOS settings.

I can't say that the install went perfectly.  I still get errors when I log in, and as was the case previously, installing my 3rd-party WiFi drivers was confusing.  (I tried to install them, but file locks and missing dependencies prevented me.  And then suddenly--about 10 minutes later--my WiFi came on after I had tethered with my phone over Bluetooth.)  Anyway, all of these minor issues aside, I'm up and running now, and I'll figure out the rest from here.

Thanks for all the help.

---

### Post by lptr on 2016-06-17
Having also a NVME drive problem, here.

Hardware is Intel NUC5i5RYK, m2 media is a Samsung SSD Model MZ-VPV5120

Installer working fine until it is getting to run grub-installer. This wants to install grub on /dev/nvme. 

To circumvent the problem I manually tried to install grub after failed Ubuntu installation. Did run
*sudo grub-install /dev/nvme0n1p1 *
that is containing root/boot filesystem on SSD. grub-install mentioned a failure: canonical path of /cow could not been found.

I do remember that easter egg "cow" when reading this. :(

Anyone having an idea what I did wrong or ist there a general problem with m2 SSDs of some sort?

---

### Post by bandyo on 2016-06-18
**[SIZE=3]Install grub in the drive, not in the partition[/SIZE]**

The NVME drive is recognized in Ubuntu using a different convention. Instead of */dev/sda*, */dev/sdb*, etc. you get */dev/nvme0n1, /dev/nvme0n2* etc. Note the first drive is *n1*. The partitions within the drives are *p1, p2*, etc. 

Grub should be installed in the MBR of the drive, not on the partitions. Ubuntu installed seems to get confused by the 0 in the drive identifier and tries to install grub in /dev/nvme and fails.

One can manually set to the correct device name */dev/nvme0n*1 during installation. Or use the command:

```
sudo grub-install /dev/nvme0n1
```

Note, it is just */dev/nvme0n1*. There is no *p1* at the end.

Hope this helps

---

### Post by lptr on 2016-06-19
@bandyo
thank you for reply. Cannot try this as I came to another solution.

In previous versions of Ubuntu I had this several times: Installation from USB stick drive did not work as expected. I remembered this and...

I took exactly the same .iso file that I used to setup the boot stick and burned a DVD-ROM. Guess: It ran through and installed GRUB, too. 

Why stick does not work and DVD does... don't ask me!

---


---
title: "Lenovo V15 G2  ALC  Ryzen 5700U + Ubuntu 21.04 - NVMe disk now missing - can't boot"
date: 2021-05-29
forum: Installation &amp; Upgrades
---

### Post by acesabe2 on 2021-05-29
Background: I've been using Ubuntu on and off since Warty and Hoary so I am pretty familiar with the system.

So I have just finally found a decent Ryzen Zen2+ laptop (~645&#8364; great price for the spec!) and while I know there can often be issues with newer hardware and available drivers for Linux, I tried out the latest Ubuntu 21.04 and everything worked OOTB from live session so I went ahead and installed:

As Ubuntu supports EFI secure boot, I chose to leave this option enabled in the BIOS....(error #1 no doubt)

During install I chose the advanced option for disk and chose ZFS (after reading up on pros and cons of this option)

Auto wiped and partition whole disk.

Also there was an option for using any proprietary drivers and media codecs which seemed like reasonable option, but i recall being prompted to use password for this option (MOKmanager it seems)

Install completed, rebooted, I did not have to enter any password at the MOK screen (happens before Grub screen iirc) as the option to boot was present and there was no info or instructions regarding using the other options so I continued.

System booted, all working nicely!

Installed available updates* and continued using.

*there was a firmware update package but cannot recall what, was not anything obvious related to any specific device or drive and did not seem to install when I tried, no way to find out what it was no without disk access anyway.

Next reboot - system unbootable. :frown:

In BIOS main page _there is no disk listed_, no option I have tried relating to disable secure boot or AMD PSP makes any difference.

My system can now get no further than the boot manger screen:

Boot Menu | App Menu

1. ubuntu
2. Windows Boot Manager
3. PCI LAN: EFI Network


I can boot to live USB session ok, I have even run: mokutil --disable-validation from terminal which on reboot brings up the MOK management util (if you boot again from live USB key) but this has made no difference.

I have read on Lenovo forums and elsewhere that if no boot config is found on an SSD NVMe drive, it will not show in the BIOS.

Pretty stumped, loading default settings in BIOS make no difference.

Hoping Windows recovery USB won't be the solution...(trying this option but is fraught with obstacles and frustrations!)

Am of course open to all suggestions from those with more recent experience of doing battle with UEFi or any ideas of secret options in the BIOS. 

The fact that the NVMe M.2 drive is not even listed in the BIOS now does not fill me with hope and the remote chance that something in the install/upgrade process may have borked the drive is although unlikely, quite a concern...TIA

From live USB session (yes this isn't the installed EFI boot config I know) to see the available boot devices):
[IMG]https://i.imgur.com/Id4uuOB.png[/IMG]

---

### Post by VMC on 2021-05-29
The easiest way to install Ubuntu with Windows, is to boot Windows and shrink its volume, then have Ubuntu live Gparted to create the partitions needed.
Then boot Ubuntu live and select Other and create you partition that way.

Under Lenova Setup Utility, go to Security look for Secure Boot section. There is where you turn it off or on. Unless I misread read your comment.

---

### Post by acesabe2 on 2021-05-29
Thanks for the reply, I didn't want the windows install what so ever and many years of experience tells me that trying to dual boot windows and Linux will end in tears sooner or later.

It's gone. Ubuntu happily wiped the disk and installed the OS to the SSD and rebooted into the new installation, so it worked. Once.

Since the first boot and subsequent upgrades (it's not impossible one of the upgraded packages did something as it was some firmware package, cannot remember what!) and reboot - no OS, no NVMe SSD visible in the BIOS (due to no readable OS seen by BIOS) nada.

BIOS "reset" doesn't impact the stored boot list, but no combination of BIOS boot settings will boot or recognise the NVMe disk.

Now in a world of pain and remorse trying to get the Lenovo (11Gig) recovery image written and installed to USB on VBox Windows install on a host system with insufficient memory and storage resources...happy days...

---

### Post by grahammechanical on 2021-05-29
From the Live session you should be able to run Gparted. It is installed. Does it see any discs/drives? Can you pull up a Grub menu? With UEFI we need to press the ESC key, perhaps several times to force the Grub menu to appear.

From the Grub menu you can choose Advanced Options for Ubuntu. If you got a kernel update then the original kernel will be in the list. Try loading with that kernel or the kernel that has a recovery mode.

Regards.

---

### Post by acesabe2 on 2021-05-29
Thanks for the reply, alas there is no disk seen from live session, nothing in /dev/nvm* nor BIOS (which won't report any NVMe disk without system installed on it).

In short there is no recovering a disk that is not visible to the host OS (in this case live USB session) in use.

I do wonder what would happen if I have a spare NVMe disk and swapped it out and rebooted, kind of seems unlikely there would be this sort of issue.

I suspect there is UUID record of the installed disk in the BIOS and due to change in OS install, it's now disabled as "security", which is after all what "secure boot" is all about. Would be nice to have a choice at install time rather than have to go through all this crap..

---

### Post by acesabe2 on 2021-05-29
So further clues after numerous attempts to create a Lenovo recovery USB drive (and failed to complete yet) I tried one of the failed attempts as it had the basic boot files copied across and booted the laptop form it and got:
[IMG]https://i.imgur.com/2GWu3Xl.jpeg[/IMG]

So not looking great so far...I have already tried a live Windows install USB drive and got no further than "Missing drivers, please select the drivers and..." ...there are no drivers that are usable from live install session...

I've now got the Lenovo USB Recovery Creator making the USB boot drive and looks like it will complete thanks to [this post]("https://forums.lenovo.com/t5/Windows-10/Problem-with-the-USB-recovery-creation/m-p/3600090?page=1#3604439") on the Lenovo forums (11Gig of files!) but I am now thinking there may actually be an issue with the drive itself...we shall see once the recovery drive completes but I rather suspect it will get no further than the screen above..

The above error code leads to post [https://answers.microsoft.com/en-us/windows/forum/windows_10-performance-winpc/windows-10-error-code-0xc000000f/765e013a-f3d0-472b-a92f-2f0ec14b0e6c](https://answers.microsoft.com/en-us/windows/forum/windows_10-performance-winpc/windows-10-error-code-0xc000000f/765e013a-f3d0-472b-a92f-2f0ec14b0e6c) which suggests Windows reinstall....fun fun fun...

[Edit] Might try the following from windows recovery USB session... [https://recoverit.wondershare.com/computer-problems/fix-windows-error-code-0xc000000f.html](https://recoverit.wondershare.com/computer-problems/fix-windows-error-code-0xc000000f.html)

---

### Post by oldfred on 2021-05-29
Was the firmware update an update to UEFI.
Some systems now support that from Ubuntu/grub using fwupd.
Devices using LVFS for firmware updates
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

If installing in UEFI mode and you need proprietary drivers, then you as owner, can in effect sign those drivers. Since proprietary drivers Ubuntu or anyone distributing those drivers cannot sign them for UEFI Secure Boot.
If you need signed drivers, often easier just to turn Secure Boot off, for now. In future we may find we need it.

An UEFI update resets UEFI settings to defaults. So any settings you changed have to be redone. UEFI does remember boot entries until drive is disconnected. Then UEFI boot entries often have to be updated with efibootmgr or reinstall of grub. Many UEFI do seem to auto find Windows, but not Linux.
I keep a list of settings for my system as I have 7 or so, some required & some optional that I change after every UEFI update.

Are you sure there is not a drive setting somewhere in UEFI settings.

---

### Post by acesabe2 on 2021-05-30
The fw update did not reference the UEFI or anything else that seemed familiar , but as it was being offered as available, I went for it...I really hope this is not the cause of the borkage!

The BIOS boot loader list seems also to be remembering the UUIDs of whatever is booting, but there is no way to edit these entries (ok there is efibootmgr but not sure it is much use for examining existing entries).

At this point I think I may as well grab my screwdriver and open up the machine, check the drive hasn't come loose some how and then try removing it then plugging it back in. The fact that if the drive contains an unusable/unreadable file system (ZFS??) makes the drive invisible is really quite something....What if I plug in a new M.2 drive? How can you reformat one when required if it is not visible to the BIOS or Live Linux/Windows system??

Bit of a cluster, but I'm holding back on firing blame in any one direction yet until it is clear what has happened...

---

### Post by VMC on 2021-05-30
Before you remove those 10 screws and pop the lid, boot with Ubuntu Live and open Terminal (Ctrl+Alt+t) and type ```
lsblk -f
``` so we can see your drive info

---

### Post by acesabe2 on 2021-05-30
Well I already popped the base plate to take a look after Lenovo recovery USB and standard Windows USB boot drives failed to detect the drive...
This is looking more and more like a dead SSD....
[IMG]https://i.imgur.com/2tfGdC1.png[/IMG]
I was pretty surprised at how small and flimsy the drive actually is but I re-seated it popped it all back together...no change...

So...was this just a dodgy drive from cheapo supplier or did installing Ubuntu 21.04 using ZFS fry it...?? We may never know...

Next steps...maybe RMA the drive (if it's possible, I'd rather not have to send the whole laptop back as it could be weeks and they'd almost certainly say "meh you installed an unsupported OS, bad luck") or just write it off and but a replacement, decent quality 512Gig drive....At this point I think I have pretty much exhausted all the possible software solutions...

---

### Post by oldfred on 2021-05-30
For more info on efibootmgr:
man efibootmgr

You can see details on all entries which use GUID/partUUID to find ESP.
sudo efibootmgr -v
And then see the partUUIDs:
lsblk -o name,fstype,size,fsused,label,partlabel,mountpoint

Typically you cannot edit UEFI boot entries, but can delete & create with efibootmg.

---

### Post by acesabe2 on 2021-05-30
Well the edfibootgr-v dos actually give some details about the boot entries stored:

[IMG]https://i.imgur.com/cebvBX0.png[/IMG]
but the lsblk command yields no more info than my previous post...

---

### Post by acesabe2 on 2021-06-01
Laptop being returned under warranty to Lenovo for repair with suspected dead SSD module...So who killed it? ZFS file-system? Mystery firmware update? We may never know...

---

### Post by acesabe2 on 2021-06-11
[Update] Laptop returned to Lenovo under warranty, SSD deemed faulty and was replaced, machine returned and now running 21.04 without issue.

Note, all secure boot options disabled before install, the laptop returned from repair with these disabled but new out of the box they were enabled, I installed Ubuntu in the space that was used by the default Windows install keeping the boot and recovery partitions just in case..., I used Ext4 this time rather than ZFS to play it safe, everything works other than Bluetooth which works but seemingly only after service restart see: [https://askubuntu.com/questions/1334098/bluetooth-not-working-in-ubuntu-21-04](https://askubuntu.com/questions/1334098/bluetooth-not-working-in-ubuntu-21-04) .

---


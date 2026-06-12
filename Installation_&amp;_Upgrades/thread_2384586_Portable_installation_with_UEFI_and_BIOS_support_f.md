---
title: "Portable installation with UEFI and BIOS support fails to boot on BIOS"
date: 2018-02-08
forum: Installation &amp; Upgrades
---

### Post by anathemort on 2018-02-08
I have found a deluge of articles and guides on building partitions for a portable installation.  I've tried to create an installation on an external SSD that can run on UEFI as well as BIOS systems.  So far, I have only been able to successfully boot into the installation on UEFI systems (one Dell laptop and one Macbook).  My home computer has a BIOS motherboard and when I try to boot into the external installation, I just get a blinking cursor on a black screen.  I've tried waiting 15+ mins and there has been no change, so I am concluding that it's hanging.

I ran BootRepair from a LiveUSB and generated this pastebin: [https://paste.ubuntu.com/26544128/](https://paste.ubuntu.com/26544128/)

[FONT=courier new]/dev/sdf[/FONT] is my external SSD with Ubuntu installed on [FONT=courier new]sdf**3**[/FONT]

My latest attemps have followed [https://askubuntu.com/a/559008](https://askubuntu.com/a/559008) without success.

Please advise any troubleshooting steps you can think of.

---

### Post by ubfan1 on 2018-02-08
You bios-boot partition should not have been formatted, and only needs to be 2M at most.  The complaint is not finding the core.img there at sector 1.

---

### Post by anathemort on 2018-02-09
> **ubfan1 said:**
> You bios-boot partition should not have been formatted, and only needs to be 2M at most.  The complaint is not finding the core.img there at sector 1.

I have seen some articles where it is formatted, some where it isn't.  I did try it unformatted and smaller in size, and I'm happy to try that again *but* how do I get core.img there at sector 1?

---

### Post by oldfred on 2018-02-09
Only with MBR installs is sector 1 used.
I have never seen and you should not see any instructions on formatting a bios_grub partition for BIOS boot. 
Perhaps confusion with the ESP - efi system partition which must be FAT32 formatted with boot flag for UEFI boot.

With gpt partitioning the gpt partition structures start at sector 1, so no space. Or that is why the unformatted bios_grub partition is required.
When installing grub to a gpt drive, it automatically finds the bios_grub partition and  puts core.img into it.
Note that with new very large drives the bios_grub must be within the first 2TB of drive.

While you can configure for UEFI & BIOS boot, your updates may get out of sync and then you may have issues.You may have to force a second update when booted in other mode.

The live installer works as it is fixed or does not change, so does not get out of sync.

---

### Post by anathemort on 2018-02-09
Thanks for the follow-up.  I have refactored the partitions and am attempting to run grub-install, but you can see the results in this screencap...

[ATTACH=CONFIG]278486[/ATTACH]

---

### Post by anathemort on 2018-02-09
I have a new BootRepair log too: [http://paste.ubuntu.com/=WyTVbZkm2w/](http://paste.ubuntu.com/=WyTVbZkm2w/)

---

### Post by oldfred on 2018-02-09
You now show grub in MBR of sdf and it looks for core.img starting as first sector of the bios_grub partition.

If you change to BIOS boot in UEFI, can you boot sdf?

---

### Post by anathemort on 2018-02-09
Nope, neither UEFI nor BIOS systems are booting now! 

Trying to follow the directions from that askubuntu thread I posted, but I get to the step "Creating a **BIOS Bootable Partition**", part 4 running grub-install, and I just get "grub-install: error: failed to get canonical path of `aufs' " which doesn't really help. So I googled a bit and found a few threads suggesting to run BootRepair, and that's what got me here.

Do you know a good step-by-step to follow?

---

### Post by oldfred on 2018-02-09
It looks like grub is installed.

So what happens when booting?
Boot-Repair in advanced options will also reinstall grub. And how you boot Ubuntu live installer, UEFI or BIOS is then how it will repair system.

What brand/model system?
What video card/chip?

The error is related to where you are installing vs. where partition is mounted.
Or possibly difference between UEFI install of grub vs BIOS install of grub.

These are the old BIOS install options which should still apply if BIOS install. 
Only if you have separate /boot you have to mount that.
Of if installing in UEFI mode, you must also mount the ESP.

 #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by anathemort on 2018-02-09
Thanks oldfred, that's helpful. I ran those steps as you outlined, and now I get a black screen with "grub rescue"... the error message is:
```
error: invalid extent.
Entering rescue mode...
grub rescue> _
```

This is on my BIOS system. Let's focus on that since it's my primary; I can tackle UEFI secondarily, I guess.

I am using an ASUS Crosshair IV motherboard with a Phenom II CPU and a Nvidia GTX 1080 video card.

---

### Post by oldfred on 2018-02-09
I found some old threads with that error.
Is system drive set for AHCI, not RAID nor IDE?

[https://ubuntuforums.org/showthread.php?t=1997316](https://ubuntuforums.org/showthread.php?t=1997316)

I do prefer smaller / (root) partition and then larger /home if newer user or separate /mnt/data partition for rest of drive.

---

### Post by anathemort on 2018-02-09
That's a hard question to answer! I have 6 SATA ports. I can configure ports 1-4 and 5-6 in the BIOS settings. Ports 1-4 are configured for RAID, and they host a pair of 1TB mechanical drives in RAID1; the other two ports here host two non-RAID 120GB SSDs. Port 5 and 6 are configured as IDE in the BIOS settings (my only other option is RAID, not AHCI). Port 5 has my optical drive, while port 6 has a third 120GB SSD.

Finally, keep in mind that I'm trying to get this running on a portable, external USB SSD, so I can't configure AHCI/RAID/IDE for this anyway. Maybe USB is always AHCI? I'm not sure how that works here.

I'm happy to blow away my partition table or do any other "restart" in an attempt to get this darned thing to work :P

---

### Post by C.S.Cameron on 2018-02-10
**Mkusb** will make a Persistent drive that works on BIOS and UEFI. 
You can confirm this on your machine before proceeding.

It is easy to change a **mkusb** Persistent USB to a Full install USB that also works on BIOS and UEFI.

Use mkusb to make a Live system on a USB (2GB or larger).
Use mkusb to make a Persistent system on a USB 16GB or larger, using default settings with ~12GB persistence.
Remove HDD before proceeding, (optional but recommended).
Insert both USB drives.
Boot Installer drive, select Install.
Select Something else.
Select sdb5, (the target drive), and click Change.
Select Use as: ext4, Format, Mount point /.
Don't touch any other partitions.
Select sdb5 for boot loader installation.
Complete installation.
Cut grub.cfg from sdb5/boot/grub and paste to sdb3/boot/grub, overwriting the existing grub.cfg file.
Delete sdb4, the ISO9660 partition and expand sdb5 into the recovered space.
Boot the target drive and run sudo update grub, (optional).

---

### Post by oldfred on 2018-02-10
Are your extra ports ASmedia ports?
I have seen issues installing on system with those ports in use, even when only DVD was plugged into that port.
Not sure if then it would interfere with USB port install?

I have installed multiple times to larger flash drives, both full BIOS with gpt and UEFI with gpt.
UEFI is more difficult as Ubuntu's grub only installs to ESP on sda, so you have to manually copy files to ESP on external drive.
And UEFI only boots from /EFI/Boot/bootx64.efi, so you have to copy /EFI/ubuntu to /EFI/Boot and rename shimx64.efi to bootx64.efi. Both copies are required as shimx64.efi is hard coded to look for more boot files in /EFI/ubuntu folder.

But BIOS installs where you select to install grub to MBR of external drive has always just worked.
And using Boot-Repair many users have reported it will reinstall grub correctly, if advanced options used and correct system & drive are chosen.

I do not AMD issues, but your nVidia will need nomodeset boot parameter until nVidia driver installed.
Some other AMD based motherboards needed IOMMU settings.
 Gigabyte GA-990FXA-UD3 and 64bit Xubuntu 16.04 LTS install
[https://ubuntuforums.org/showthread.php?t=2370503](https://ubuntuforums.org/showthread.php?t=2370503)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

---

### Post by anathemort on 2018-02-10
> **C.S.Cameron said:**
> **Mkusb** will make a Persistent drive that works on BIOS and UEFI. 
You can confirm this on your machine before proceeding.

It is easy to change a **mkusb** Persistent USB to a Full install USB that also works on BIOS and UEFI.

@C.S.Cameron, thanks for your instructions. Should I wipe out the existing partition table first? Or just use what I've got and let mkusb do its thing?


@oldfred thanks for the follow-up. I'll look at those options if the above doesn't work.

---

### Post by C.S.Cameron on 2018-02-11
I let mkusb do all the work and make a Persistent install using default settings.
Adjust persistence space to give as much NTFS partition as you need for Windows/Linux data, if any.
You can try the persistent SSD on your computer to confirm it works before converting it to Full install.
The Full install should work on any computer the mkusb Persistent install works on.

---


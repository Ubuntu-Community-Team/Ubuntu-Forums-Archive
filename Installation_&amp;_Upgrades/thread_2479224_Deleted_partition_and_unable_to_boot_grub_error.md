---
title: "Deleted partition and unable to boot grub error"
date: 2022-09-18
forum: Installation &amp; Upgrades
---

### Post by jaded747 on 2022-09-18
Hello everyone, I've been at this for a couple hours and I am a little stuck.

I had ubuntu (20.04, updated recently to 22.04) working fine and naturally I wanted to change that so I deleted a partition I shouldn't have. 

I have a 256 GB disk showing a 537 MB filesystem partition, then two 120 GB partitions split horizontally (instead of vertically?). I don't really understand how it got this way but the disk was getting full and I wanted that extra 120 GB of 'unused' space.

So everything is borked and I shouldn't have done that.

No problem, made a live-usb of 22.04 on a spare SSD and managed to boot into ubuntu (eventually).

I ran disk-repair and here is the log file.
[https://paste.ubuntu.com/p/GgZKGmr5Qq/](https://paste.ubuntu.com/p/GgZKGmr5Qq/)

I'm trying to run/install testdisk without any luck either based on another . At this point I am hoping to repair my grub on the original disk or worst case scenario recover my files from the old disk and do a clean install. 

If anyone can point me in the correct direction that would be great.

---

### Post by oldfred on 2022-09-18
You now only show FAT32 partitions on sda & sdb. And sdc shows FAT32 and no partitions.
FAT32 should only be used for smaller partitions like an ESP as it does not have journal and cannot have any file over 4GB.

You also have old BIOS/MBR configuration, but all systems in last 10 years are UEFI and should have UEFI installs on gpt partitioned drives.

If you converted a gpt drive to MBR, you erased drive.
Testdisk and then maybe photorec would be your only chance to recover anything. 

If you used one of your larger drives as the installer, by using dd to copy ISO, that totally erases the drive as it removes all partition table entries and makes a hybrid DVD/flash drive. First 4GB (size of ISO) is totally gone. Photorec may be able to find some data on rest of drive.

Best option always is to do new install & restore from your normal backup. That should take about an hour. Anything longer means you have not done backups & restore correctly.

---

### Post by Impavidus on 2022-09-19
> **jaded747 said:**
> 
I have a 256 GB disk showing a 537 MB filesystem partition, then two 120 GB partitions **split horizontally** (instead of vertically?). I don't really understand how it got this way but the disk was getting full and I wanted that extra 120 GB of 'unused' space.

In the built-in disks tool, this means that the top partition was an extended partition and the bottom one was a logical partition embedded in the extended partition. That's what extended partitions are for; it's a way around the limit of 4 partitions on MBR formatted drives. So it looks like you deleted your filesystem.

The best thing to do would be to reinstall Ubuntu and recover your important documents from a backup. If that drive space hasn't been overwritten yet, it may be possible to recover the entire filesystem. If it has been partially overwritten, you may still be able to recover some files, mixed with junk like old versions of those files and without filenames. I've never had to do this myself, so I can only give a link: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery). Look under Lost Partition.

---

### Post by jaded747 on 2022-09-19
> **Impavidus said:**
> In the built-in disks tool, this means that the top partition was an extended partition and the bottom one was a logical partition embedded in the extended partition. That's what extended partitions are for; it's a way around the limit of 4 partitions on MBR formatted drives. So it looks like you deleted your filesystem.

The best thing to do would be to reinstall Ubuntu and recover your important documents from a backup. If that drive space hasn't been overwritten yet, it may be possible to recover the entire filesystem. If it has been partially overwritten, you may still be able to recover some files, mixed with junk like old versions of those files and without filenames. I've never had to do this myself, so I can only give a link: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery). Look under Lost Partition.

Holy smokes guys, I was so close to getting this solved yesterday. The Datarecovery page that Impavidus linked was the ticket. I just ran parted and the rescue command as described to add it back to the partition table and all of my data was there! I have no idea if it is bootable though... My guess is I will still have an issue with grub. Copying some of my files over and will reboot and see what happens. Worst case scenario I'll do a clean install and copy the data back when I am done. Thank you!

> **oldfred said:**
> [COLOR=#000000]You also have old BIOS/MBR configuration, but all systems in last 10 years are UEFI and should have UEFI installs on gpt partitioned drives.[/COLOR]

[COLOR=#000000]If you converted a gpt drive to MBR, you erased drive.[/COLOR]

I didn't convert anything. This mobo doesn't have any option to install with UEFI as far as I can tell. I tried messing with the BIOS settings but there is no option for secure boot that I can see. So I did the install the old fashioned way, which worked. The computer is relatively new, just something I cobbled out of parts to be a streaming/filesharing workhorse on my home network. 

If anyone has any tips on the Grub rescue screen let me know. Otherwise I'll be back later with a progress report. Wish me luck.

---

### Post by oldfred on 2022-09-19
You may just need a grub re-install.
You can do that using live installer and adding Boot-Repair from ppa.
If most often suggests a grub update, which just updates menu. But in advanced mode you can choose the full reinstall of grub. Also select to install latest kernel.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by jaded747 on 2022-09-19
This again?
[https://paste.ubuntu.com/p/Gjr52KKgmK](https://paste.ubuntu.com/p/Gjr52KKgmK)

Edit: Yes, my motherboard is not compatible with UEFI for some reason.

Edit Edit: I wrote in my first post **disk**-repair but I was running **boot**-repair as described in the post above. (using live usb in "try ubuntu" mode and installing boot-repair from the terminal with ppa) That's where the pastebin log is from. I ran boot-repair again after adding to the partition table and will wait for a reply before attempting a repair. Thanks.

---

### Post by oldfred on 2022-09-19
You are showing mount of ESP in fstab which would mean a UEFI install? Line 178.
BIOS installs now want a FAT32 partition for ESP, even if not used. But they do not mount it as an ESP.
You also have grub installed to MBR. So either grub in MBR or Grub in ESP? (not shown) is not valid. You would have to boot live installer in UEFI boot mode to see UEFI info.

Reinstall of grub will fix only one boot mode.

Is F14 newest UEFI for your system? See line 71
What brand/model system or motherboard.
I have a Skylake Gigabyte board using f23a. But even if same brand, UEFI vendors may have different versions for different vendors or systems.

---

### Post by jaded747 on 2022-09-20
I'm not sure how that is possible. I struggled to install ubuntu the first time. When I boot a UEFI installer on USB or on disk it will not install. I'm 99% certain it is not compatible. I've been using Rufus for this.

F14 is the newest BIOS for my board. It's a gigabyte motherboard you can find on gigabyte.com/motherboard/GA-P55A-UD3P-rev-20

Thanks.

---

### Post by yancek on 2022-09-20
>  When I boot a UEFI installer on USB or on disk it will not install. 

That's curious as your boot repair clearly shows beginning at line 24 an EFI partition with the necessary EFI files to boot Ubuntu.  If your motherboard Is not EFI compatible that will not work.  Beginning at line 39, boot repair shows that sdb2 is a Legacy install of Ubuntu with the proper Grub files to boot.  Beginning at line 13, boot repair shows Legacy Grub installed an is looking for the remaining Grub files on "(,msdos5" which won't work as you have Ubuntu/Grub on sdb2.  Reinstall Legacy Grub pointing to the system partition, sdb2 and see if that helps

---

### Post by oldfred on 2022-09-20
That is an UEFI based motherboard. But it looks like first generation UEFI, which many vendors did not implement well.
Linux had to do many work arounds. And many vendor UEFI firmware updates required.
Even then, many users found BIOS boot to work better.

---

### Post by jaded747 on 2022-09-20
> **yancek said:**
> That's curious as your boot repair clearly shows beginning at line 24 an EFI partition with the necessary EFI files to boot Ubuntu.  If your motherboard Is not EFI compatible that will not work.  Beginning at line 39, boot repair shows that sdb2 is a Legacy install of Ubuntu with the proper Grub files to boot.  Beginning at line 13, boot repair shows Legacy Grub installed an is looking for the remaining Grub files on "(,msdos5" which won't work as you have Ubuntu/Grub on sdb2.  Reinstall Legacy Grub pointing to the system partition, sdb2 and see if that helps

I mean I can try booting it with EFI, I have nothing to lose except time. Just tell me what to do in boot-repair. Otherwise I'll reinstall legacy Grub pointing to sdb2 and see what happens.

I can come back with screenshots but my motherboard does not have any options in the BIOS/CMOS to install as UEFI. I was looking for secure boot options as well but the options are limited lol.

---

### Post by oldfred on 2022-09-20
How you boot the USB flash drive, UEFI or BIOS is then how it installs or repairs.
You should in motherboard's boot options, for the live installer, two boot options for the flash drive. One clearly UEFI:XXXX and other XXXX. Often XXXX is name or label of USB flash drive or PMAP.

---

### Post by jaded747 on 2022-09-20
I can't boot the usb drive as UEFI. I've gone through every setting, there is no SCM/Secure boot, there is no legacy mode, no UEFI mode.

When I try the usb drive I get the error message that I am trying to boot an EFI as BIOS. 

So I am going to wipe the drive and reinstall as MBR/BIOS because I don't have any other choice.

---

### Post by jaded747 on 2022-09-20
Well this is some convoluted system. It shows BOTH BOIS and EFI partitions on my drive. How the heck does that work?

But anyways, I'm back online, just restoring data from my backup and setting up my environment.

---

### Post by jaded747 on 2022-10-06
I'm going to go ahead and mark this as "solved" because I was able to retrieve my data. Thanks again to everyone.

---


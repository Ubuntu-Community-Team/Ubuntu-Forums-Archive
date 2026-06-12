---
title: "Yet another failing boot with EFI"
date: 2014-01-21
forum: Installation &amp; Upgrades
---

### Post by Amir_Hossein_Hajiz on 2014-01-21
Hi guys,

I know there have been lots of threads with the same problem, but the booting problem seems to be kind of unique to each device and each firmware, as I have tried every possible solution in a trial and error manner but no success.

A bit of a story: I purchased a Sony VAIO Pro 13, which comes with Windows 8. I tried to make it dual boot of Win8 and Ubuntu. Same as many others the biggest problem was that it was booting into Win8 directly. So I did some fixing but I ended up losing my Win8 and now I can't get it to boot into anything, seeing the famous error message of "Could not start Windows". I'm now trying to make it a single boot for Ubuntu 13.10.

Some info:
Boot repair stats: [http://paste.ubuntu.com/6791139/](http://paste.ubuntu.com/6791139/)
Secure boot: [Enabled]
Sony VAIO Pro seems to come with a recovery partition, which was /dev/sda1 and was marked as "boot" and "hidden". I accidentally deleted it. There was also an EFI after that recovery partition as far as I remember, which was marked as "boot". However right now I have deleted all of them and did a start fresh install on Ubuntu.

Has already tried (but didn't work):
Boot repair
Using efibootmgr to create an entry named "Windows Boot Manager"
Creating two EFI partitions to simulate what it was in the first place
Also please note that there is no quickboot or fastboot in the BIOS settings (or at least I can't find it). Also no Intel SRT settings.

Now I'm hopeless :( I don't want the Win8 back. Fully installed ubuntu is what I'm trying to get.

Thanks in advance for your help.

---

### Post by tfrue on 2014-01-21
You should disable secure boot, fastboot, and decide if you want to use a GPT disk or MBR. Then we can go from there, and I would suggest GPT.

---

### Post by oldfred on 2014-01-21
I think Sony is one that has the "buggy" UEFI. Or it has modified the UEFI to only boot Windows. That is not per UEFI standard, but the only way you can boot is to rename the Windows efi file and make it really be shim. Then UEFI thinks it boots Windows but really boots grub2's shim file. Grub2's shim has the Microsoft signing key and should work even with secure boot on, but often better to have it off.

You can use Boot-Repair or manually rename files. Even though you deleted Windows you still have the Windows efi files in the efi partition.
       buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)

   Boot-Repairs rename copies this /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi, becomes this:
/EFI/Microsoft/Boot/bkpbootmgfw.efi

   With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.
And a Windows update may rewrite the bootmgfw.efi file overwriting the shim version, so then if you can only boot the Windows version you have to rerun boot repair. If you can boot Ubuntu entry in UEFI menu, undo the rename.

  available as a "Rename Windows EFI files" option in the Advanced Options for the few UEFI that are modified to only Boot Windows efi file.
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply

 
   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.
    
       Sony - manually copy grub efi files & rename to make them work post #3
[URL="http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi"]http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi
[/URL]
 [http://ubuntuforums.org/showthread.php?t=2102083](http://ubuntuforums.org/showthread.php?t=2102083)
So this time installed 12.10, then  booted again from liveCD, made backup of (efi part)/EFI/microsoft/boot and copied all files from /EFI/ubuntu into it. Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi. And it works

    
 Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

---

### Post by Amir_Hossein_Hajiz on 2014-01-22
Thanks for all the info and help [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711"). You are a life saver. For future references I think I should share what happened and how I fixed it.

Beside the symptoms I mentioned earlier as the question, these are other things that happened along the way:

1- Boot repair didn't help. It actually put me in more trouble as it caused the issue that prevented me from booting into Win8 either.
2- efibootmgr didn't help. As oldfred has mentioned, it's due to the "buggy" firmware of Sony VAIO Pro
3- SecureBoot doesn't help. It detects that EFI is modified and prevents the boot saying that it's not the original or valid operating system (don't quite remember the error message)
4- Sony VAIO firmware is so hard-coded that the first time I used efibootmgr to delete Windows boot manager, I ended up having two "Windows Boot Manager" entries. The fake one that I created and one that Sony VAIO created on start up. De-activating that entry doesn't work either, nor does changing next boot or boot order, again due to #2.
5- Don't worry if you are seeing two EFI partitions. The first one is hidden and is for Sony recovery. Don't touch it (refer to [http://paste.ubuntu.com/6778553/](http://paste.ubuntu.com/6778553/), which is the info gathered by boot-repair before I ruin my Win8 setup)
6- Copying shimx64 didn't help. I copied grubx64 over bootmgfw.
7- As you can see in two pastebin links I have here, boot repair only did its job the first time, and before I ruin my partitions. I'd recommend avoiding it, specially if you can manually copy efi files.
8- Even after all these, I got to GRUB, but GRUB couldn't load into ubuntu. I used LiveUSB one more time and used this link to fix it (just followed the steps): [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.Ut-mZHiIbCI](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.Ut-mZHiIbCI)

One more time, thank you guys for the help.

---

### Post by Amir_Hossein_Hajiz on 2014-01-22
Also, for those who don't know how to copy efi files (I didn't know how to do it in the first place either). First you'll need the Ubuntu LiveUSB or LiveCD. Now assume EFI partition is under /dev/sdaX. If you don't know what number X is, you can use GParted (usually comes with Ubuntu). It's the partition marked as FAT32 and has "boot" flag. If you see two of them, it's probably the second one, as the first one is Sony VAIO's recovery partition (which is also marked as hidden). Now do:

```
sudo mount /dev/sdaX /mnt
sudo cp /mnt/EFI/Microsoft/Boot/bootmgfw.efi /mnt/EFI/Microsoft/Boot/bootmgfw.efi.old              # to have a backup
sudo rm /mnt/EFI/Microsoft/Boot/bootmgfw.efi                                                       # just to make sure you will copy the file correctly later
sudo cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmgfw.efi
sudo shutdown -r now                                                                               # restart
```

---


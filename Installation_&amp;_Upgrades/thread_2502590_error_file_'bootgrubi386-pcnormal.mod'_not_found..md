---
title: "error: file '/boot/grub/i386-pc/normal.mod' not found."
date: 2024-11-20
forum: Installation &amp; Upgrades
---

### Post by remarkub on 2024-11-20
I had been running Kubuntu 22.04 LTS on some older hardware, no dual-boot. After doing updates I'm getting this error and stuck in grub rescue mode.
```
error: file '/boot/grub/i386-pc/normal.mod' not found.
grub rescue> ls
(hd0) (hd0,msdos5) (hd0,msdos1) (hd1) (hd1,msdos1) (hd2)
```
Filesystem is unknown for each one of those except (hd0,msdos5), which contains my normal root directory.

I found the boot-repair tool and it suggests to ask in the forum to be sure that its recommended actions won't make the problem worse before I just go for it: [https://paste.ubuntu.com/p/fXSnRHyq6f/](https://paste.ubuntu.com/p/fXSnRHyq6f/)

sdb is a media drive from when I was running a mythtv recorder, sdc is the live usb.

I tried mounting sda1 in the live usb, and it appeared to be empty? Not sure if I should've expected anything to show up.

I don't remember seeing an option for UEFI in my bios.

Can anyone confirm that the boot-repair recommendation is the correct course of action? Thank you!

---

### Post by oldfred on 2024-11-20
Was system UEFI?
You have an ESP - efi system partition mounted in fstab for UEFI boot.
But since report run in BIOS mode, it does not show if you have UEFI entry for boot or boot files in ESP partition.
You also have grub in MBR.

After update only one grub will work, which every was updated last. Or maybe grub in MBR is correct & system should boot in BIOS mode or you have UEFI boot files in ESP and UEFI boot should work. But HP may need you to change settings, both default boot mode and UEFI boot setting.

---

### Post by remarkub on 2024-11-21
The system likely *was UEFI*, I do think I had first installed with a different motherboard and after the power supply caught fire, moved the hard drive to another case which had an older motherboard inside. It booted again, and since I had considered the services I had running too important, I left it up and forgot about any differences until now. 

It's now in an HP Compaq 6005 Pro MT PC. As far as I can tell, it is not capable of UEFI, though I would love to find out I'm wrong.

---

### Post by oldfred on 2024-11-21
Specs say its from about 2005.
If that is correct, then it is BIOS only.

I used Kubutu on my old 2006 Toshiba. It was slow and had limited memory. Ubuntu would not install, but Kubuntu did.
But found my external SSD with full install configured for UEFI boot would work on that old BIOS only system, if I added a BIOS boot stanza to directly boot the install on the SSD. Became very functional as long as I did not try to load too much at once.

---

### Post by remarkub on 2024-11-21
I can certainly relate to not being able to load too much on it, but I don't think the original UEFI motherboard was so much newer than this one. When I first moved it over, I didn't even notice any huge decline in function, and this is while it was serving as a dual-tuner PVR and media player.

Anyways, I'm no expert on boot configurations, which is why I'm using the repair tool. Will boot-repair do this for me, with either the suggested or custom settings?

---

### Post by yancek on 2024-11-21
Your boot repair output does not show any files for Ubuntu on the EFI partition (sda1).   If you can access that partition from a 'live' Ubuntu or other Linux, mount it and check to see if there  is an ubuntu directory there.

> sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
sudo ls /mnt/sda1/boot/efi/EFI

The normal.mod file in your case should be in the /boot/grub/i386-pc directory.  Mount sda5 and check to see if that file is there.  If you do not have it or do not have the i386-pc directory, you can copy it there from /lib/grub/.

---

### Post by remarkub on 2024-11-21
sda1 had been completely empty until I misunderstood your reply and copied normal.mod there.

Copying it to /boot/grub/i386-pc/ has resulted in a new error for grub rescue:
```
error: file '/boot/grub/i386-pc/extcmd.mod' not found.
```

Is it fair to assume that everything it's going to need, I can copy from /lib/grub/? Since I'm not sure what else is missing (or what happened to it), would I be well-served to just rename /boot/grub/i386-pc/ and copy the entire i386-pc directory over from /lib/grub/?

Thank you.

---

### Post by remarkub on 2024-11-21
Actually, I think I found them. [https://paste.ubuntu.com/p/S5q2zWwWsB/](https://paste.ubuntu.com/p/S5q2zWwWsB/)

As I was about to attempt copy the whole /lib/grub/i386-pc/ directory over, I wanted to make sure there were no symlinks I'd be missing, and saw that much of my /boot/grub/i386-pc/ contents had a ~ appended. What might have done this?

---

### Post by oldfred on 2024-11-21
If it is BIOS boot, I might use Boot-Repair in BIOS boot mode from live installer and use its advanced mode to totally reinstall grub and latest kernel.
I would expect that to remove the mount of the ESP in fstab, so then just BIOS boot.

---

### Post by yancek on 2024-11-21
The recommendation in post 9 would probably be the simplest.

In my earlier post, I meant for you to check /boot/grub to see if you had an i386-pc directory.  If you have a Legacy install that directory should be there with all the correct/needed files.  If that directory did not exist, it could simply be copied (the entire directory) from /lib/grub.

> saw that much of my /boot/grub/i386-pc/ contents had a ~ appended.  

That often is used to indicate a backup file and the original should also be there.  Brief discussion/explanation at the site at the link below.  If you have a file with a tilde (~) at the end of the name, there should be another file of the same name without the tilde.  If there isn't, that is a pretty good explanation of your problems but I have no idea how that would happen.

[https://security.stackexchange.com/questions/180756/what-does-the-tilde-mean-at-the-end-of-a-file-extension](https://security.stackexchange.com/questions/180756/what-does-the-tilde-mean-at-the-end-of-a-file-extension)

>  I would expect that to remove the mount of the ESP in fstab, so then just BIOS boot. 		

Yes or simply comment it out in fstab by putting a # character at the beginning of the line although if your computer isn't EFI compatible, no reason not to delete the line.

---

### Post by remarkub on 2024-11-21
Thank you both.

I want to clarify since this seems to be the big deal it feels like:
-Will boot-repair be in BIOS mode automatically? It has pre-selected "Use the standard EFI file" and "Separate /boot/efi partition:"=/dev/sda1 ? I don't see any other options that look like they pertain to BIOS as opposed to UEFI.
-Installing the latest kernel is done from the "Purge kernels then reinstall last kernel" option? Or does that just reinstall the most recent one that was already present? This option was *not pre-selected*, and the only thing I've seen that might justify going into Advanced options as suggested in post #9, rather than using its recommended repair.

Thanks again for all your help and patience!

---

### Post by oldfred on 2024-11-21
I think Boot-Repair is seeing the mount of the ESP in fstab & the ESP.
But if you boot live installer in BIOS mode & add Boot-Repair, in advanced options you should be able to choose.

You many need to remove mount of ESP in fstab & ESP partition, so Boot-Repair does not think it is an UEFI install.
The BIOS version of grub is grub-pc and the UEFI version of grub is grub-efi-amd64.

I have created a BIOS grub boot on an old laptop to boot an UEFI install on external SSD. Install works either way, its really just version of grub that is different between UEFI & BIOS and a few settings or required partitions.

---

### Post by yancek on 2024-11-22
> error: file '/boot/grub/i386-pc/extcmd.mod' not found 

You reported the above error in post 7.  That file should be in that directory.  On my system, there are 300 files in that directory.  If you don't have all the correct files there, you will continue to get errors.  If you don't have an i386-pc directory in the /boot/grub directory with all the necessary files you will continue to have problems.  You should take the suggestion above to either delete or comment out the entry for /boot/efi in the /etc/fstab file and reboot to test.  Verify that you have the needed file in the i386-pc files and if you don't, copy them there.

---

### Post by remarkub on 2024-11-28
Had to put this aside for a bit but I'm back.

> **yancek said:**
> You reported the above error in post 7. That file should be in that directory. On my system, there are 300 files in that directory. If you don't have all the correct files there, you will continue to get errors. If you don't have an i386-pc directory in the /boot/grub directory with all the necessary files you will continue to have problems. You should take the suggestion above to either delete or comment out the entry for /boot/efi in the /etc/fstab file and reboot to test. Verify that you have the needed file in the i386-pc files and if you don't, copy them there.

I've commented out the /boot/efi line from /etc/fstab and also copied every .mod file from /lib/grub/i386-pc/ to /boot/grub/i386-pc/ on sda5. Trying to boot from the hard drive still goes to grub rescue mode with the error:
```
error: sumbol `grub_disk_native_sectors` not found.
```
I'm definitely at a point now where I'd like to reinstall grub than chase each new error as it comes up. Newest boot-repair log at [https://paste.ubuntu.com/p/mdjbCpxR3S/](https://paste.ubuntu.com/p/mdjbCpxR3S/) now that I've made these changes.

> **oldfred said:**
> I think Boot-Repair is seeing the mount of the ESP in fstab & the ESP.
But if you boot live installer in BIOS mode & add Boot-Repair, in advanced options you should be able to choose.

You many need to remove mount of ESP in fstab & ESP partition, so Boot-Repair does not think it is an UEFI install.
The BIOS version of grub is grub-pc and the UEFI version of grub is grub-efi-amd64.

I have created a BIOS grub boot on an old laptop to boot an UEFI install on external SSD. Install works either way, its really just version of grub that is different between UEFI & BIOS and a few settings or required partitions.

I'm still not clear on how to boot live installer in BIOS mode, I haven't seen any options for that during the boot process. Closest thing I've seen is grub settings which brings up a text editor for changing setparams, but none of my research has found anything to get to the live installer in BIOS mode. Is it a different installer iso entirely? Otherwise I'm not sure where to find that option.

Attempting to apply any changes in boot-repair or run it gives this error:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294575&stc=1[/IMG]

Thanks again for your patience and help.

---

### Post by oldfred on 2024-11-28
Some UEFI have two sections. A UEFI boot option menu and a non-UEFI boot or BIOS/CSM/Legacy menu  depending on vendor.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

My system has UEFI : XXXX or XXXX all in one list. One clearly UEFI boot and the other BIOS/Legacy. The XXXX is name or label of flash drive.

How you boot live installer UEFI or BIOS is then how it installs or Repairs. Both Windows & Linux.

---

### Post by remarkub on 2024-11-29
> **oldfred said:**
> Specs say its from about 2005.
If that is correct, then it is BIOS only.

I used Kubutu on my old 2006 Toshiba. It was slow and had limited memory. Ubuntu would not install, but Kubuntu did.
But found my external SSD with full install configured for UEFI boot would work on that old BIOS only system, if I added a BIOS boot stanza to directly boot the install on the SSD. Became very functional as long as I did not try to load too much at once.

As you observed in post #4 this hardware predates UEFI (or close to it), so no such option is presented to me at boot time. It seems that it would then be automatically booting in BIOS mode, correct? And yet it seems I cannot convince the boot-repair tool to function in BIOS mode, as it insists that I need to disable the legacy mode. Is there something I can do to force it to recognize that I need a BIOS mode installation? And if not, can I accomplish what I need with the command line rather than relying on the automated GUI version?

I'm very sorry if I'm misunderstanding you and the solution is in front of me, but I don't recognize it. Thank you again

---

### Post by yancek on 2024-11-29
If you don't have any options in your BIOS referring to EFI/UEFI, I don't see why the installer is trying to do an EFI install.  Since you have commented out the /boot/efi entry in our /etc/fstab file (or deleted the entry) you could try deleting the EFI partition which shows as sda1 in boot repair.  The link below to the Ubuntu site explains how to reinstall Grub from a 'live' usb.  Under the sections Fixing a Broken System and via the live cd terminal sections.  Basically the partition and install Grub.  If you boot from a 'live' usb, the device name may be different so verify that from the live usb with sudo fdisk -l

```
sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
  
```

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by remarkub on 2024-12-01
> **yancek said:**
> If you don't have any options in your BIOS referring to EFI/UEFI, I don't see why the installer is trying to do an EFI install.  Since you have commented out the /boot/efi entry in our /etc/fstab file (or deleted the entry) you could try deleting the EFI partition which shows as sda1 in boot repair.  The link below to the Ubuntu site explains how to reinstall Grub from a 'live' usb.  Under the sections Fixing a Broken System and via the live cd terminal sections.  Basically the partition and install Grub.  If you boot from a 'live' usb, the device name may be different so verify that from the live usb with sudo fdisk -l

```
sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
  
```

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

Many thanks, this got me booted again!

---


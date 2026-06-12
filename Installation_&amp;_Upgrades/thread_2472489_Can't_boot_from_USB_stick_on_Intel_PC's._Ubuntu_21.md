---
title: "Can't boot from USB stick on Intel PC's. Ubuntu 21.10"
date: 2022-02-28
forum: Installation &amp; Upgrades
---

### Post by gil80 on 2022-02-28
It's probably not related to Intel, but I can only boot from my AMD based laptop.

I downloaded ubuntu 21.10 ISO file.
I used Rufus to copy it to my 8GB USB stick.
I booted to the ubuntu installation from the 8GB USB Stick.

In the installation process, I selected **OTHER** and then selected my 256GB USB3.0 Gen2 USB Stick.
I allocated 256MB as EFI partition and the rest is for the system.

Once installation is finished, I reboot and remove the installation USB. Testing the 256GB stick on my AMD laptop, I can boot into Ubuntu. However, both on my Intel PC and Intel laptop (Lenovo), I select to boot from the 256GB stick and the system reverts back to the BIOS menu to select boot disk option.
The Lenovo laptop won't even boot into the installation USB drive at all.

What am I missing here?

[https://cdn.discordapp.com/attachments/946862468431499305/947917207004926032/20220228_200417.jpg](https://cdn.discordapp.com/attachments/946862468431499305/947917207004926032/20220228_200417.jpg)
[https://cdn.discordapp.com/attachments/946862468431499305/947883980043190292/20220228_175227.jpg](https://cdn.discordapp.com/attachments/946862468431499305/947883980043190292/20220228_175227.jpg)

---

### Post by tea for one on 2022-02-28
On your Intel PC and Intel Lenovo Laptop, it is worth double-checking the UEFI settings:-

Disable TPM
Disable Secure Boot
Disable Platform Trust Technology
Disable Fast Boot
Disable Legacy mode
Check that Legacy USB Support is enabled

Depending on the vendors' UEFI configuration, there could be other settings to investigate?

---

### Post by gil80 on 2022-02-28
> **tea for one said:**
> On your Intel PC and Intel Lenovo Laptop, it is worth double-checking the UEFI settings:-

Disable TPM
Disable Secure Boot
Disable Platform Trust Technology
Disable Fast Boot
Disable Legacy mode
Check that Legacy USB Support is enabled

Depending on the vendors' UEFI configuration, there could be other settings to investigate?

If I was able to boot on the installation USB without changing any BIOS settings, why would it be different for the actual ubuntu USB stick?
Could it be that the AMD laptop from which I've done the installation is somehow configuring the USB ubuntu installation to be compatible with AMD devices only?

---

### Post by tea for one on 2022-02-28
> **gil80 said:**
> If I was able to boot on the installation USB without changing any BIOS settings, why would it be different for the actual ubuntu USB stick?
Please confirm that you can boot into an Ubuntu live session on both your Intel PC and Intel Lenovo laptop?

---

### Post by gil80 on 2022-02-28
> **tea for one said:**
> Please confirm that you can boot into an Ubuntu live session on both your Intel PC and Intel Lenovo laptop?

I can confirm that I can only boot into an Ubuntu live session on my Intel PC (Desktop) and AMD laptop. NOT the Lenovo Intel laptop.
But, my Desktop PC won't boot into the Ubuntu OS on the 256GB USB.

---

### Post by tea for one on 2022-02-28
Without knowing about the OS on your AMD laptop, perhaps the bootloader is installed on the PC where you made the Ubuntu external device?

When I make a full installation (including user name and password) to an external drive, I always isolate the internal drives so that Grub will be installed on the external target device.

---

### Post by gil80 on 2022-03-01
> **tea for one said:**
> Without knowing about the OS on your AMD laptop, perhaps the bootloader is installed on the PC where you made the Ubuntu external device?

When I make a full installation (including user name and password) to an external drive, I always isolate the internal drives so that Grub will be installed on the external target device.

On the AMD latptop I have Windows 11.
On my PC desktop I also have Windows 11.

I can see that in my Windows 11, my C: drive has Ubuntu bootloader (see screenshot above on the Samsung drive).
This is not desired.

So you believe that if I redo the installation on my external USB stick while all internal drives are disconnected, it would work? i.e., be able to boot from the USB stick regardless of the host hardware?

---

### Post by tea for one on 2022-03-01
> **gil80 said:**
> So you believe that if I redo the installation on my external USB stick while all internal drives are disconnected, it would work? i.e., be able to boot from the USB stick regardless of the host hardware?

It should work if the host hardware is compatible.
No success so far, therefore worth a shot - nothing ventured, nothing gained ;)
You may have to disable Trusted Platform Management and Secure Boot.

It will not work regardless of all host hardware e,g ARM devices, 32 Bit PCs, possibly Chromebooks inter alia.

It is impossible to provide clear, precise instructions due to the exact nature of a Windows PC.

Windows 10/11 + Secure Boot + Trusted Platform Management + Platform Trust Technology + Optane + Hibernation + Bitlocker + Trusted Supervisor UEFI + Raid + A Myriad of Other Settings.
All these conspire to inhibit the easy use of Ubuntu and family flavours.

---

### Post by ubfan1 on 2022-03-01
Or just look at the EFI parttiion on the USB stick.  It's FAT, and the Ubuntu bootloaders, grubx64.efi and  shimx64.efi should be in ...<whever mounted>/EFI/ubuntu.  If missing, the likelihood is that the install went to the internal disk.  A quick fix would be to just copy all the dirs/files from the internal EFI to the USB's EFI.  Then the USB should boot, no changes needed, since the UUID in the three line grub.cfg stub in .../EFI/ubuntu should be the USB's root.  Note, the USB may boot, but the launchpad bug 1396379 may leave the creating system unbootable without the USB present.

---

### Post by breakdaze on 2022-03-02
If you want to try to use GRUB boot loader to boot, it needs to be on the device, not the partition, as in /dev/sdd not /dev/sdd1 as shown in your photo.

You can try to use your UEFI BIOS to point directly to the EFI System Partition, like you have been, but you may have mixed results.

Also, from your Rufus USB stick, you should be able to add a custom entry to the grub.cfg to test booting the other drive, or test from the grub command line manually first. The easier method for the custom grub entry is to search for the label of the ext4 partition and set that to the root for grub to use, but you have to assign it a label first. Let me know if you want more details about this.

You could also run the boot repair disk on each system, just to run the Boot info Summary, and post those. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

What I would do, if you have time, is just reinstall Ubuntu 21.10 to the 256GB putting the boot loader on the drive, not the partition, as I mentioned above.

---

### Post by oldfred on 2022-03-02
+1 on ubfan1's suggestion.
The bug is very old, but still applies.
Ubuntu's ubiquity installer only installs to first drive's ESP (or MBR if BIOS). And with UEFI you cannot change that without leaping thru some hoops.
But you just need to move boot files, or reinstall grub either manually or with Boot-Repair to external drive.
External drives all boot from /EFI/Boot/bootx64.efi but full install also need /EFI/ubuntu folder.

Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive.

---

### Post by breakdaze on 2022-03-02
@oldfred So, does what I said apply too? The grub boot loader should normally be installed to the device /dev/sdX and not /dev/sdXN ? I didn't realize he needed to copy those EFI files also, but that makes sense. They were never installed. It sounds like he has Windows, attached an external USB 256GB drive, and slso attached a USB thumb drive, made that an installer media with Rufus, then used said Live system installer to install a full Ubuntu system to the external 256GB drive. After that he unugged the drive and brought it to various computers. So, maybe a grub menu entry using a search for the label of his partition would also be helpful. Since the actual computer he's attaching to changes.

After installing grub of course. I knew there are a few ways to reinstall grub. Another is the Grub for Windows as described on the Pen Drive Linux site. That works well under Windows.

---

### Post by oldfred on 2022-03-02
@breakdaze
You do always specify to install grub2 bootloader to a drive like sda, not sda1. But with UEFI, the boot files are automatically installed to an ESP - efi system partition.
Its just with Ubiquity installer that it defaults to the first drive's ESP. And even though it shows option to change location in combo box and with manual partitioning you can unmount & mount a different ESP, that does not work with installer. You can manually change ESP during install using terminal, but most users would not know to do that. And they have to have an ESP on the external or any second drive. Installer only creates ESP on first drive, if it does not have one.

But first choice should be just to reinstall grub manually or with Boot-Repair, if ESP is on external drive. Or copy files if user can do that. Then new install would be final option, but you still have to partition in advance & work around the Ubiquity bug.

---

### Post by gil80 on 2022-03-03
> **breakdaze said:**
> If you want to try to use GRUB boot loader to boot, it needs to be on the device, not the partition, as in /dev/sdd not /dev/sdd1 as shown in your photo.

You can try to use your UEFI BIOS to point directly to the EFI System Partition, like you have been, but you may have mixed results.

Also, from your Rufus USB stick, you should be able to add a custom entry to the grub.cfg to test booting the other drive, or test from the grub command line manually first. The easier method for the custom grub entry is to search for the label of the ext4 partition and set that to the root for grub to use, but you have to assign it a label first. Let me know if you want more details about this.

You could also run the boot repair disk on each system, just to run the Boot info Summary, and post those. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

What I would do, if you have time, is just reinstall Ubuntu 21.10 to the 256GB putting the boot loader on the drive, not the partition, as I mentioned above.

Thanks for the detailed info.

can you please provide more details this? 
> Also, from your Rufus USB stick, you should be able to add a custom  entry to the grub.cfg to test booting the other drive, or test from the  grub command line manually first. The easier method for the custom grub  entry is to search for the label of the ext4 partition and set that to  the root for grub to use, but you have to assign it a label first. Let  me know if you want more details about this. 

> What I would do, if you have time, is just reinstall Ubuntu 21.10 to the  256GB putting the boot loader on the drive, not the partition, as I  mentioned above.
I'll give it another go.

---

### Post by oldfred on 2022-03-03
If you have ESP on external drive, just reinstall grub.
If yo do not have an ESP use gparted from live installer to shrink a partition and add an ESP - efi system partition,  FAT32 with esp,boot flags.
Then use Boot-Repair and its advanced mode to reinstall grub. Advanced mode gives choice of install and choice of drive to install grub into. 
Default fix may or may not choose correct options for an external install. And often is just an update to grub menu.

---

### Post by breakdaze on 2022-03-03
@gil80 oldfred made me aware that there is a bug with the installer, so reinstalling may not be the best thing to do, unless you unplug the Windows drive with the EFI System Partition (ESP).

He's more familiar with the boot-repair disk, and it does sound like it would help you install grub and hopefully make the correct menu entry to get you booting.

I would still go back and do the label thing after booting into Ubuntu [https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

As far as the grub command line from the grub on the Rufus stick, you press c to get to the command line, then start trying ls to see where your vmlinuz and initrd.img files are for booting.

like: ls(hd0,1)/ ls(hd0,2)/ ls(hd1,1) etc

the hd starts at 0, but the partitions starts at 1

[https://www.gnu.org/software/grub/manual/grub/html_node/Command_002dline-and-menu-entry-commands.html](https://www.gnu.org/software/grub/manual/grub/html_node/Command_002dline-and-menu-entry-commands.html)
[https://www.gnu.org/software/grub/manual/grub/html_node/ls.html#ls](https://www.gnu.org/software/grub/manual/grub/html_node/ls.html#ls)

EDIT: After the ls, if you don't see anything, you may need to install a module in grub, depending if the drive is formatted with a GUID partition table  (GPT), then try again.

Then you either edit a grub menu entry and boot that, or manually pass the grub shell the commands to specify the path of the linux and initrd, then (if in the grub shell), finally issue the command: boot.

This would just be to test, because you probably won't permanently have the grub menu booting from your pen drive.

As far as ESP, the UEFI firmware needs a file on a FAT32 EFI System Partition, with the EFI loader for linux. When you used Rufus, the FAT32 formatted pen drive acts as this. On your full install, the ESP partition would have the directory /EFI/boot and the file bootx64.efi in there. On the Rufus USB stick, same thing, /EFI/boot/bootx64.efi but again, since it is already FAT32, it doesn't need a special EFI partition.

By the way, on my pen drive, the grub.cfg file is located in /EFI/boot/grub or X:\EFI\boot\grub under Windows, lol. But also check /boot/grub

My pen drive manually created menu entries to boot Windows 10 and Ubuntu 21.10 are this:

```
menuentry "Ubuntu 21.10 Desktop" {
  set root=(hd1,2)
  linux /vmlinuz root=/dev/sda3
  initrd /initrd.img
}

menuentry "Windows 10" {
  insmod part_gpt
  insmod chain
  set root=(hd4,gpt2)
  chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}

```

The part after linux /vmlinux root=   is for the linux kernel to know it's root, but set root=(hd1,2) is for grub to know where linux and initrd are.

---

### Post by gil80 on 2022-03-03
Ok, I'm a bit lost and overwhelmed :)

I really appreciate both of your detailed posts. I'm trying to make sense of things.

The things I'm trying to figure out now are:
1. How should I partition and format the 256GB drive?
2. Should I use Rufus?
3. Should I use the ISO installation live ubuntu USB to install?
4. If 3 is yes, then do I need to partition my 256GB to two partitions? If so, what each partition should be?
5. Using the boot-repair seems too complicated to use.
6. I don't know what is labeling partition and why to use it.
7. How to remove the ubuntu boot entry from my C: drive?

---

### Post by oldfred on 2022-03-03
As new user use gpt and just an ESP as FAT32 & / (root) partition as ext4.
You have to partition any second or external drive with gparted in advance.
Boot-Repair is for most users a lot easier than the manual chroot from live installer to new install, required to mount the install partitions, change root (CHROOT) and install grub to another install.

Depending on how you want to use 256GB drive, you may want additional partitions, but that becomes your choice depending on your use. I use a small / as my flash drives are more for emergency boot or repair and then large data partition for backup/copy of some of my data from my main working install. Flash drives are not as durable as SSD or HDD, so you should have another drive for backups.

You can use Rufus or one of many other install tools to create an install flash drive on a smaller flash drive which extracts the ISO to make a bootable drive. The installer typically erases entire drive, so you do not want to use a drive with data you want to preserve.

I also label partitions. Labels make sense. Better than c: drive, d: drive etc. And if you mount a unlabelled partition it uses UUID which makes even less sense.

This is my NVMe internal SSD. I have multiple other installs & data partitions on HDD and multiple flash drives with full install & data.
```

[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lsblkt [/COLOR]
NAME        FSTYPE   SIZE MODEL                          FSUSED LABEL     PARTLABEL            MOUNTPOINT PARTUUID
[/FONT][FONT=monospace][COLOR=#000000]nvme0n1            465.8G Samsung SSD 970 EVO Plus 500GB                                                   [/COLOR]
&#9500;&#9472;nvme0n1p1 vfat     512M                                 12.8M ESP_NVME  esp_nvme             /boot/efi  c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1 
&#9500;&#9472;nvme0n1p2 ext4    29.3G                                       focal_0   focal_0                         043d0f2a-48f1-4bcd-8d8b-df02a242436c 
&#9500;&#9472;nvme0n1p3 ext4    29.3G                                  9.7G focal_k   focal_k              /          c4d96c9e-eebb-43e6-b1b0-7ece2306cfee 
&#9500;&#9472;nvme0n1p4 ext4    29.3G                                       future    future                          a4d9289a-6beb-4e64-b11e-65aba5ddb884 
&#9492;&#9472;nvme0n1p5 ext4   195.3G                                  129G nvme_data nvme_data            /mnt/data  dfd49ef3-46a6-4cad-8f64-7b1696fba6fb


[/FONT]
```

---

### Post by breakdaze on 2022-03-03
I agree with oldfred about everything, and since you're new, let's try to make it simple.

1. don't do anything to the 256GB drive because the installer can do it for you. Tell the installer to use the whole drive.
1a. physically unplug all other SSD or hard drives
2. yes, use Rufus and your downloaded Ubuntu ISO to create an installer on a USB pen drive sized 32GB or less. This will wipe the drive.
3. yes. use all the automatic settings and tell it to install to your 256GB drive.
4. n/a
5. probably not, but, after you install, and still have issues, use Rufus on another small pen drive to make the Boot Repair USB stick live system. Run the thing that gathers information about your system. It will prompt you to upload thar report to Ubuntu pastebin. Link to the URL of that pastebin here on this thread.
6. read the Wiki article I linked to and what oldfred said, but let's just leave that for after you get Ubuntu installed and  booted on the 256GB drive.
7. Not sure what you mean by that, can you provide a photo? Or, gather the information using the boot repair as above.

---

### Post by gil80 on 2022-03-05
> **breakdaze said:**
> I agree with oldfred about everything, and since you're new, let's try to make it simple.

1. don't do anything to the 256GB drive because the installer can do it for you. Tell the installer to use the whole drive.
1a. physically unplug all other SSD or hard drives
2. yes, use Rufus and your downloaded Ubuntu ISO to create an installer on a USB pen drive sized 32GB or less. This will wipe the drive.
3. yes. use all the automatic settings and tell it to install to your 256GB drive.
4. n/a
5. probably not, but, after you install, and still have issues, use Rufus on another small pen drive to make the Boot Repair USB stick live system. Run the thing that gathers information about your system. It will prompt you to upload thar report to Ubuntu pastebin. Link to the URL of that pastebin here on this thread.
6. read the Wiki article I linked to and what oldfred said, but let's just leave that for after you get Ubuntu installed and  booted on the 256GB drive.
7. Not sure what you mean by that, can you provide a photo? Or, gather the information using the boot repair as above.

I cannot physically disconnect my nvme C: drive. It's buried deep under the GPU and water tubing. My BIOS only lets me disable SATA controller, not nvme controller.

So I guess I'm only left with the option to use the boot-repair, isn't it?
If I use the boot-repair Live-usb, then how can I be certain it doesn't break my Windows boot?

As for No.6, see this: [https://cdn.discordapp.com/attachments/946862468431499305/947917207004926032/20220228_200417.jpg](https://cdn.discordapp.com/attachments/946862468431499305/947917207004926032/20220228_200417.jpg)
Can you see the 2nd option? This is my main nvme C: drive where Windows 11 lives. For some reason, it has an ubuntu entry that doesn't actually boot into ubuntu on my 256GB USB stick, but simply boot into CLI grub. I would like to remove that entry from the boot menu. This option only appeared after I tried installing Ubuntu using the live-usb on my 256GB USB stick.

---

### Post by oldfred on 2022-03-05
The Ubiquity installer always installs to first drive.
So one of your older installs added that entry.

While you should be able to remove it in UEFI settings, not the UEFI boot menu. It is easy to remove with efibootmgr from Ubuntu.
You may also will want to remove /EFI/ubuntu folder from ESP partition on NVMe drive. Windows & Ubuntu do not normally show that partition.
Do not delete ESP & you want to keep /EFI/Microsoft & /EFI/Boot folders in ESP to be able to boot Windows.

# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

[https://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743](https://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743)

[https://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader/497720#497720](https://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader/497720#497720)

---

### Post by gil80 on 2022-03-06
> **oldfred said:**
> The Ubiquity installer always installs to first drive.
So one of your older installs added that entry.

While you should be able to remove it in UEFI settings, not the UEFI boot menu. It is easy to remove with efibootmgr from Ubuntu.
You may also will want to remove /EFI/ubuntu folder from ESP partition on NVMe drive. Windows & Ubuntu do not normally show that partition.
Do not delete ESP & you want to keep /EFI/Microsoft & /EFI/Boot folders in ESP to be able to boot Windows.

# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

[https://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743](https://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743)

[https://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader/497720#497720](https://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader/497720#497720)

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290120&stc=1[/IMG]

Both Windows and Ubuntu have the same HEX, so how can I issue `*sudo efitbootmgr -b XXX -B`*?

---

### Post by oldfred on 2022-03-06
Please do not post screen shots of termimal output. Just copy & paste. If longer use Code Tags.
Easy to add Code Tags with Forum's Go Advanced Editor & # icon.
For screen shots use Advanced editor and paperclip icon.

Ubuntu & Windows show same GUID, so booting from same ESP.
You use the 4 char code to identify each entry.
Ubuntu is 0000 and Windows is 0003.

---

### Post by gil80 on 2022-03-06
ok, thanks for the explanation and let me know about how to properly post terminal outputs.

By the way, what does this mean? > You may also will want to remove /EFI/ubuntu folder from ESP partition on NVMe drive is this done using the `efibootmgr` or do I manually delete folders?

---

### Post by gil80 on 2022-03-06
> **oldfred said:**
> Please do not post screen shots of termimal output. Just copy & paste. If longer use Code Tags.
Easy to add Code Tags with Forum's Go Advanced Editor & # icon.
For screen shots use Advanced editor and paperclip icon.

Ubuntu & Windows show same GUID, so booting from same ESP.
You use the 4 char code to identify each entry.
Ubuntu is 0000 and Windows is 0003.

Unfortunately, it didn't work.
Please see the attachment. It's still there.
I used `sudo efibootmgr -b 0000 -B`

Please, also see my previous post.

---

### Post by gil80 on 2022-03-06
> **breakdaze said:**
> I agree with oldfred about everything, and since you're new, let's try to make it simple.

1. don't do anything to the 256GB drive because the installer can do it for you. Tell the installer to use the whole drive.
1a. physically unplug all other SSD or hard drives
2. yes, use Rufus and your downloaded Ubuntu ISO to create an installer on a USB pen drive sized 32GB or less. This will wipe the drive.
3. yes. use all the automatic settings and tell it to install to your 256GB drive.
4. n/a
5. probably not, but, after you install, and still have issues, use Rufus on another small pen drive to make the Boot Repair USB stick live system. Run the thing that gathers information about your system. It will prompt you to upload thar report to Ubuntu pastebin. Link to the URL of that pastebin here on this thread.
6. read the Wiki article I linked to and what oldfred said, but let's just leave that for after you get Ubuntu installed and  booted on the 256GB drive.
7. Not sure what you mean by that, can you provide a photo? Or, gather the information using the boot repair as above.

I used the boot-repair live USB on my Laptop which has Windows installed on its internal SSD and Ubuntu on an external SSD, both worked fine.
This laptop was used to boot into the boot-repair USB stick while the 256GB USB Ubuntu stick was attached. I was trying to figure out how to install boot files into the 256GB. 
Not only that it didn't work, I now cannot boot into windows and the ubuntu on the external SSD. I only get Grub CLI. Luckily I didn't do it on my main desktop PC.

In summary:
1. Used laptop that has [B]Internal Windows 11 on SSD
[/B]2. [B]External SSD with Ubuntu

[/B]Both worked fine. I could select which operating system to boot from.

After using boot-repair live USB, to fix the boot on my 256GB ubuntu stick, all boot options are gone.


[B]UPDATE:

[/B]1. I was able to fix my **External SSD with Ubuntu, **using the live boot-repair USB**. **I'm now able to boot on my laptop to Ubuntu on the external SSD and Windows 11 **[1]**.

2. I was able to get my 256GB ubuntu USB stick to boot on my main PC desktop!! :) I don't know what was it that I did with boot-repair, but it seemed to work. The beauty of it is that ubuntu and windows are completely separate in the sense that I don't have a GRUB boot menu to choose from if the USB drive is not connected. It's only if it's connected then I can select to boot from it and then the GRUB boot menu appears and I can select Ubuntu.

3. I wasn't successful (yet again) in removing the ubuntu boot entry from my C drive as I posted in the image above.

**[1] **For my laptop - Given I need to have my External SSD with Ubuntu connected in order to show the GRUB menu to select either Ubuntu or Windows 11, if the external SSD drive is not connected then I'm not able to boot to Windows 11 at all, even if I change in BIOS to boot from installed OS. Is it possible to use boot-repair to have Windows 11 load independently from the external SSD ubuntu drive?

---

### Post by oldfred on 2022-03-06
Post the actual command & then efibootmgr -v command.

Do you have an ESP on external drive?
External drives do not boot from an Ubuntu entry normally.
They boot just like the live installer from a UEFI: USB entry that uses /EFI/Boot/bootx64.efi.
But a full install to an external drive needs the ESP with both /EFI/Boot & EFI/ubuntu folders as the version of bootx64.efi is really just a copy of shimx64.efi and need files/folders in /EFI/ubuntu.

You have to use a file manager in either Ubuntu or Windows, mount the ESP and look at the folders. Do not delete /EFI/Boot nor /EFI/Microsoft folders.
or in terminal manually mount and delete folder.

---

### Post by breakdaze on 2022-03-07
[https://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader#497720](https://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader#497720)

Remember what oldfred said there,
"You have to remove ubuntu folder from efi partition first or UEFI will re-add it. Then you have to remove UEFI entry from UEFI."

Before you use boot-repair, you may want to post the results of "Create a Boot Info Summary" for the system in question.

Remember, UEFI is the firmware on your motherboard, and it needs to find a FAT32 filesystem with an EFI loader that will load your OS, or GRUB. Normally this is done with a FAT32 formatted file system on a special partition called the EFI System Partition. Each different OS will have their own files in directories on that partition. Again, the files for Ubuntu are also there, and if you just delete the entry from your firmware settings, bit don't delete the files, then your UEFI firmware will just add the entry again.

Listen to oldfred also, he knows this stuff very well. And please post your "Boot Info Summary" to Ubuntu pastebin, then use that url here in this thread to get guidance.

And yes, if your UEFI firmware entries can point to the files on the EFI System Partition for Ubuntu and/or Windows, you don't necessarily need the GRUB bootloader.

EDIT: Like oldfred said, post the output of:
```
efibootmgr -v
```
That's a lowercase letter v.
You may want to read the man page[http://manpages.ubuntu.com/manpages/impish/man8/efibootmgr.8.html]("http://manpages.ubuntu.com/manpages/impish/man8/efibootmgr.8.html")

@oldfred I think the OP has a full install on the external SSD disk. What would be different about the UEFI firmware finding the ESP on that disk? Also, could the firmware detect an ESP on the external disk, as well as internal, or would it only see one at a time?

---

### Post by gil80 on 2022-03-08
> **breakdaze said:**
> [https://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader#497720](https://askubuntu.com/questions/429610/uninstall-grub-and-use-windows-bootloader#497720)

Remember what oldfred said there,
"You have to remove ubuntu folder from efi partition first or UEFI will re-add it. Then you have to remove UEFI entry from UEFI."

Before you use boot-repair, you may want to post the results of "Create a Boot Info Summary" for the system in question.

Remember, UEFI is the firmware on your motherboard, and it needs to find a FAT32 filesystem with an EFI loader that will load your OS, or GRUB. Normally this is done with a FAT32 formatted file system on a special partition called the EFI System Partition. Each different OS will have their own files in directories on that partition. Again, the files for Ubuntu are also there, and if you just delete the entry from your firmware settings, bit don't delete the files, then your UEFI firmware will just add the entry again.

Listen to oldfred also, he knows this stuff very well. And please post your "Boot Info Summary" to Ubuntu pastebin, then use that url here in this thread to get guidance.

And yes, if your UEFI firmware entries can point to the files on the EFI System Partition for Ubuntu and/or Windows, you don't necessarily need the GRUB bootloader.

EDIT: Like oldfred said, post the output of:
```
efibootmgr -v
```
That's a lowercase letter v.
You may want to read the man page[http://manpages.ubuntu.com/manpages/impish/man8/efibootmgr.8.html](http://manpages.ubuntu.com/manpages/impish/man8/efibootmgr.8.html)

@oldfred I think the OP has a full install on the external SSD disk. What would be different about the UEFI firmware finding the ESP on that disk? Also, could the firmware detect an ESP on the external disk, as well as internal, or would it only see one at a time?

Hi mate, thanks again to both of you. Unfortunately, I guess I'm too dumb as I don't quite understand the explanations of oldfred and the man pages I read are beyond my brain capacity. I don't understand them. Sorry for being such a drag...

Is there a simpler guide for dummies on how to remove boot entries and also how to convert an external SSD ubuntu installation to boot on any machine?

This is the pastebin of `efibootmgr -v` [https://pastebin.com/GHLAh7UR](https://pastebin.com/GHLAh7UR)
And this is the boot info [https://pastebin.ubuntu.com/p/42Hfy2vcjN/](https://pastebin.ubuntu.com/p/42Hfy2vcjN/)

---

### Post by oldfred on 2022-03-08
From Ubuntu live installer you run 
sudo efibootmgr -v
(and if you had posted it, I would not have had to repost it.

```

lubuntu@lubuntu:~$ sudo efibootmgr -v 
BootCurrent: 0005 
Timeout: 1 seconds 
BootOrder: 0003,0004,0005,0000 
Boot0000* ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb) 
Boot0003* Windows Boot Manager    HD(2,GPT,58109890-24f4-4389-8959-63895ba6189e,0x118008,0x32008)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)..BO 
Boot0004* ubuntu    HD(2,GPT,58109890-24f4-4389-8959-63895ba6189e,0x118008,0x32008)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO 
Boot0005* UEFI: SanDisk Cruzer Blade 1.26, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(8,0)/HD(1,MBR,0x36831,0x800,0xee8400)..BO
```

And as per man page example:
> [FONT=monospace][COLOR=#000000]**Deleting**[/COLOR][COLOR=#000000]** a **[/COLOR][COLOR=#000000]**boot**[/COLOR][COLOR=#000000]** option**[/COLOR]
       Assuming the configuration in the first example, [COLOR=#000000]**efibootmgr**[/COLOR][COLOR=#000000]** -b**[/COLOR][COLOR=#000000]** 4**[/COLOR][COLOR=#000000]** -B**[/COLOR][COLOR=#000000] could be called to delete entry 4 and remove it from the BootOrder. [/COLOR]
[/FONT]

And your entries then would be these:
sudo efibootmgr -b 0000 -B  # just 0 may work.
sudo efibootmgr -v # just to confirm order is still the same
sudo efibootmgr -b 4 -B    # or 0004

---

### Post by breakdaze on 2022-03-08
OK, help us understand which drives are inside the PC, and which are external. Hopefully you know your models.

```
sda:2000GB:scsi:512:4096:msdos:ATA WDC WD2003FZEX-0:;
1:1049kB:2000GB:2000GB:ntfs::;
sdb:1000GB:scsi:512:512:gpt:ATA Samsung SSD 860:;
1:1049kB:1000GB:1000GB:ntfs:Basic data partition:msftdata;
sdc:8004MB:scsi:512:512:msdos:SanDisk Cruzer Blade.

1:1049kB:8004MB:8003MB:fat32::boot, lba;
nvme0n1:2000GB:nvme:512:512:gpt:Samsung SSD 980 PRO 2TB:;
1:1049kB:587MB:586MB:ntfs::hidden, diag;
2:587MB:692MB:105MB:fat32:EFI system partition:boot, esp;
3:693MB:2000GB:2000GB:ntfs:Basic data partition:msftdata;
nvme1n1:2000GB:nvme:512:512:gpt:CT2000P2SSD8:;
1:1049kB:2000GB:2000GB:ntfs:Basic data partition:msftdata;
```
I'm guessing the SanDisk Cruzer Blade is the USB pen drive running to Boot Repair. 
The ATA WDC WD2003FZEX-0 (Western Digital desktop HDD) must be a regular HDD inside your PC.
The Samsung SSD 860 is internal?
Samsung SSD 980 PRO 2TB is also internal, it seems by the model, right?
Also the Crucial CT2000P2SSD8?
You didn't have the 256GB drive attached this time, or?
What is the make and model of that one?

---

### Post by breakdaze on 2022-03-08
Can you also post the output of
```
sudo blkid
```

So you have two things you are trying to do, right?
1) get rid of an UEFI entry on the motherboard 
2) have an external drive with a full installation of Ubuntu?

The 2nd one may require some extra work. Also depending on how you do it, you may need to do tweaking on each computer you attach it to. Also, every drive you plug in and out can change the disk order in Linux, UEFI, and/or Windows disk management.
Can you boot into Windows on this machine currently?

---

### Post by gil80 on 2022-03-18
> **breakdaze said:**
> OK, help us understand which drives are inside the PC, and which are external. Hopefully you know your models.

```
sda:2000GB:scsi:512:4096:msdos:ATA WDC WD2003FZEX-0:;
1:1049kB:2000GB:2000GB:ntfs::;
sdb:1000GB:scsi:512:512:gpt:ATA Samsung SSD 860:;
1:1049kB:1000GB:1000GB:ntfs:Basic data partition:msftdata;
sdc:8004MB:scsi:512:512:msdos:SanDisk Cruzer Blade.

1:1049kB:8004MB:8003MB:fat32::boot, lba;
nvme0n1:2000GB:nvme:512:512:gpt:Samsung SSD 980 PRO 2TB:;
1:1049kB:587MB:586MB:ntfs::hidden, diag;
2:587MB:692MB:105MB:fat32:EFI system partition:boot, esp;
3:693MB:2000GB:2000GB:ntfs:Basic data partition:msftdata;
nvme1n1:2000GB:nvme:512:512:gpt:CT2000P2SSD8:;
1:1049kB:2000GB:2000GB:ntfs:Basic data partition:msftdata;
```
I'm guessing the SanDisk Cruzer Blade is the USB pen drive running to Boot Repair. 
The ATA WDC WD2003FZEX-0 (Western Digital desktop HDD) must be a regular HDD inside your PC.
The Samsung SSD 860 is internal?
Samsung SSD 980 PRO 2TB is also internal, it seems by the model, right?
Also the Crucial CT2000P2SSD8?
You didn't have the 256GB drive attached this time, or?
What is the make and model of that one?

I'm guessing the SanDisk Cruzer Blade is the USB pen drive running to Boot Repair.  - **CORRECT**
The ATA WDC WD2003FZEX-0 (Western Digital desktop HDD) must be a regular HDD inside your PC. - **CORRECT**
The Samsung SSD 860 is internal? - **YES**
Samsung SSD 980 PRO 2TB is also internal, it seems by the model, right? - **YES AND THIS IS THE WINDOWS BOOT DRIVE (MAIN DRIVE)**
Also the Crucial CT2000P2SSD8? - **INTERNAL**.
You didn't have the 256GB drive attached this time, or?** I DIDN'T HAVE IT ATTACHED.**

---

### Post by gil80 on 2022-03-18
> **breakdaze said:**
> Can you also post the output of
```
sudo blkid
```

So you have two things you are trying to do, right?
1) get rid of an UEFI entry on the motherboard 
2) have an external drive with a full installation of Ubuntu?

The 2nd one may require some extra work. Also depending on how you do it, you may need to do tweaking on each computer you attach it to. Also, every drive you plug in and out can change the disk order in Linux, UEFI, and/or Windows disk management.
Can you boot into Windows on this machine currently?

1) get rid of an UEFI entry on the motherboard - **YES. I think this entry is installed on my main C: drive, the Samsung 980 PRO.**
2) have an external drive with a full installation of Ubuntu? - **YES, SUCH AS THE 256GB USB STICK TO BOOT FROM ANY PC.**

---

### Post by oldfred on 2022-03-18
Lets see where you are now at:

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by gil80 on 2022-03-20
> **oldfred said:**
> Lets see where you are now at:

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


Can you please clarify?
> use ppa version with your USB installer (2nd option) or any working install

Why shouldn't I use the boot-repair iso to generate the report? I don't know how else to generate the report.

---

### Post by oldfred on 2022-03-20
The ppa is typically updated more frequently. So we prefer to use Ubuntu live installer & add the ppa.
For any repairs that Boot-Repair cannot fix you need the live installer anyway.

If you only have the Boot-Repair ISO as a bootable device you can use it.

---

### Post by breakdaze on 2022-03-20
> **gil80 said:**
> 1) get rid of an UEFI entry on the motherboard - **YES. I think this entry is installed on my main C: drive, the Samsung 980 PRO.**
2) have an external drive with a full installation of Ubuntu? - **YES, SUCH AS THE 256GB USB STICK TO BOOT FROM ANY PC.**

LOL, no need to do the bold and ALL caps thing, we're trying to help, but we need to be on the same page, and next time connect the 256Gb USB stick.

FYI, some people see ALL CAPS as SHOUTING and it is often seen as not polite. :) My ALL CAPS below are NOT shouting. :)

First, do what oldfred says, and I will just let him help you out from here on out, but let me give you some background about the UEFI specification, and how it typically works. You said the entry is on the C: drive, which isn't correct, and so let me clarify.

[SIZE=4]1) Your motherboard firmware is the UEFI type, and the boot entries are actually saved on a chip on your motherboard that your firmware can access.[/SIZE]
**[SIZE=4]This entry you see at boot is not stored on ANY disk, it is on a special chip the firmware uses, usually a NON-VOLATILE RAM chip. This boot entry is also known as a BOOT VARIABLE[/SIZE]**

[SIZE=4]2) Each boot entry that is installed when you install an operating system does two things, a) creates a boot entry that is stored on the chip b) creates or adds boot files to a special partition on your disk, called the EFI System Partition, also known as the "ESP" for those who like abbreviations.
3) As a user in Windows, you can't normally view the contents of the ESP, it is not in the C: drive or any other partition you normally see.
4) The UEFI specification can only use FAT specification filesystems (FAT32, FAT16 or FAT12), but usually FAT32.[/SIZE]

This means that:

1) When you **install Ubuntu**, then Ubuntu makes a custom "Ubuntu" entry and** stores this on the chip on your motherboard**, then adds files to the ESP under \EFI\Ubuntu\ such as \EFI\Ubuntu\grubx64
2) Typically when you then boot into your install of Ubuntu, this ESP is mounted and visible under the directory /boot/efi, thus if you look in /boot/efi/EFI you should see the Ubuntu directory.
3) If you don't go into /boot/efi/EFI/Ubuntu, delete those file(s) **FIRST**, then delete the Ubuntu directory, then using that *efibootmgr *program to remove the entries from your motherboard chip, then the entry could reappear because **Ubuntu puts it back onto the chip** when it finds the /EFI/Ubuntu directory!

Your UEFI firmware also typically will be able to find generic removable devices, but only if they have been made UEFI bootable, and that means those must either be FAT32 formatted OR have their own ESP with the correct files for UEFI to use.

So, if you go and install Ubuntu to an external drive, it could very well add the UEFI entry to the chip on your motherboard, and files to your existing ESP (that Windows ALSO uses (with it's own directory, files, and entry on the chip).

Ubuntu also usually installs the GRUB boot loader somewhere (ESP usually), depending on the installer and your choices. This is a separate thing, but for UEFI to access this grub boot loader, it too needs to be on a FAT32 volume, and have a file that UEFI can load.

Here is yet more information about how it all works: [https://wiki.debian.org/UEFI](https://wiki.debian.org/UEFI)
Namely of use:

> Booting from removable media

If there are no boot variables pointing to a bootloader program in the ESP, or if the user has told the system appropriately, it will look for bootloaders in certain specific paths too. On each device, it will look for FAT32 filesystems. Within each of those, it will look for a specifically-named bootloader file, again with a different name per architecture:

Architecture - amd64
Path - \EFI\boot\bootx64.efi 

Which means this is the default place the UEFI specification will look on an external USB drive, so it's probably best to set it up like this, and NOT use a custom entry called Ubuntu or whatever OS. Make sense?

There are many reasons a particular PC's firmware could have trouble booting a USB drive, or things you need to do to make it show up, here are some possibilities: [https://neosmart.net/wiki/boot-usb-drive/](https://neosmart.net/wiki/boot-usb-drive/)

Furthermore, if you make a drive UEFI bootable, and the PC you attach to is in LEGACY BIOS mode, or just OLD and is a BIOS (not UEFI) firmware, you would need to make the drive BIOS bootable as well!

best of luck!

---


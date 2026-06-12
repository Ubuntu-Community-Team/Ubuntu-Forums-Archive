---
title: "Installation process installs Ubuntu, but not GRUB"
date: 2024-10-12
forum: Installation &amp; Upgrades
---

### Post by drhex on 2024-10-12
My system has 3 OS partitions - One for the current OS, one for the previous and one even older. All 3 OSes are versions of Ubuntu.
When a new version is available, I let it overwrite the oldest version. That way I can boot into older versions and compare or copy files to the newer OS.
This worked fine for many years up until version 23.10.
When I installed Ubuntu 24.04, it formatted the partition and copied in all the files as expected, but at restart the GRUB menu was unchanged and it booted into 23.10 as if GRUB was not updated.

As a workaround, I could solve this by editing **/etc/default/grub** in 23.10 so that the
**GRUB_DISABLE_OS_PROBER=false**          line was activated and then running ```
update-grub
```
After a reboot, 24.04 was now available as a grub menu option so I could access the newly installed OS.
I hoped this was just a temporary bug in the 24.04 installer, but now after installing Ubuntu 24.10, the boot process is still loading **/boot/grub/grub.cfg** from the old 23.10 partition.

I did not notice any grub-errors in the installation process.

Is there something special that needs to be done during installation of Ubuntu 24.04+ in order for GRUB to be updated?    I don't want ta have to keep 23.10 around forever in order to install future versions.

---

### Post by oldfred on 2024-10-12
I also have multiple installs on both SSD, HDD and if external SSD plugged in even more. 
You have to manage grub boot.
Easiest way is to boot into install you want to use as main working install & reinstall (not update) grub. If UEFI and entry in fstab has correct ESP, this is all you need, but assumes many defaults on UEFI grub install.
sudo grub-install

Boot process is UEFI entry, using GUID/partuuid to find ESP partition. Check that partuuid is correct for ESP you want to use.
In ESP is a 3 line grub configfile entry to full grub.cfg in your install. Only one entry, so UUID needs to be newest install's UUID. You can manually edit that file with correct UUID, but default mount of ESP in fstab locks it. You can change mount to default from 0077, but then it is less secure. Or edit from live installer.

To see details:
sudo efibootmgr -v  # not newer version now has too much detail, but older versions needed  -v to see partuuid.
This works for me as I changed mount of ESP.
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /boot/efi/EFI/ubuntu/grub.cfg [/COLOR]
search.fs_uuid 811e6de9-cd5e-4983-9f45-5e72e73cb578 root  
set prefix=($root)'/boot/grub' 
configfile $prefix/grub.cfg
[/FONT]
```

I find with multiple installs, better to turn off os-prober and copy boot stanzas into 40_custom for older installs.
examples from cavfan
[https://ubuntuforums.org/showthread.php?t=2392441&p=13816046#post13816046](https://ubuntuforums.org/showthread.php?t=2392441&p=13816046#post13816046)
Using 40_custom & Custom menu
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[https://askubuntu.com/questions/1425637/how-can-i-add-windows-11-to-grub-menu](https://askubuntu.com/questions/1425637/how-can-i-add-windows-11-to-grub-menu) &

---

### Post by drhex on 2024-10-13
Thanks for the info.  Logged into the 24.10 partition, I ran
```
grub-install /dev/nvme0n1
```

It did its job and said "no error reported".  It had no effect though, after a reboot I still get the 23.10 partition's grub menu.

Also tried putting the Linux Mint-based boot-repair disk from [http://www.debugpoint.com/boot-repair-disk]("http://www.debugpoint.com/boot-repair-disk") on a USB-pin, booted from it and ran its repair tool, explicitly selecting the 24.10 partition.
It also had no effect on subsequent reboots.

---

### Post by drhex on 2024-10-13
Getting closer to finding the problem now!
On the SSD, there is also an EFI partition with boot-related stuff on it.  The files there have timestamps from October 2023 indicating they were written around when I installed Ubuntu 23.10.
The old 23.10 also has a mountpoint at **/boot/efi** and an entry in /etc/fstab to mount that EFI partition.

My newer 24.04 and 24.10 installations though have no EFI entry in their **/etc/fstab** and there is no **/boot/efi** mount point.
Maybe there is some extra checkbox I should have ticked during the installation?

---

### Post by ajgreeny on 2024-10-13
I'm not on my Xubuntu box at the moment but I think your grub-install command needs to tell the system to start using grub from the 24.10 not the older version.
I tried the simple command shown by oldfred when I first installed the 24.04 version to my 22.04 box but wanted 22.04 to still manage grub, but when booting to 22.04 and running grub-install it didn't work.
Once I get to my Xubuntu box I will show you the command you may need to use to solve this problem as I can't remember the exact syntax required.

---

### Post by drhex on 2024-10-13
Works now!

I re-ran the Ubuntu 24.10 installation process, overwriting everything.  On previous Ubuntu installations, the only thing I used to change was to indicate the desired root partition and tell the installer to mount it at "/".
This time I also clicked the EFI partition and told it to format it as **vfat** and mount it at **/boot/efi**
I also had to explicitly tell it to use my **swap** partition for swapping  (otherwise it creates a 4 GB file for that).

Previous installers did the last two things automatically.

---

### Post by ajgreeny on 2024-10-13
[I]Whoops!!
Sorry but I missed you post that you added since my last visit here.
I will l;eave the rest of this however just in case it helps in any other situations.[/I]

Firstly, I hope I have understood exactly what you want on your computer, which is that 24.10 should be the default OS that you boot into from grub and that you want 24.10 to be the OS that manages grub rather than either of your older versions.

Try booting into 24.10 from whichever grub you currently have and from 24.10 use command ```
sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi     --bootloader-id=ubuntu --recheck --no-floppy
```
This has worked for me at least twice, maybe more times, and the system now manages and uses grub from the OS that I want, ie, the OS from which I ran that command, in my case 24.04 as I use LTS versions only.

---

### Post by oldfred on 2024-10-13
If you do not have the mount of an ESP in your fstab, that would probably indicate a BIOS boot install.
Many UEFI systems will default boot either BIOS or UEFI where others require specific setting in UEFI for one or the other.

How you boot install media, UEFI or BIOS/Legacy/CSM is then how it installs. UEFI should clearly be shown, but BIOS may just be name or label of flash drive.

New systems starting about 2020 are UEFI only. My Dell laptop says BIOS, but once in "BIOS" it says UEFI only.

---


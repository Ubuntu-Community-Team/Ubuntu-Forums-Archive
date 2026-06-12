---
title: "USB UEFI Install results in multiple boot options."
date: 2015-09-21
forum: Installation &amp; Upgrades
---

### Post by ben161 on 2015-09-21
After reading all the USB and UEFI posts on both this forum and Rods pages, I'm at a loss.

I installed Linux Mint Cinnamon onto a 64GB USB stick from a UUI Live USB.  I don't want to use a Live USB version with persistence due to performance and size restrictions.

As per the guidance, I created the following partitions:
-efi (400MB)
-/ (59GB)
-swap (4GB)

(note I didn't create a separate home partition as I want the size of the home partition to be flexible and not lock in the size of the root)

I chose to encrypt the home directory on installation.

I can boot it fine in UEFI with Secure boot if I choose the correct instance.

My issue is the booting menus and options.

As per the guidance, in windows8, hold the shift key and select 'reboot'.  The machine reboots into the UEFI menu with the following options:
-Continue
-Use a Device
-Troubleshoot
-Turn off PC

I select 'Use a Device"

This then provides the next menu which is the issue:
-Internal Hard Disk or Solid State Disk
-Ubuntu
-ubuntu
-USB Drive (UEFI)
-Internal CD/DVD ROM Drive (UEFI)

I've tested the three options that may boot my installation.  Options 2, 3 and 4 above.  
-Ubuntu with a capital U, fails with a "Selected boot image did not authenticate.  Please press <Enter> to Continue."
-ubuntu with a lower case 'u' works perfectly.
-"USB Drive (UEFI)" fails as per option 2.  "Selected boot image did not authenticate.  Please press <Enter> to Continue."

Questions:
1. Why would the UEFI be scanning and detecting Ubuntu twice?
2. Surely Option 4 should be the logical choice and work?  It is a successful UEFI Secure boot installation, so very weird this fails.
3. What is the difference between the two Ubuntu instances and why is UEFI picking up the two different Ubuntu instances.
4. Could this possibly be due to where I selected for the bootloader during the 'something else'?  I tried an installation for each, selecting sdb, the EFI partition and the root partition.  All installs resulted in the same scenario.

I'm aware that UEFI scans the disks on boot to look for bootloaders and at the moment am vaguely assuming that there is a rogue instance of a boot loader creating the instance in the menu of "Ubuntu".  Still I would love to know 'why':-).

PS.  I tried to use boot-repair and all it did was brick the installation.

---

### Post by Bucky Ball on 2015-09-21
Are you trying to install Ubuntu or Mint? While Mint is based on Ubuntu they are not the same.

---

### Post by oldfred on 2015-09-21
Normally there are two ubuntu UEFI entries. One is shim (grub) for secure boot and the other grub.
And if secure boot is on, then grub will not boot, only shim. Both should work with secure boot off.

Standard install defaults boot loader to sda, usually internal drive. And path is /EFI/ubuntu.
But if removable drive only boots from /EFI/Boot/bootx64.efi which is not created on a full install to a second drive or any external drive. You have to manually create it.

You need to copy all of /EFI/ubuntu from sda to external drive's efi partition. And then copy again to /EFI/Boot. Then rename /EFI/Boot/shimx64.efi (or grubx64.efi) to bootx64.efi. 
The reason you also need the /EFI/ubuntu folder is that the full install of grub seems to be hard coded to find /EFI/ubuntu/grub.cfg which is a simple configfile entry to find the full grub.cfg in your install by UUID.

After making those changes, my full install on a flash drive works.
Note that when booted into an UEFI ubuntu install, fstab mounts the efi partition at /boot/efi. Or then full path is /boot/efi/EFI/Boot to sda's efi partition. I also copied as fallback or default boot on my Ubuntu install in sda, so I have this:

```
fred@trusy-ar:/boot/efi/EFI/Boot$ ls -l
total 2260
-rwxr-xr-x 1 root root  956792 Sep 30  2014 bootx64.efi
-rwxr-xr-x 1 root root 1355736 Oct  8  2014 shimx64.efi

```

---

### Post by ben161 on 2015-09-22
Thanks oldfred!  I think I understand what you are saying.  One hitch.  The only UEFI machine I have is this one.  sda (internal hard drive) is running windows8.  So I'm not quite clear when you say "[COLOR=#000000]You need to copy all of /EFI/ubuntu from sda to external drive's efi partition."[/COLOR]  sda /EFI/ubuntu doesn't exist.  I did the complete install on sdb (the USB stick).  Can you clarify?

Cheers.

Ben.

---

### Post by oldfred on 2015-09-22
Every time I have installed to sdb internal drive or external flash drive in UEFI mode, it always has installed a /EFI/ubuntu folder in sda's ESP. I even told it to install to the ESP on sdb or flash drive and during install it says installing grub to sdb, but it overwrites my efi boot files in sda. I have several installs of Ubuntu and main working install is on sda. I quickly learned to backup efi partition so I could restore direct boot to main working install on sda.

If you do not have a /efi/ubuntu in the sda drive's ESP, then did you install in BIOS boot mode?

Live installer does not make it easy to copy files anymore. User is 999 and all my ext4 partitions are full install's default of user 1000. But FAT32 partition does not have as many user, ownership and permission issues as Windows formats do not support those. 

My newest full install of Ubuntu 15.10 on sdb changed mount of efi partition to 777 from defaults, so no one can use it. I had to change mount of efi partition to defaults like my 14.04 install to be able to edit ESP. Have not installed a full install of newest version to flash drive yet.

If you have the two Ubuntu entries in UEFI, then you must have /efi/ubuntu in ESP.

Post this from live installer's terminal:
sudo efibootmgr -v
and you should get something like this:
Boot0014* ubuntu    HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File(\[COLOR=#ff0000]EFI\UBUNTU\GRUBX64.EFI[/COLOR])..BO

---

### Post by ben161 on 2015-09-22
WOW, it's all becoming clearer.  I had no idea that the live installer even touched the hdd of sda.

Output from the terminal of the USB installation booted, not from the live installer:
 sudo efibootmgr -v
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0001,3001,0000,0002,2001,2002,2003
Boot0000* ubuntu    HD(2,145800,82000,c980ff80-3f8a-4142-9801-9c790c9ecc22)File(\EFI\ubuntu\shimx64.efi)
Boot0001* Windows Boot Manager    HD(2,145800,82000,c980ff80-3f8a-4142-9801-9c790c9ecc22)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}.../................
Boot0002* Ubuntu    HD(2,145800,82000,c980ff80-3f8a-4142-9801-9c790c9ecc22)File(\EFI\ubuntu\grubx64.efi)RC
Boot2001* USB Drive (UEFI)    RC
Boot2002* Internal CD/DVD ROM Drive (UEFI)    RC
Boot3001* Internal Hard Disk or Solid State Disk    RC

Is there a best practice for cleaning up the sda EFI boot files?

cheers.

Ben.

---

### Post by oldfred on 2015-09-22
Once you copy them to flash drive and confirm you can boot flash drive without issue, you can just delete /EFI/ubuntu folder.
You also can delete with efibootmgr the hard drive entries using the /EFI/ubuntu files.
Or you can just leave them.

I believe you will just be using the UEFI USB entry to boot flash drive. And that by default uses the /EFI/Boot/bootx64.efi. But if grub or shim must have the /EFI/ubuntu/grub.cfg and probably some of the other support files in /EFI/ubuntu.

There also is a way to directly install grub to a removable device.  I have used that to create a smaller flash drive to directly boot ISOs with only grub & ISO on flash drive. It puts a slightly different configuration of grub that only looks in the /EFI/Boot folder for all its files.

---

### Post by ben161 on 2015-09-23
Thanks Oldfred!  Really appreciate your experience insights and advice!

Please forgive my ignorance as I'm from a networking background and not a unix/linux super user by a long shot.

Can you possibly outline the basic steps you took for the copy process.  I seem to have an issue once I have booted to a live USB or CD. 
-Am I correct in understanding that you do all of this from a live USB and not the installed USB?
-How do you view and check the contents of the unmounted EFI partition prior to copy?
-How do you perform the permissions change (partitions, files and folders) to default?  I assume there is not "revert to default" flag so you have to know exactly what permissions where.
-How do you perform the copy?  
-As a best practice where do you copy your partition to?

Cheers.

Ben.

---

### Post by oldfred on 2015-09-23
Windows NTFS & FAT32 do not have permissions & ownership except when mounted from Linux and that is only defaults, not details by folder & file like Linux supported file systems.

I think I have used Nautilus, perhaps with sudo, and have used command line to copy files. I use Nautilus to see files & often to copy path to terminal. If you click on path at top of Nautilus you can paste into terminal. I will type sudo then cntrl-shift-v to paste from keyboard, or use gui/mouse.
Where mounted and typing the paths is often the issue for me as not expert on typing.
I always label partitions so default mount is by label not some very long UUID that I cannot copy easily. With gpt there are two labels, one partition & one filesystem. I usually make them the same or slightly different like ESP, efi or USBefi. I use Disks to label if I forget when creating partitions with gparted, but you also can use gparted to set labels.

I have the commands posted in detail in link in my  signature for one drive. With external or second drive you then also have to mount it. And it then depends exactly on where you mount each. All the times I have done it were from my working install in sda, so my commands would be different.

Try Nautilus first. If that does not work easily then I maybe can post details, but would need details on partitions.
sudo parted -l

If Linux partitions I do have a couple of commands I use for my /mnt/data partitions to set them similar to /home's permissions.

---


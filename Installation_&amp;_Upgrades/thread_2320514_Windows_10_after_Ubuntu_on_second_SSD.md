---
title: "Windows 10 after Ubuntu on second SSD"
date: 2016-04-14
forum: Installation &amp; Upgrades
---

### Post by quickdry21 on 2016-04-14
I built a new desktop machine and need to install Window alongside Ubuntu. I know the traditional logic is that you should install Windows first, then install Ubuntu, but I got so danged excited I went and installed Ubuntu first, as I only need Windows for gaming.

Now I am looking to slap Window onto the second SSD in the box and I'm having a hard time finding any advice that pertains to my situation - most documentation I can find speaks more towards installing the two OSs alongside each other on a single disk.

It's a UEFI install, Ubuntu on an NVMe M.2 SSD, Windows 10 will be going on a SATA connected SSD. Ideally I can keep Windows 10 dirty paws off the primary Ubuntu NVMe SSD all together, it should live in isolation on the second SSD like the outcast it is.

Disconnecting the NVMe SSD during the Window install _should_ do the trick, but is that really necessary? Is Windows really going to start messing with the bootloader of a completely different disk? I mean, how does it know which I am going to boot off of.

Anyways, it's been a *long* time since I've installed Window onto anything, I'm hoping I can be lazy and not have to disconnect anything, but I'm skeptical I can give Window that much credit. I know, worst comes to worst, I can reinstall grub 2, but at that point I would probably just do a complete reinstall, my new baby has to remain perfect :D

---

### Post by oldfred on 2016-04-15
In BIOS mode, Windows installed to second drive when first drive is default in BIOS and Ubuntu on sda or first drive, Windows installs a 100MB boot partition to boot drive. Since it does not see Linux partitions it just overwrites the first 100MB often totally corrupting Ubuntu.

With UEFI both systems normally share the same ESP - efi system partition.
You do want to be sure to install Windows in UEFI boot mode and just like Ubuntu how you boot install media, is then how it installs.

But with UEFI you do not set default boot drive and with NVMe drive not sure what Windows will see.

I suggest good backups which you should normally have as a standard procedure anyway. Just make sure it is current.
I would probably try the Windows install just to see what it does.

Perhaps someone else has installed Windows second with UEFI. I have not installed Windows since XP ten years ago.

---

### Post by quickdry21 on 2016-04-15
Ubuntu is installed in UEFI, the second drive will be wiped clean with a new GPT partition table. 

I'm not concerned with losing anything, everything is replicated with git and syncthing. 

I'm more concerned with losing time, but that's not the end of the world. 

I'm probably going to just install Windows 10 with the Ubuntu SSD in and see what happens. 

My hopes are not high that this will go smoothly. 

Either way I'll report back with what happens, maybe I can share my experiences with anyone looking for info in the future.

---

### Post by quickdry21 on 2016-04-15
Not going to lie, I'm feeling pretty good about myself after this one.

So, after reading around I learned that UEFI firmware looks at the /efi folder of each attached drive, there is no longer a master boot record that Windows overwrites (which is what I remember happening back in the day).

Ubuntu installs to it's own folder, /EFI/ubuntu - all should be good right, Windows will just install its own boot code leaving poor old Ubuntu alone!

Luckily for me I backed up my /boot/efi directory, just in case. I installed Windows 10 on my second SSD, and it decided to wipe the EFI boot partition on the primary SSD.

Windows 10 install seems to have fully reformatted the EFI partition on the main SSD, resulting in a loss of ubuntu boot files and renaming of the partition UUID.

Seeing is how I couldn't find a lick of information on installing Windows 10 *after* Ubuntu, here is what I did:

* This only applies to UEFI installs
* I'm dual booting from two SSDs - this _should_ work when dual booting from the same drive as Windows 10 did not create an EFI partition on the drive I installed it to, it only mucked with the EFI partion on the dedicated Ubuntu drive.
* My "primary" SSD is running on M.2 NVMe, the "secondary" Windows 10 install SSD was running on SATA slot 0 - again, I doubt this makes any difference but I haven't tested otherwise.

1. Install Ubuntu as normal on primary (NVMe) SSD
2. *very important* back up ubuntu efi boot files, they live at /boot/efi/EFI/ubuntu - you can copy them to the partition you installed Ubuntu to - as long as they are available when booting to a Live CD later
2. Create a new partition table of type GPT on secondary SSD (left partition table empty, all unallocated space)
3. Install Windows 10 to secondary SSD - this will make Ubuntu unbootable
4. Boot Ubuntu Live CD
5. Mount the EFI partition - the live cd won't let you do this through the GUI, so figure which one you want with `sudo fdisk -l`, then mount it somewhere
6. Copy the ubuntu boot efi files you backed up into the mounted EFI partition, this is what it should look like after:

$ sudo ls /boot/efi/EFI
Boot  Microsoft  ubuntu

7. This is the tricky part - when Windows overwrites the partition, the disk UUID changes - what Ubuntu had saved to /etc/fstab is no longer valid. It took me a few attempts of failed boots to figure this out - I would get to grub (so the EFI boot had succeeded at least) - but then it would hang after selecting Ubuntu.

So, get to grub and boot ubuntu into recovery mode.

Drop to a root terminal.

Figure out the new UUID of the EFI partition (you will need to know what the device path is, /dev/sdx1 sort of thing, for me it was /dev/nvme0n1p1 but NVMe is special)

$ blkid /dev/nvme0n1p1
/dev/nvme0n1p1: UUID="A846-E136" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="21f1cb33-15c6-4e68-a256-ba829b9c77c1"

Write down the value in quotes for UUID="    ...    "

Edit /etc/fstab, there will be a line that looks like:

UUID=A846-E136  /boot/efi       vfat    umask=0077      0       1

Update the UUID (note this is mine after fixing)

8. Reboot - feel like a linux master

I'm not entirely sure why I am writing out this semi-detailed guide, maybe there are others out there who will wish to do something similar. If there are others, this is a very high level guide, you will have to be comfortable with a terminal

---

### Post by oldfred on 2016-04-16
Thanks for the write up. 

I find that my second install of Ubuntu to sdb, would not install to an ESP - efi system partition on sdb, even though I clicked that in Something Else, and it even said during install - installing grub to sdb. But it only overwrote the /EFI/ubuntu folder.
I also learned quickly to back up ESP. :)

Older versions of Ubuntu used 'defaults' not 'umask=0077' as parameters in fstab. I now change mine back to default. With 0077, you have no permissions to do anything while booted in your install to ESP. Or only from live installer as you found out.

```
# /boot/efi was on /dev/sda1 during installation
UUID=FD76-E33D  /boot/efi       vfat    defaults        0       1

```

---


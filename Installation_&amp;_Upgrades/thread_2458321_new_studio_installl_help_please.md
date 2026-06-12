---
title: "new studio installl help please"
date: 2021-02-21
forum: Installation &amp; Upgrades
---

### Post by 1byte on 2021-02-21
can anyone help me with this>? i choose to install alongside win10 but it chooses another HDD I can't change, and I want it on the SSD with win10 - i tried "something else" but over my head a bit
thanks
I've done it before but long time ago with mint

---

### Post by Impavidus on 2021-02-22
Use Windows tools to shrink the Windows partitions on the SSD to make room. You can use gparted on the live disk to create Ubuntu partitions, or you can do it in the installer. Select the partition, click "edit", set filesystem type and mountpoint, then install. On UEFI systems, the bootloader is automatically put in the efi partition of the first drive.

---

### Post by 1byte on 2021-02-22
and do i just create the one single partition?
or do I create 3 as it seems the way linux works, a partition for home, swapfile and OS
thanks for the help

---

### Post by 1byte on 2021-02-22
i created a partition on the SSD but still wouldn't let me chose the SSD from first option and o something else when I highlighted that partition it threw up som error which I cant remember what it said but I wasn also unable to TICK the partition for formatting,  used Minitool Partition wizard, I have since undone the partition back to what it was as its obviously the wrong way

---

### Post by Impavidus on 2021-02-23
Minitool PartitionWizard is a Windows tool that only knows about Windows partitions (FAT and NTFS). It's good to shrink Windows partitions, but useless when dealing with Linux partitions. Use gparted. It's included on the live disk.

There are many ways to partition your hard drives for Ubuntu and there's no simple right or wrong. At the very least you need a root partition, where the main part of the OS and applications are stored. Put it on the SSD. It must be at least 30GB (technically, it can be less, but you'll have to be careful) and it must be of a type that supports UNIX-style permissions, so no NTFS or FAT. Use ext4 unless you have some good reason to use something else. The mountpoint for the root partition is /.

A swap partition is optional. If you don't create one, the installer will create a swap file instead. In that case, make sure there's enough room for it on the root partition (about 4GB).

A /home partition (mountpoint /home, best to make it ext4 too) is where your documents and personal settings will be stored. It's optional, but keeping your documents outside the root partition is recommended on larger systems. There are other ways to do it.

What do you want to do with your other hard drive? Is it for documents you want to share between both OSs? Or do you want your /home partition there?

Most Windows 10 systems use UEFI and GPT partitioning, which is good. Some use dynamic disks, which is bad, as this is some Windows extension that doesn't work with Linux.

---

### Post by yancek on 2021-02-23
Reading the official Ubuntu Documentation on the subject at the link below before trying to install again should answer your questions.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by rbmorse on 2021-02-23
Compatibility support mode (CSM) should be disabled in the EFI setup.  Also, make sure fast startup and hibernation are disabled on the Windows installation, then do a complete shut down (power off) from the Windows session before trying to install a Linux.

---

### Post by slickymaster on 2021-02-23
*Thread moved to **Installation & Upgrades**.*

---

### Post by 1byte on 2021-02-23
this is an old 2009 SandyBridge PC with BIOS not UEFI
all that instructions./ etc are totally over my head - dunno why they cant make it simpler

---

### Post by 1byte on 2021-02-23
ok so even installing it on another drive didnt work.... ive installed mint before on my dd machine and my own years back, why is it so difficult now? is it cos im using UBUNTU STUDIO m not the ones everyone coming from windows uses so installers are probably better/easier?

P.S. Minitool DOES do Ext4 etc

---

### Post by Impavidus on 2021-02-23
> **1byte said:**
> 
P.S. Minitool DOES do Ext4 etc
Does it? I didn't see it mentioned on their website. This time, I actually checked. Quickly.

What about giving us some data?

How are your ssd and harddrive currently partitioned? Where do you want the Ubuntu operating system and applications, your user settings, your documents? Do you want your documents to be available from both operating systems? It's normal for a computer from 2009 to be bios, it's less common for such an old computer to run Windows 10 satisfactory. Dual booting with Windows 10 can be a bit of a hassle, in particular in bios mode. It was easier before Windows 8. What are the specs of that computer? In particular memory, CPU and graphics hardware. If 12 years old, Ubuntu may be too much for it, but the lighter flavours may be fine.
> **1byte said:**
> all that instructions./ etc are totally over my head - dunno why they cant make it simpler
If you wipe Windows, it's really simple.

---

### Post by 1byte on 2021-02-24
i have:
2 x 2 TB drives and 1 x 500GB drive for DATA storage
1 x 250GB Samsung EVO which has win10 on and I want Ubuntu Studio on the SSD too, I know it's possible cos I've done it before with MINT on my dads PC and its the SAME PC as have it now...
ill have to print off instructions and follow them
its 4Ghz Quad-Core 32nm SandyBrdge with 1GB 256-Bit GTX460 and 12GB of 1600Mhz RAM - so think it is powerful enough for ANY linux distro

---

### Post by Impavidus on 2021-02-24
Quite a powerful computer, for one that's 12 years old. I guess it has seen some upgrades?

In Windows, create enough unallocated space on the drive where you want to install Ubuntu. Disable FastStartup (a setting that uses hibernation to make Windows appear boot faster, but grub can't boot Windows in that state) and make sure you've got a Windows repair drive (you may need one if Windows decides to enable FastStartup).

In the Ubuntu live session, create the Linux partitions you want. Run the installer, choose "something else". Select your partitions and give each its mountpoint. If not available from the dropdown list, just leave it. it can be fixed later.

Normally on dual boot systems in bios style with multiple hard drives, you keep the Windows bootloader on one and put the Linux bootloader on a different drive. I think you can put grub on a different drive from the one where you put the root partition. You'd have to set boot priority to that drive. It's a bit unusual though, and there may be some caveats in it.

I can't be more specific.

---

### Post by 1byte on 2021-02-25
> **Impavidus said:**
> Quite a powerful computer, for one that's 12 years old. I guess it has seen some upgrades?

In Windows, create enough unallocated space on the drive where you want to install Ubuntu. Disable FastStartup (a setting that uses hibernation to make Windows appear boot faster, but grub can't boot Windows in that state) and make sure you've got a Windows repair drive (you may need one if Windows decides to enable FastStartup).

In the Ubuntu live session, create the Linux partitions you want. Run the installer, choose "something else". Select your partitions and give each its mountpoint. If not available from the dropdown list, just leave it. it can be fixed later.

Normally on dual boot systems in bios style with multiple hard drives, you keep the Windows bootloader on one and put the Linux bootloader on a different drive. I think you can put grub on a different drive from the one where you put the root partition. You'd have to set boot priority to that drive. It's a bit unusual though, and there may be some caveats in it.

I can't be more specific.

no probs n thanks for your help, ill print off ur previous instructions n create the 2 ext4 partitions first on Minitool, a 50GB one fo OS, 4Gb one swap-file (if that's the best way)
thanks again

I'll report back when done

PS: good guess on age of PC, exactly 12 years old hehe - Sandybridge gave it away lol, till on same SSD, only the 2 x 2TB drives added since i built it for my dad whos now give it to me as mine broke (he was FSX player so machine had to be decent at the time sandybridge was the king of the hill)

---

### Post by 1byte on 2021-02-25
also yeah i have the documents etc stored on another hard-drive (Pics,docs,music,vids) so that they can be accessed by any OS on the SSD

---

### Post by Impavidus on 2021-02-25
Just make sure you install Ubuntu on the right drive and don't overwrite your documents. But keep backups nonetheless. As long as Windows FastStartup is off, you can access your files on NTFS partitions from both operating systems.

---


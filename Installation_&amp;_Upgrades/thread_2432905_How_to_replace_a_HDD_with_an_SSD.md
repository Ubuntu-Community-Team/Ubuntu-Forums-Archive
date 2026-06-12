---
title: "How to replace a HDD with an SSD"
date: 2019-12-10
forum: Installation &amp; Upgrades
---

### Post by robertcull1 on 2019-12-10
I am not using a UEFI based computer. The SSD has less space on it than the HDD.

I am using a dual-boot system that starts up letting me select the operating system with GRUB 2. The system originally had a copy of Windows 7 running on it. I installed a copy of Ubuntu 18.04 LTS alongside the Windows OS using an Ubuntu installation flash drive.

I want to create a new bootable duel boot SSD from the HDD. I wish to use dd and Gparted from a bootable Ubuntu installation flash drive to create the bootable SSD.

My partitions look like this from Gparted:

[IMG]https://live.staticflickr.com/65535/49201581782_ee90d1c568_z.jpg[/IMG]

I have never done anything like this before, but after a little research online this seems like the best approach:

1. Copy the Windows partitions onto the SSD. Use a recovery disk to repair the MBR so that it boots to Windows 7.

From the HDD I will need to copy the MBR (/dev/sda1), the Windows OS partition (/dev/sda2) and the Windows 7 recovery image (/dev/sda3). I am assuming that when I repair the MBR with the recovery disk it will also tell the Windows OS where to find the Windows 7 recovery image (/dev/sda3) should I ever need it.

Now if I am to copy these partitions to the SSD, I need to make one NTFS partition exactly as big as the MBR on the SSD. I also will need to make an NTFS partition on the far right end of the SSD exactly as big as the recovery image partition (/dev/sda3) on the HDD. Then in the remaining space on the SSD I will make another NTFS partition as big as or greater than the Windows 7 OS partition (/dev/sda2).

I am assuming that you can choose whatever size you want to make a partition when you are making it with Gparted.

What I don't know is how can I find out the exact size of the MBR (/dev/sda1) and the recovery image partition (/dev/sda3) using the Ubuntu tools available?

I have another question regarding partitioning and formatting the SSD with Gparted. When you ask Gparted to make a partition table, it prompts you to choose an MSDOS partition table. That's what I want, right?

2. After I get the Windows 7 installation working, I then plan to install Ubuntu from the bootable Ubuntu installation media. This will also install GRUB2 into the MBR.

3. Then I will use Gparted from the Ubuntu installation media to shrink the Ubuntu partition (/dev/sda4) on the HDD so that it will fit onto the Ubuntu partition on the SSD.

4. Then I will use Gparted to overwrite the Ubuntu partition on the SSD with the Ubuntu partition (/dev/sda4) from the HDD. After doing so I should be able to boot either operating system from the GRUB2 boot menu.

---

### Post by oldfred on 2019-12-10
Generally you do not backup MBR. You can easily reinstall either Windows boot loader or Ubuntu's grub boot loader. Grub also has more boot data in the sectors just after the MBR.

Usually dd is not the best tool as it also copies unallocated space and is really for same size to same size drives. 

Windows with MBR has to have a primary NTFS partition with the boot flag to either boot from, repair or install into. With Windows 7 & later, it typically has a small boot partition with boot flag and then the large c: "drive" partition.
Note that Windows 7 expires Jan 2020, so is it really worth all the effort?

After you reinstall Ubuntu, I would use cp -a or rsync with several parameters to copy your /home data. I suggest yourestore from your normal backup as that then is a good test that your backup includes everything. And you then still have your old drive, just in case your backup is not as complete as you expect. Drives fail, sometimes without any warning, so backup is essential.

If this was the newer UEFI/gpt type install, you could not use dd to copy anything but the entire drive as each partition has an unique GUID that must be in partition table & backup partition table. With MBR, you have no backup partition table, so always a good idea to either backup partition table and/or know details by sector of your current partitioning. (I export partition table info, save in /home so my normal backup of /home includes the partitioning info).

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by robertcull1 on 2019-12-11
Thanks, that takes care of everything.

---

### Post by ubfan1 on 2019-12-11
Another thing to pay attention to: Many older hard disks' alignment would not be suitable for SDDs.  Current partitioning tools start on sector 2048, so have proper alignment, but old Windows installs typically started on sector 63. Improper alignment can impact performance.

---


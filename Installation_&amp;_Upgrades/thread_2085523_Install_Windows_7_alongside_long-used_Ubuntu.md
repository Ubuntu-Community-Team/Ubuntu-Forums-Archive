---
title: "Install Windows 7 alongside long-used Ubuntu"
date: 2012-11-18
forum: Installation &amp; Upgrades
---

### Post by Sidrabs on 2012-11-18
Hello,

Ok, here's this weird request, shame on me, I know :)
So, I want to install Windows 7 on my laptop, alongside the Ubuntu 12.04 that is running there right now. For gaming, obviously, cause not all games run via Wine or in VMs.

Since I don't want to screw up my Ubuntu installation (with my documents and all), I'd better do this carefully, if at all. So I need some good advice. Most of the tutorials suggest installing the Windows first, and then proceed with installing Linux, since the Windows installer is jealous and doesn't treat the GRUB politely. In my case, that is not an option - the Ubuntu is taking all the HDD, and the best I can do is shrinking the main partition, allocating new one and installing the Windows there.

So I am looking for advice how to do that properly - do I need to back up GRUB config before installing Windows, how to install Windows without destroying Ubuntu install, and how to fix the bootloader after the Win is installed. Or maybe you'd suggest to abandon the whole idea as totally crazy, I can take that as well.

---

### Post by Mr_JMM on 2012-11-18
Unless someone corrects me, I believe that Windows, whilst you can install it after, has to be on partitions that are at the start of the hard drive. This means you will have to shirink the Linux partitions by adding space BEFORE it (the usual is after). There is small risk that you can lose data so make sure it's all backed up.

Once you've installed windows you'll lose grub so you'll need to boot from a Live DVD and reinstall.

There are more complicated ways to do this if you can't backup your data first.

Sinc you asked how to do this "properly" then my advice would be to back up your data, repartition your drive, install windows to the ntfs or empty space (depending on how you want windows to be installed) THEN install Ubuntu into the partition(s) you created.

Again, there's simple and more complex options to achieve the above.

---

### Post by oldfred on 2012-11-18
It does not have to be first, although most installs are. But it does have to be a primary partition or sda1 thru sda4, formatted NTFS and with the boot flag.

Windows 7 default install is two partitions, one a hidden boot/repair and the main install. Boot partition is primarily to allow you to encrypt main install, but may let you boot repair console if you need chkdsk or other repair in main partition. But it installs to one partition, just make a separate Windows repairCD in case you need it in the future.

If you format with gparted to NTFS, you may have to reformat again with Windows. NTFS partitions have two versions of PBR - partition boot sectors, one XP style and the other Vista/7/8 style. One difference is calling out booting with ntldr or bootmgr.

       [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
    
You need current version liveCD of Ubuntu to reinstall grub2's boot loader.

       [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

---

### Post by Sidrabs on 2012-11-19
Oh, boy.

Since the wise approach involves full backup, there's little point in breaking my neck trying to set it all up so that Windows install actually works and nothing else is broken.

Perhaps it is more practical to backup all my data and some of the software (the ones that would be harder to reinstall from software centre), and go on with setting up new partition scheme, format disk, install Windows, install Ubuntu, move back the data and install the applications. Sure thing, reconfiguring the applications back to current state will take some pain, but let's be honest, I've accrued a lot of junk over the years anyway.

---

### Post by oldfred on 2012-11-19
All your settings are in /home, so a good backup & restore of that or a separate /home that you reuse as part of the install will preserve your settings. If you made any system wide settings like grub, Internet or Video they may be in /etc.

You can make a list of installed applications and automatically reinstall.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

    
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

    
My backup plan is just to reinstall. So I try to backup what I think I need to restore with a new clean install.
       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

            Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

            More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

---


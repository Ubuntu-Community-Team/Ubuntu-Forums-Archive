---
title: "Partition Ubuntu Vista"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by ubuntoexpert on 2008-03-12
I have a new laptop computer with a 120-GB hard drive. I have installed Ubuntu and probably corrupted the Vista installation. Right now the Linux CD installation tells me that in Computer, I have an 18.6-GB volume and a file system (that probably was supposed to have been a swap file) is listed as 2.1 GB.

When I begin the installation from the CD and go down to the fourth step "Prepare Partitions" I have:

/dev/sda1 ext3   /   about 20 GB
/dev/sda6 swap  about 2 GB
free space 93 GB
/dev/sda5 swap 8 MB
free space 4910 MB

I have not formatted anything yet in this dialogue.

My goal is to have Windows Vista in a 45-GB partition, Ubuntu on a 20 GB partition with two other partitions utilizing the rest of the hard drive. Earlier, when I was in the Ubuntu installation, I was able to download, but not install EASYBCD.

I do not see Vista on booting into the bios.

I will appreciate advice as to how to get out of this situation.

---

### Post by Twitch6000 on 2008-03-12
Yeah it seems you deleted vista somehow.The best thing you can do is one out of two things.Completey go linux.Or use boot and nuke then reinstall vista.

---

### Post by markjensen on 2008-03-12
What exactly did you do?

Did you use a tool to resize partitions?  Did you manually select and create, or let the installer do the work?

Did you plan on re-installing Vista, or were you just shrinking it to make room?  Does this laptop have an OEM 'recovery partition'?

It looks like something went horribly wrong, as I don't see the installer creating **two** swaps on its own.

Unless the free space is your original NTFS Vista partition, you might be in trouble.   If that is your Vista, you can use **fdisk** to manually re-define that space as "NTFS".  **DO NOT FORMAT it**, or tell it to create the "filesystem".  Just define the partition and write/save the change, and reboot.   Boto into Linux as a LiveCD, if you must and see if you can browse your created NTFS drive and see files?  If you can, you are good to go.  If not, you have likely lost your data.

---

### Post by Pumalite on 2008-03-12
See if you can repair Vista MBR with Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
If not, I'm afraid you'll have to start from scratch; this time partition within Vista with Vista partitioner before installation of Ubuntu:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by markjensen on 2008-03-12
Please, before you start from scratch and potentially lose your data, try re-assigning the large "empty" space as NTFS, and see if your filesystem "magically" reappears with all the data.

---

### Post by Pumalite on 2008-03-12
Super Grub is capable of booting your Windows if there is a Windows left.

---

### Post by markjensen on 2008-03-12
> **Pumalite said:**
> Super Grub is capable of booting your Windows if there is a Windows left.

That's all good and well.  But look at his partitions!   "ext3", "swap", free space, "swap", and free space.

Windows will _not_ boot from that!  He needs to see if he can salvage an NTFS partition, first!

(or evaluate what data was on the drive and elect to just start over)

---

### Post by Pumalite on 2008-03-12
Boot your Ubuntu Live CD and post:
sudo fdisk -lu

---

### Post by Computer Guru on 2008-03-13
MarkJensen is right, there's a good chance that data isn't gone for good.
fdisk won't be of any use recovering partitions though, he'll need something like testdisk by CGSecurity:  [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) (runs on Linux and/or Windows)

BTW, to the OP: you couldn't run EasyBCD in Ubuntu because it can only be used from Windows. It doesn't run on Linux.

---

### Post by ubuntoexpert on 2008-03-13
> **Pumalite said:**
> See if you can repair Vista MBR with Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
If not, I'm afraid you'll have to start from scratch; this time partition within Vista with Vista partitioner before installation of Ubuntu:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)
This sounds Helpful
Thank u very Much

---

### Post by Pumalite on 2008-03-13
You are welcome. Good luck.
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

### Post by markjensen on 2008-03-13
"start over" is always an option.  I thought you wanted access to your NTFS partition and data...:confused:

---


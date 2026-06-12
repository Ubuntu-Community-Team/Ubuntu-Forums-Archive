---
title: "No volume groups found Grub"
date: 2014-12-24
forum: Installation &amp; Upgrades
---

### Post by linuxsyst on 2014-12-24
So, I was installing ubuntu and i split my partitions on /boot, windows and linux ( / ). But when i finished the installation and turned on the laptop my Windows 7 didnt show up in the grub there was only ubuntu and ubuntu recovery.
the **fdisk -l** output is this:
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005cd85

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400   83  Linux
/dev/sda2          206848   429894347   214843750    7  HPFS/NTFS/exFAT
/dev/sda3       429895680   625141759    97623040   83  Linux


```
What i did is I tried to edit /etc/grub.d/40_custom and added this:
```
echo "Adding Windows" >&2
cat << EOF
menuentry "Windows" {
set root=(hd0,2)
chainloader +1
}
EOF

```
then i ran **update-grub** but I only got (ubuntu) linux and initrd images and **No volume groups found** then i also tried the **grub-mkconfig -o /boot/grub/grub.cfg** command but the output is same.

---

### Post by Mark Phelps on 2014-12-24
Windows on a preinstalled machine typically comes with two partitions already formatted, the first one being small (few hundred MB), being used for the Windows boot loader files, and having the boot flag set; the second one being much larger and being used for the Windows OS and other files.

Windows won't boot unless the partition containing the boot loader has the boot flag set. Linux, on the other hand, doesn't care about the boot flag being set.

Since sda1shows the boot flag set, I have to presume this originally contained your Windows boot loader files -- which you wiped out when you reformatted that partition to a Linux fillesystem.

So, at the very least, you would have to set the boot flag on sda2 in order to have Windows boot from it.  But, if your boot loader files have been overwritten, you would also have to reinstall them in sda2 for Windows to boot.

Need to tell us in detail what you did.

---

### Post by schragge on 2014-12-24
Just to be on the safe side, try this:
```

echo "Adding Windows" >&2
cat << EOF
menuentry "Windows" {
[COLOR=red]insmod ntfs[/COLOR]
set root=[COLOR=red]'[/COLOR](hd0,2)[COLOR=red]'[/COLOR]
chainloader +1
}
EOF

```

---

### Post by linuxsyst on 2014-12-24
**schragge**, just tried it, returns the same.
[ 						 							]("http://ubuntuforums.org/member.php?u=311399")**Mark Phelps, **I guess I reformatted the windows boot loader partition to a linux file system as you said. it's an ext2 partition with a boot flag and it's mounted to /boot but it doesn't have the windows boot loader. So if I understand you the windows won't boot without the boot loader? So I should make a new partition with the windows bootloader and than add that partition to grub?

---

### Post by yancek on 2014-12-24
As explained above, windows 7 particularly a pre-installed version, will have a separate boot partition and you should not make any changes to it.  To repair this you will probably need a windows installation DVD and select the Repair option when you boot it.  You might be able to find a repair CD if you don't have the installation medium, I don't know as I don't use windows.  You have probably overwritten the windows boot files on sda1, can't tell from the information posted.  Linux systems do not use the "bootable"/"active" marker and don't need it but windows does.  If you can't make any progress with this, you might go to the site below and download and run the boot repair script at the link below.  Select the option to create a bootinfo summary.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by linuxsyst on 2014-12-24
Alright thanks, I have 1 more question I guess the win7 repair disk will make the bootloader partition, but then I will have to boot linux and there update the grub?

---

### Post by schragge on 2014-12-24
With Windows 7 Installation or System Repair Disc you will be able to put Windows bootloader directly into Win7 partition. A separate boot partition may be the default layout, but it is not required to boot Windows. But you'll need to mark the Windows partition as active (i.e. set the bootable flag), e.g. with
```
sudo sfdisk --activate=2 /dev/sda
```

---

### Post by oldfred on 2014-12-26
Running the default Windows fixes will install bootmgr and BCD files into your main install if you have boot flag on the main install.
But that also will install the Windows boot loader to the MBR. Best to confirm Windows does boot ok, and then you have to reinstall grub to MBR to boot Ubuntu. And since you created a separate /boot partition that is a bit small, you need to mount it also when reinstalling grub and must regularly house clean old kernels as you do not have much room. Generally better with most Desktop installs not to use the /boot partition anyway.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---


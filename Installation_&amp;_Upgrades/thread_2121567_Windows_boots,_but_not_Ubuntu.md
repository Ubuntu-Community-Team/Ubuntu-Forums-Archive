---
title: "Windows boots, but not Ubuntu"
date: 2013-03-02
forum: Installation &amp; Upgrades
---

### Post by sasparilla on 2013-03-02
Hi,

For Explanation:
I have 2 Drives in my System: 1x SSD and 1x HDD.

The complete SSD is used as my Windows 7 Partion. The HDD contains all of my data.

I want to test Ubuntu (64 bit) so i splittet my HDD and created a small partiton for Ubuntu.
I chose in the Ubuntu installation ext 4 journaled and "/" 
Also i chose to install the Bootmanager on the HDD.

After the installation is completed and i select my Harddrive in the UEFI, Windows 7 starts as usual, but no Ubuntu!

What is wrong here? Please help!
I tried to install it on an USB-Stick too, same Result! Its simply not bootable.

Thank you!

---

### Post by oldfred on 2013-03-02
Is Windows installed in UEFI mode? Then did you install Ubuntu in same mode? Both have to be either UEFI or BIOS/Legacy/CSM or whatever your system calls it.

You can convert a BIOS install of Ubuntu to UEFI, but drive must be gpt not MBR. Ubuntu works from gpt drives with either BIOS or UEFI.
Windows only boots from gpt with UEFI. Or from UEFI only boots with gpt partitioning.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[URL="https://help.ubuntu.com/community/UbuntuSecureRemix"]https://help.ubuntu.com/community/UbuntuSecureRemix

[/URL]

---

### Post by sasparilla on 2013-03-02
My Mobo is An ASUS Z77 Board with UEFI.

I installed Windows the usual way.

How to install Ubuntu on my second Partition of my HDD and boot from the UEFI from it? Is it even possible?

---

### Post by darkod on 2013-03-02
You have to install ubuntu in uefi mode too if windows is in uefi. When you boot the usb stick boot the uefi device not the legacy. There will be two devices on uefi boards. You have to boot the uefi one.

---

### Post by sasparilla on 2013-03-02
thanks for your reply, can u tell me exactly how to install Ubuntu 12.10 in UEFI-Mode?

and what has Windows to do with it anyway, since it is on a totally different Drive?

Tank you very much!

---

### Post by oldfred on 2013-03-02
When you say you installed Windows in usual way that could mean either BIOS/MBR or UEFI/gpt. How you boot install media for both Windows & Ubuntu is how it installs. From UEFI menu you should get two boot choices from installer.

When you boot, UEFI/BIOS system writes data to drive for operating system to use. UEFI writes data somewhat differently than BIOS so you cannot dual boot from one to the other if not same mode. You can dual boot if one is BIOS and the other UEFI only if you go into UEFI and change from or to the correct mode you installed operating system in.

May be best to post this.

sudo parted -l

---

### Post by sasparilla on 2013-03-02
Once again, what does it matter if my SSD wich contains Windows 7 ist MBR or GUID? Its MBR by the way. 

What are those "modes" you talking about? Or do you mean just the MBR vs GPT ?

I want to install Ubuntu on a partition of another physical Drive and boot from it via the UEFI of my Mainboard by selecting it there.

---

### Post by darkod on 2013-03-02
The MBR or GPT matters if you are not sure in what mode it's installed because win7 can work on gpt only in uefi mode, and it can work on mbr (msdos table) only in legacy mode. So, if the SSD has msdos table, you have win7 in legacy mode.

To avoid any further confusion, go into BIOS and disable the uefi boot. Set the setting to Legacy Only or what ever it is called in your bios.

With the new uefi boot process it matters how you install each OS even when they are on separate disks. This is because the boot mode is general, it's either legacy or uefi. So, both OSs have to be installed in the same mode, what ever your boot mode is.

If you are not getting grub2 menu when booting from the hdd, it might be that grub2 didn't install correctly on the mbr. It happens sometimes. Boot the ubuntu cd/usb in live mode and post the output of:
```
sudo fdisk -l (small L)
```

That will show us your ubuntu root partition so we can give you commands to install grub2 to the mbr.

---

### Post by darkod on 2013-03-02
As for the different boot modes and how you boot install media, now that you have uefi board get used to it. :)

On uefi enabled boards the optical and usb boot devices will have two versions, two separate devices. One will be the older legacy mode, the other the UEFI mode which should have the UEFI prefix or similar.

So, when we say boot the stick in uefi mode, it means to select the UEFI stick and not the standard legacy stick. How you boot it, that is how it will install.

If you look in the list of boot devices, I'm sure you will see some with UEFI prefix, if you haven't disabled uefi boot yet. For sepecting a device to boot from to install, it's best to use the board boot menu, usually accessible with F12 or similar. This is because you boot your stick only once to install, no point going into bios making changes for one boot. If the board has boot menu, use it.

---

### Post by sasparilla on 2013-03-02
ive now selected boot legacy only in my Bios /UEFI.

I install it now again and will post you my [LEFT][COLOR=#000000][FONT=Ubuntu Mono]sudo fdisk -l
[/FONT][/COLOR][/LEFT]
Where to put the grub2 bootloader? directly on the partition of my HDD where i put my Ubuntu-install?

Thanks !! :-)

---

### Post by darkod on 2013-03-02
No, if you did that last time, that is because it's not booting. You didn't need to reinstall all of it, probably only grub2 needed installing on the mbr. That is done easily with two commands from live mode.

Anyway, the grub2 bootloader goes to a MBR of a disk. In this case it would be the MBR of the hdd. NOT the ubuntu partition. The boot process starts on the MBR so the bootloader needs to be there.

Also, you will need to tell bios to boot from that hdd first, not the ssd.

---

### Post by oldfred on 2013-03-02
You have to install the grub2 boot loader to the MBR of the hard drive you install Ubuntu into, not any partitions. Computers only boot from MBR in BIOS mode. UEFI only boots from efi partition. So no systems boot from a partition unless you have another boot loader that has the capability to chain load.

---

### Post by sasparilla on 2013-03-02
alright that makes sense... 


here my sudo fdisk

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8bc7817c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   250066943   124930048    7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  1953525167   976762583+  ee  GPT
ubuntu@ubuntu:~$

---

### Post by sasparilla on 2013-03-02
can you tell me those 2 commands please to install the bootloader on the MBR of mz HDD 

i already installed it on the ubuntu partition...

---

### Post by sasparilla on 2013-03-02
> **darkod said:**
> No, if you did that last time, that is because  it's not booting. You didn't need to reinstall all of it, probably only  grub2 needed installing on the mbr. That is done easily with two  commands from live mode.

Anyway, the grub2 bootloader goes to a MBR of a disk. In this case it  would be the MBR of the hdd. NOT the ubuntu partition. The boot process  starts on the MBR so the bootloader needs to be there.

Also, you will need to tell bios to boot from that hdd first, not the ssd.



can you tell me those 2 commands please to install the bootloader on the MBR of mz HDD 

i already installed it on the ubuntu partition...

---

### Post by darkod on 2013-03-02
Hold on, that message about gpt table on sdb is important. Please post the result of:
```
sudo parted /dev/sdb print
```

---

### Post by sasparilla on 2013-03-02
awesome, i installed it with grub2 on the mpr an now it works! Thanks!!!!



test@test-System-Product-Name:~$ sudo parted /dev/sdb print
[sudo] password for test: 
Model: ATA SAMSUNG HN-M101M (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  994GB   994GB   ntfs         Basic data partition
 2      994GB   1000GB  6291MB  ext3

test@test-System-Product-Name:~$

---

### Post by darkod on 2013-03-02
You have a 994GB ntfs partition on that disk, do you want to keep it? Do you have important data there?

---

### Post by sasparilla on 2013-03-02
exactly! is that a problem? i installed ubuntu only for test purpose on a 6gb Partition on that HDD, if i like it i will buy a second ssd anyways

---

### Post by oldfred on 2013-03-02
To get grub to install correctly on gpt drives you also need a tiny 1MB unformatted bios_grub partition. You can have that anywhere on drive and with gparted right click to add flags and add the bios_grub flag.

You only have 6GB for Ubuntu. I normally suggest 10 to 25GB for / (root) with the larger size for larger drives since you should have space.  With 6GB you will not be able to install a lot and will have to be careful to manage space with regular housecleaning.

---

### Post by darkod on 2013-03-02
Hmm, you left too little space for ubuntu, only 6GB. In theory it could install on 6GB, but it won't have much space. Plus it will not have a space for a swap partition.

Another issue is that on gpt disks ubuntu needs a small bios_grub partition so that grub2 can install properly.

If you still want to try it post the output of:
```
sudo parted /dev/sdb unit MiB print
```

and I can give you more specific commands how to do the bios_grub partition.

---

### Post by sasparilla on 2013-03-02
am i right that mz HDD hast GPT Format and not MBR?

---

### Post by darkod on 2013-03-02
Yes, it has gpt table. You can see it clearly in the parted output.

---

### Post by sasparilla on 2013-03-02
Does GPT actually have any advantage against MBR?

---

### Post by darkod on 2013-03-02
I would say not much, but haven't looked into the details.

It has more importance with windows, as mentioned. If you want UEFI, it has to be on gpt. Ubuntu can work on either combination but windows can't.

But now that it's gpt, you can't convert to msdos without losing the data. So you would need to move the data, make a new blank msdos table, make the needed partitions, and then move the data back.

One benefit of gpt is that all partitions are like primary, you don't need to think about primary/logical partitions any more, you simply create them. It has no limit of 4 primary partitions. But usually you don't need so many partitions on your system for this to be an issue. With good planning msdos tables are sufficient too.

---

### Post by oldfred on 2013-03-02
You have to use gpt if drive is over 2TB and it is suggested for SSDs. You do not have logical partitions as the new limit is 128 partitions which all are one type or essentially primary. And it has a backup partition table to help avoid some partition issues.

 GPT Advantages (older but still valid)  srs5694 post #@:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

### Post by sasparilla on 2013-03-03
Thanks for your help, apreciate it!

I have one more question? Do i need a Swap Partiton? What is it exactly for and how do i make one correctly?

---

### Post by Akhj on 2013-03-03
Yes, you need a swap partition because it is as same as Page file in Windows.

---

### Post by darkod on 2013-03-03
In theory it can work without it, but it's usually better to have one. Although since you left only 6GB on the disk I don't see how you can make a swap partition too. You barely have space for the root partition.

The swap is used if all the memory gets used up. When you create it manually, you select the size you want and in the Use As field select 'swap area'. The swap has no mount point, it is used automatically. If you use the auto methods to install it will create a swap according to the unallocated space it has available.

---

### Post by sasparilla on 2013-03-03
Thanks you helping me alot! I installed already the AMD Graphicsdriver and the System runs super smooth now :-)

I tried to install a second Driver for my TV-Card and failed. Could you explan the following Guide for me? (iam super-ubuntu-noob)
I even cant get started with the first command, how do i enter it in terminal? with the # ?


Heres the Manufactures Manual for installing the Driver:

Driver tested for Linux kernel 2.6.31 to 3.6.x
Make sure you're &#8222;root&#8220; user!

1.
Copy &#8222;tt_s2_4100_drv_lnx.tar&#8220; into root directory - for example, flash drive:

# cp /mnt/tt_s2_4100_drv_lnx.tar.bz2 /root

2.
Change into root directory, extract, build and install the driver (for example 64-bit
Linux kernel 3.x).

# tar xjvf tt_s2_4100_drv_lnx.tar.bz2
# cd tt_s2_4100_drv_lnx
# ./tt_install_lnx3x_x64.sh
# make
# make install
# shutdown -r now

Examples for other kernel versions:

&#8222;tt_install_lnx3x_x86.sh&#8220; : 32-bit (x86) Linux kernel version 3.x
&#8222;tt_install_lnx26_x64.sh&#8220; : 64-bit (x86_64) Linux kernel version 2.6.x
&#8222;tt_install_lnx26_x86.sh&#8220; : 32-bit (x86) Linux kernel version 2.6.x

3.

When all steps are sucessfully and there isn&#8216;t any error, you could run:
# dmesg | grep frontend

---

### Post by darkod on 2013-03-03
No, the # means the command prompt but as root user. It also mentiones to make sure you are the root user. In ubuntu that means using sudo in front of every command but instead of typing it in front of every command you can first do:
sudo -i

Enter your user password when it asks you, and after that you will see the prompt change from username@ to root@. Any command you run will be run as root. So, start entering the commands one by one ignoring the #. To exit the root prompt you simply use 'exit'.

---

### Post by sasparilla on 2013-03-03
but how does terminal know where i put the driver?

---

### Post by darkod on 2013-03-03
Well, it doesn't. You need to know that. :)

Where ever you put the downloaded file, you open terminal, go into that folder and execute the commands there. For example, to make it simple, when you download the file it would usually go to your Downloads folder. Open the folder and move the file to your Home folder.

When you open terminal it opens by default in your home folder, so the file is already there, and you can start executing the commands after you switch to root. If switching to root changes you to the root home folder, go back to yours with:
cd /home/username

The cd command is used to change the current folder where you are. You can list folder contents with:
ls

That can help you checking which files are in that folder and whether the file you expect to be there is really there.

---

### Post by sasparilla on 2013-03-03
sorry for my maybe stupid question, but how would the first command be right if the Driver File would be on my Desktop for example.

In the Manual they have an USB-Stick.

Thanks!!

---

### Post by darkod on 2013-03-03
If the file is on the desktop, first you do the sudo -i to become root and after that you change the folder to:
cd /home/username/Desktop

Of course, change 'username' with your username. And Desktop needs to have the first letter in capital, linux makes difference between capitals and smallcase when typing folder names, unlike windows.

---

### Post by sasparilla on 2013-03-03
it doesnt work... Terminal says that it doesnt find File or directory

---

### Post by darkod on 2013-03-03
Then it's not there. Did you check the content with ls first. ls is short for list and as I said it will show you all folder content. Double check if the file is there. It's not that difficult to navigate with ls and cd, you only have to get used to it. I'm old enough to remember when we had to do that in DOS, there were no fancy GUI windows then. :)

When you want to go one level up with cd, the command is:
cd ..

Otherwise, to go into a folder you use:
cd <folder name>

---


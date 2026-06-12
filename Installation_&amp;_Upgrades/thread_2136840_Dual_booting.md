---
title: "Dual booting"
date: 2013-04-18
forum: Installation &amp; Upgrades
---

### Post by Tesseract007 on 2013-04-18
Can I Dual boot like say Ubuntu and Linux Mint? I know I can dual boot Windows and linux.

---

### Post by oldfred on 2013-04-18
Sure, just install to different / (root) partitions. Best not to share a /home. You can use same swap unless you hibernate which is not recommended it dual booting. You may want data partition(s) for data you may want to easily access from multiple installs.

You can install in 10 to 25GB depending on how much you plan to use them. 

Grub2's os-prober now makes it easier as it finds most other installs and automatically adds other installs to menu. Best to plan a bit as last install will put its boot loader into the MBR and be the main booting partition, although it is not really difficult to change.
Ubuntu does not really offer a choice not to install grub so you can use grub from another install.

Also best to use Something Else or manual install to make sure you choose correct partitions and sizes.

---

### Post by Tesseract007 on 2013-04-18
Ok im a newbie. I've looked for grub on my computer but I cant find it. How do I go about setting up a dual boot config?

---

### Post by oldfred on 2013-04-19
Grub2 is just the boot loader. But it does have parts in several places on your system. It actually is handled automatically with your install.

If you are already dual booting post a link to the BootInfo report.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

Use Windows disk tools to resize Windows and reboot so it can run chkdsk. Do not create partitions with Windows.
But use gparted to create partitions for Linux.


 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

---

### Post by fantab on 2013-04-19
> **Tesseract007 said:**
> [SIZE=4]Ok [SIZE=4]im a [SIZE=4]newbie. I've looked for grub on my computer but I cant find it. How do I go ab[SIZE=4]out setting up a dual boot config[SIZE=4]?[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

Grub is a Boot-Loader and not your regular application. So you will not find it your application menu.

Let us assume that you are already dual booting Windows and Ubuntu. Now you want to install Linux Mint. 

1. You will create a partition of about 15-25 GB. You can use Gparted to do so.
2. Then you will boot your computer with Linux Mint install CD/USB.
3. When you are asked how you want to install Linux Mint you will choose manual method or "SOMETHING ELSE" option.
4. You will direct the install to the created 15-20 GB partition, format it as ext4 and use '/' as mountpoint.
5. You will then choose the location to install Grub, Boot-loader. Since you already have Grub from previous Ubuntu install, you don't need it actually. However since Linux Mint is based on Ubuntu you may NOT get the option to NOT install it. So you will either replace Ubuntu's Grub by installing it on /dev/sda (assuming you have only one HDD) or you will install it on /dev/sda3 (where /sda3 is the partition on which you will install Linux Mint). 

The later method will not replace Ubuntu's Grub. However, if you do take the later route then, after installing Linux mint you will have to boot into Ubuntu and UPDATE GRUB, so that Linux Mint shows up. You don't need this step if you replace Ubuntu-Grub with that of Mint's. 

Now the catch: Suppose you've installed Grub from Mint replacing Grub from Ubuntu and later you've decided that you don't want Mint and remove it. Then you have to REPAIR your Ubuntu-Grub to be able to boot your computer again. But if you want to remove Ubuntu, after installing Grub from Mint. Then you have to worry about nothing.
This is reason why it is  recommended that your main Linux OS should control the Grub, yet this is not set in stone. Other Distros however, do give you an option to NOT install Grub. So after installing 'Other Distro' and NOT installing Grub you will boot into Ubuntu and UPDATE GRUB.

I hope I've been clear.

EDIT: If you will install MINT for Cinnamon-desktop then allow me to inform you that you can install Cinnamon in Ubuntu and without any issues or complications.

---


---
title: "Installing Ubuntu 14.04 alongside Windows 8 - win8 not recognized"
date: 2014-06-14
forum: Installation &amp; Upgrades
---

### Post by carusoswi on 2014-06-14
I have this problem which I see many have, and I have read, read, read, but am confused by what seems like confusing information.
I read where I can zap the GPT data structures, and I worked through a detailed step by step process which promises to allow me to install alongside win8 with secure boot and EFI both enabled.

The laptop is my son's and I messed it up once, don't want to repeat that for him.

I apologize if the answer resides on the forum already, but four hours of searching only leaves me confused.

Could someone advise?

Should I go ahead and run the Ubuntu installation using "something else"?

I'm thinking if I do that, it will result in a system that will only boot to Ubuntu.

Thanks in advance for any replies.

Caruso

---

### Post by thomaz_ebihara on 2014-06-14
Did you create a partition for Ubuntu in Windows? If not, see "step 1" in my guide on how to do that: [http://thomaz.org/ubuntu-windows-8-install-troubleshooting.php](http://thomaz.org/ubuntu-windows-8-install-troubleshooting.php)

---

### Post by carusoswi on 2014-06-14
Did that, thanks.

---

### Post by carusoswi on 2014-06-14
In fact, we have a separate, empty physical drive onto which we plan to install Ubuntu.

While we would prefer to preserve Windows (my son because he is not 100% certain he has backed up every bit of data that he wishes to save, me because I would like to solve the problem), we have reached that point where we are ready to sacrifice the Windows OS in favor of Ubuntu.

Caruso

---

### Post by oldfred on 2014-06-14
Best just to disconnect Windows hard drive. Then do a UEFI install to your second drive. How you boot installer either UEFI or BIOS is how it will install.

You want gpt partitioning for UEFI boot and an efi partition so Ubuntu drive can boot from its own drive without having to have a working Windows drive.

Basic UEFI info:
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Something else which is required if you do not disconnect Windows drive or want anything other than the default of just / (root) and swap.

 Install to external drive. Also any second drive.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

Many more links in the link in my signature.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---


---
title: "Trouble Installing Ubuntu 14.04 to an external hard drive Toshiba C55-A5300"
date: 2014-07-30
forum: Installation &amp; Upgrades
---

### Post by ian58 on 2014-07-30
Can someone please lend a hand? I am using a Toshiba C55-A5300 Laptop and I am trying to install Ubuntu 14.04 to my external 2 TB Seagate FA Go Flex Desk. I am using the 14.04 desktop .iso on dvd as a live disc and i currently have my partitions set as mostly ext4 mounted to / and a swap folder.....i really am a complete noob here and can't seem to figure this out. Does anyone have any suggestions as far as partitioning and general installation or can you link me to an answer that is already available because i cannot find anything here!

---

### Post by sudodus on 2014-07-30
Welcome to the Ubuntu Forums :-)

It was the right thing to start an own thread.

I have a slightly similar Toshiba, and I can run Ubuntu both in BIOS and UEFI mode.

Please read carefully the advice and links by oldfred in the other thread [Ubuntu on an external HDD]("http://ubuntuforums.org/showthread.php?t=2235588") and consider what is different in your case.

1. [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

See also the second post in that link, which is about UEFI.

2. If you have problems, it can also be because of the boot media. Today I think it is easier to succeed in making a USB boot drive (pendrive) and booting from it. Then you can install your Ubuntu system into the external hard drive (like it were an internal drive). See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

3. What about that external hard disk drive: Is it new and empty, or are there lots of files, that you want to keep there?

---

### Post by oldfred on 2014-07-30
Is your C55 a newer system with UEFI or a BIOS boot system? How you boot installer UEFI or BIOS is how it installs and you want Ubuntu in the same boot mode as Windows.

If only having Ubuntu on external drive you can use gpt partitioning which is compatible with UEFI. But Ubuntu will also boot in BIOS mode from gpt partitioned drives. XP did not work with gpt drives but that should not be an issue.

Some external drives have built in encryption or other proprietary configurations that as configured only work with Windows. Is your standard or can you totally erase it to make it standard? Vendor of hard drive should have info on that if needed.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

    
If UEFI you still want grub2's boot loader on external drive and need efi partition and install of grub to external. And you can only do that with the Something Else install.

 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

      
 Install to external drive. Also any second drive. Or any install with Something Else
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

While this was for a flash drive, the instructions really apply to any external drive.
 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---


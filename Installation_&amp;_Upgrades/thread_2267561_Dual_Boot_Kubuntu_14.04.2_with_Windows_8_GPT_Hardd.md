---
title: "Dual Boot Kubuntu 14.04.2 with Windows 8 GPT Harddrive and UEFI"
date: 2015-03-02
forum: Installation &amp; Upgrades
---

### Post by mike_4 on 2015-03-02
Hi everybody,

I have a Dell Inspiron Ultrabook 14z, windows 8.1 with UEFI and with a 500GB GPT HDD and a 8GB GPT SDD, I can delete the SSD when its necessary for the installation. 
Here are 2 screenshots with more details of my hard drives: 
[http://s17.postimg.org/g7qh536i7/partition_screenshot.png](http://s17.postimg.org/g7qh536i7/partition_screenshot.png)
[http://s15.postimg.org/6q18vec9n/partition_screenshot2.png](http://s15.postimg.org/6q18vec9n/partition_screenshot2.png) (DiskPart windows tool ->detail disk)

I wanted to install Kubuntu-14.04.2 as Dual Boot with a usb, I allocated space on my partition, turned fast and secure boot off. I used microsoft rufus tool to boot the ISO of Kubuntu with the usb and I selected "GPT Partition Scheme for UEFFI Computers".
 
For the installation I booted with UEFI and Legancy but both didn't worked. ( Picture of boot options: [http://postimg.org/image/5bvvocpsj/](http://postimg.org/image/5bvvocpsj/) )
Then in the "disk installation" it just shows a part of my hard drive and lesser space that I have free ( picture: [http://postimg.org/image/kj79uys9f/](http://postimg.org/image/kj79uys9f/)  ). When I try to add a partition to the free space I get the error message:"Uanble to satisfy all constraints on the partition".

When I try ubuntu via usb it shows my drives on the desktop but I can't open them.   

I've been sitting already 5 days trying to install it, I read so many forums. I also tried to install it on a virtual drive disc on my hard disk. 
I hope someone can help me.
Many thanks in advance.

Mike

---

### Post by oldfred on 2015-03-02
Your SSD is probably Intel SRT that is seen as RAID and is just cache location for Windows fast boot.

Users have posted with SRT, they now just have to turn off SRT and change to AHCI for drives. Older installs needed RAID meta-data removed from drive, but that should not be required, so links below showing removing RAID meta-data commands can be skipped.
 Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)


Dell XPS13 - New Broadwell, not yet fully supported Feb 2015
 [http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/](http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/)
[http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly](http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly)
Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)
[http://ubuntuforums.org/showthread.php?t=2204287](http://ubuntuforums.org/showthread.php?t=2204287)

---

### Post by mike_4 on 2015-03-06
Thank you very much oldfred. :) 
Yes, my ssd is a intel SRT, but it was to risky for me to change it in the bios to AHCI.  
I just unistalled Intel Rapid Start Technology in Windows 8 and I formated 8gb (which i only see) of my 32gb ssd to MBR. Then everything worked I could install Kubuntu on my GPT Hard Drive and use dual boot with windows 8. In Bios it still shows me SRT. 
Now I just don't know if I can use the rest of my ssd as a simple volume and how I can do this because in windows it only shows that my ssd is 8gb big and in BIOS 32gb.

---

### Post by oldfred on 2015-03-06
With gpt it has a protective MBR(msdos) to show the old partition table. That is just to prevent older MBR tools from formatting a gpt partitioned drive.

The size of the SRT seems to be the size of RAM. Rest of SSD is then unused.
Some that are primarily Ubuntu users totally turn off SRT and just use SSD a / (root).

If SSD is a lot larger, you can install Ubuntu into the remaining space. 
My normal recommendation for / is 25GB but 20 is also plenty. I use about 11GB of / but have all data in data partitions.

---


---
title: "Surface Pro 3 SSD 256 GB Dual boot with windows 8.1 Issues"
date: 2014-12-10
forum: Installation &amp; Upgrades
---

### Post by shane34 on 2014-12-10
I finally decided to download Ubuntu and plan to install Backbox as I've been unsuccessful at being able to dual boot, much less install Kali Linux for the past two weeks.  I don't feel like I know enough about switching from UEFI to Legacy, much less hear half these terms before I started this journey.  So I began installing Ubuntu and of course after I partitioned my drive, I read somewhere that I'm not supposed to partition my SSD (is this true or not?). Now that I have already partitioned my drive from some of the download tutorials for Kali Linux, I figured I could just load Ubuntu on the partition that I had already created(Let me know if this is something I can not do).  I'm able to pull up the installation prompts and am now on the "installation type" prompt. Before I do anything else I wanted to check with you all, as you seem like a nice bunch, before I choose the wrong choices, as I apparently have no idea what I'm doing. 

I'll Try to take you step by step with what I did to begin with Kali Linux:

1) Partitioned my C drive with 60gb, and gave my new drive the path of E:.
2) that is about as far as I got with Kali linux as when I would reboot from usb I would never get any prompts to do anything different than Windows.

So now on to Ubuntu
1) I downloaded Ubuntu, created the image with Zip7 onto my USB.
2) Charm>settings>Change PC Settings>Update and Recovery>Recovery>Advanced startup (restarts)
3) So my computer restarts, and a prompt for choosing how to boot such as "Use a device"> USB Drive and my computer restarts
4) GNU Grub pops up with the option to install Ubuntu so I click that and ubuntu initiates the installation.
5) Next Option is Wireless which I can't setup as my keyboard for my SP3 will not work with Ubuntu.  I've read the issues about the USB, but the keyboard for the SP3 isn't technically a USB device??? So I ignore that and go onto the next prompt
6)Select install this 3rd party software
7)Click something else/Install from USB yadda, yadda, yadda...
8) Installation menu pops up and I'm at this page which is where I want to make sure I'm doing this correctly, as I have 10 choices to choose from.
9) I'm assuming the /dev/sda5 is the correct drive I'm wanting to install Ubuntu on, as the size of the drive is the only one that is similar to the partition I created.
10) I select Change.. and a window prompt "Edit partition" pops up and it is telling me from a drop down menu: "Use as:" Swap area, EFI boot partition, etc...

This is where I'm confused as this is the first time I have done this and I've watched one too many Youtube videos and read one too many forum posts to continue searching.  One person said that I need to do swap area, one person said since I have ssd I don't need to do that... etc... 

Can someone perhaps help point me in the right direction, thanks!!  

P.S. If something doesn't makes sense in this post, point it out so I can explain it some other way.

---

### Post by grahammechanical on 2014-12-10
Here is some more reading:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

when installing Ubuntu using the "Something Else" option we need to select partitions, assign a file system, give a mount point, tick to format the partition or not. We do all this in the dialog that appears after we select a partition and click "Change."

If the partition is for Ubuntu we 

a) select Ext4 as the file system in the "Use As" panel. We could select one of the other offered file systems but Ext4 is the usual file system used with Ubuntu.
b) we give the partition a mount point of /
c) we also tick to format the partition. It is necessary for a new installation but optional if we are over-writing an existing installation of Ubuntu.

If the partition is to be used as swap we

a) select swap as the file system in the "Use As" panel
b) we give the partition a mount point of swap
c) we tick to format the partition

Here is a where the complications start for you. Do you need a swap partition? How much memory does the machine have? I ask because, personally, I would not want to put a swap partition on an SSD. It is something to do with the limited read/write life of SSDs as compared to standard hard disks. I may of course be believing in a myth. I have not researched this.

Further complications for you. Normally it is not necessary to have a boot partition. But you will need an EFI partition. Thankfully you can use the boot partition that is there for Windows 8. This is all something to do with UEFI.

> 
[LIST]
[*=left][FONT=inherit]if you use the manual partitioning ("Something else"), the difference is that you will have to set the /boot/efi mount point to the EFI partition. And if there was not any EFI partition on your HDD, you first will have to create it (see the "[Creating an EFI partition]("https://help.ubuntu.com/community/UEFI#Creating_an_EFI_partition")" paragraph below).[/FONT]
[/LIST]


> 
[LIST]
[*=left]If your disk already contains an EFI partition (eg if your computer had Windows8 preinstalled), it can be used for Ubuntu too. Do not format it. It is strongly recommended to have only 1 EFI partition per disk.
[/LIST]


I am quoting the wiki page on the first link I provided. So, you have to select the existing EFI partition and click change and in the "Use As" panel select EFI Boot partition. But you may have noticed that you do not tick to format the partition. Get that bit wrong and I think you will lose the Windows 8 boot files in the EFI partition. I cannot tell you the mount point but it might be boot/efi. 

Although I have done many installs of Ubuntu on my 2 hard disks I do not have either UEFI or Windows. And I do like to offer advice from personal experience. So, this is as far as I go. If I have got things wrong other will be quick to correct me.

Regards.

P.S. I would be nice if in Windows you could take a screenshot of the SSDs partitioning and post the image here. It may be useful for us to see what you are seeing.

---

### Post by shane34 on 2014-12-11
Here is the picture of my drives. So what you're saying is perhaps I did not need to partition the drive my self, I should just install Ubuntu in the same drive that windows 8.1 is installed? The "existing EFI Partition" would be the same one that Windows 8.1 is installed correct?

[IMG]http://i.imgur.com/kBmr62W.png[/IMG]

Also, should I remove the new partition that I have created?

---


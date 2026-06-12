---
title: "installing 12.04 lts on new toshiba 500 gb drive"
date: 2013-10-07
forum: Installation &amp; Upgrades
---

### Post by Terry_Lembke on 2013-10-07
hi, my name is Terry Lembke . My current system is 10.04 running on a 500 gig drive toshiba usb . My laptop is a 
compaq pressario cq 50 notebook .
2 gig of ram 
intel cpu 575@2.0 ghz 2.0ghz
the lap top has win vista home basic 32 bit os 
I have never installed ubuntu before . I bought a new 500 gig toshiba usb drive to put new ubuntu on so i don't blow other one up 
my questions is how to do it ?

---

### Post by oldfred on 2013-10-07
You are borderline between full Ubuntu and Xubuntu or Lubuntu. It is a single core 64 bit processor and with 2GB of RAM you could run Ubuntu, but depending on video Unity may not run. My older system is dual core and I do not run Unity but gnome-panel with only 1.5GB of RAM.

Your system should be new enough to boot from flash drive.
 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)

You need to use Something Else or manual install as that is the only one that gives the choice on where to install grub2's boot loader and you want it on the external drive which probably will be sdb. All auto install options will install grub to sda as default and do not give any options.


 Install to external drive. Also any second drive.
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
      
 Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
      
 Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

      
 Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by heir4c on 2013-10-07
Edit: I am to late, my writing in English is not so fast I see. :D


The same as a normal install except when you install you need to choose the second HD to install on. 
But first you need a live-dvd or live-usb.
So, create a live-dvd/usb. When you not using a usb than u need a DVD to burn the image on, because the ISO is to big for a CD.
burn the ISO as a 'image' and not as 'data'
When you use a USB you can use the usb-creator. I think it is in 10.04 also (to long ago that release :))
You need a usb of 1GB at least.
Or you use unetbootin: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) or Multisystem: [http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

After creating DVD or USB than you boot up with the DVD or USB. (Maybe you must change the boot order in Bios or use the bootmenu with F12 or F8 (depends from which laptop you have).

More info see here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
When you have more questions about creating the live-dvd/usb or other things you can ask it.

---

### Post by Donut50 on 2013-10-08
if making a bootable disk of ubuntu is too hard for you (no offense) you can buy from cannonical a disk with ubuntu preinstalled on it!
but the lack of performance is not too bad on your laptop i guess, i use ubuntu on a old netbook with an intel atom n450 at 1,4 ghz and a gig of ram and it runs really smooth, so that should not be a problem.
just insert the disk and press f12 when you are at your bios or whatever your boot option key is on your laptop an select the disk.
the following steps should not be hard and you just have to select your language and if you want to install it with another OS or ubuntu only.

hopefully i helped you out a bit :)

---

### Post by Terry_Lembke on 2013-10-09
JUST BEAR WITH ME FOLKS . I AM a Newbe . I down loaded the 12.04 from the site onto a dvd . put it in my computer and fired it up on it run great got on line and run fine . the drive I want to install on has some auto backup software on it .
My questions are these 
1 can I install from my live dvd ? 
2 the new drive has some auto backup software on it will this need to be removed ? 
3 do i need to partition the drive before or after install ? If so how ?

Thanks in advance 
Terry

---

### Post by oldfred on 2013-10-09
Not sure what auto backup software you have. That is probably Windows anyway and is in either FAT32 or NTFS partition. You can shrink that partition, if data only you can use gparted on liveDVD or flash drive. But often better to use Windows on shrinking NTFS partitions and immediately running chkdsk on that partition from Windows.
You can partition in Advance with gparted (never use Windows to create partitions). Or you can create partitions as part of install. Default installs just create / (root) and swap partitions and install the grub2 bootloader to the MBR of sda (if BIOS booting). 
If second drive best to use Something Else or manual install even if partitioned in advance. then you can choose to install grub2's boot loader to the external drive.
 Install to external drive. Also any second drive.
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
      
 Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---


---
title: "Xubuntu Live USB w/ persistence"
date: 2014-04-28
forum: Installation &amp; Upgrades
---

### Post by James_D on 2014-04-28
Hi all,
 I wanted to give Xubuntu a shot, have been using windows forever. I like the idea of booting from a usb stick. I have the iso, and I am using pendrivelinux's Universal USB Installer. I also have UNetbootin but I'm just using UUI at the moment. Now I made 2 live usb's, and followed the instructions from askubuntu.com ( [http://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb](http://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb) ), which tells me to make 2 live usbs w/100mb of persistence on both, boot from 1, remove casper file using rm -v /media/xubuntu/UUI/casper-rw, open gparted, unmount usb, resize partition to 1000mb, create new partition on unallocated partition, select file system as ext 4 and label as casper-rw, click check mark, shutdown, remove 1st usb, boot from 2nd usb, open terminal and type "df . -h" to check to see if everything matches up correctly. Problem is it doesn't, but wen I open gparted up on reboot, the partition is almost as big as my device. Also, it doesn't save so I guess it didn't add persistence, but I read somewhere that I have to add "persistent" to a file so it will save and I must do it every boot, but I can't find that page anymore =/.

 So in summary, I want to be able to make a Live USB w/ persistent storage that utilizes my whole 32 gb usb, seeing as the max size u can make using UUI is 4gb. I have 2 laptops and the laptop used to create them is a Win 7. Made with UUI. I really need help and I appreciate all the help I can get. Thank you.

---

### Post by sudodus on 2014-04-28
Welcome to the Ubuntu Forums :-)

There are links to several tools and instructions in the following link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

You need to have ***persistent*** as a [boot option]("https://help.ubuntu.com/community/BootOptions").

-o-

Another alternative is to install Xubuntu to one of the USB pendrives. Make a ***regular installation***, but to a USB drive instead of an internal drive. As long as you avoid proprietary drivers, it will be portable (work in many computers). An installed system is more stable, and can be updated/upgraded without limits, while a persistent live system cannot upgrade the kernel.

---

### Post by slickymaster on 2014-04-28
Besides the references posted by sudodus, and just for completeness, I leave two more links for you to go through:

From oldfred, one of the forum mods -> [Choosing between Live USB and Full USB Installation]("http://ubuntuforums.org/showthread.php?t=2130234&p=12578569&viewfull=1#post12578569")
From wiki.ubuntu -> [LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")

---

### Post by James_D on 2014-04-28
Problem solved

---

### Post by sudodus on 2014-04-28
Please post the output of the following commands, when your USB drive is connected

```
sudo parted -l
```
and
```
df
```

It will show the partition structure of your USB drive. Also, did you add the ***persistent*** boot option?

---

### Post by C.S.Cameron on 2014-04-28
Following is a step by step for making Live USB's with persistence size only limited by flash drive size.
I would make the first partition oversize because it is the only one a Windows machine can see.
You can revise partition size later using gparted.

Boot Live CD or Live USB.
Plug in flash drive.
Start Partition Editor.
Create 10 GB FAT32 partition, (on the left side of the bar). (size is optional, extra space can be used for file storage and transfer to Windows machines).
Create a 10 GB ext2 partition to the right of this, labeled it "casper-rw". (ext3 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, Go to the root folder of your Live USB
Enter the syslinux directory, (or for UNetbootin the root directory).
Make the syslinux.cfg file writeable
Replace the contents of the file syslinux.cfg with:

```
    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Shutdown, remove CD, reboot.


First time booting go to users and groups and create an account with yourself up as an Administrator, with password if desired.

Note:
The above code will bypass the Try/Install and Language screens.

---


---
title: "Configure LiveUSB not to create a new partition"
date: 2024-11-18
forum: Installation &amp; Upgrades
---

### Post by hmomcm on 2024-11-18
Ubuntu LiveUSB will create a new partition on the freespace automatically during booting, it is used to store personal informationand data. how can I disable this feature if LiveUSB is public?

---

### Post by yancek on 2024-11-18
I don't know what "Ubuntu LiveUSB" is.  Can you clarify what software that is?    A standard 'live' usb will be read only.  Some software can be used to create persistence, is that what you are referring to?  I'm unaware of any software that creates a new partition on freespace during boot.

---

### Post by hmomcm on 2024-11-22
> **yancek said:**
> I don't know what "Ubuntu LiveUSB" is. Can you clarify what software that is? A standard 'live' usb will be read only. Some software can be used to create persistence, is that what you are referring to? I'm unaware of any software that creates a new partition on freespace during boot.

Ubuntu LiveUSB is a bootable USB stick created by Ubuntu ISO. Select try Ubuntu, then It did create new partition for writing data, may not write data to the system partition.

---

### Post by grahammechanical on 2024-11-22
> Select try Ubuntu, then It did create new partition for writing data, may not write data to the system partition.

I do not agree with you. It is only the Ubuntu installer that creates partitions. And only then if we select Install alongside or Erase disk and install Ubuntu. When running the Try/Live Ubuntu session we have to open GParted to create partitions.

When using the Try/Live session we can use all the applications available, We can even download applications and create documents. Everything is stored into system memory (RAM) and when we close the session everything is lost as RAM is freed up for other uses.

This is why we do not understand what you want to do. 

Regards

---

### Post by yancek on 2024-11-22
>  Ubuntu LiveUSB is a bootable USB stick created by Ubuntu ISO

The Ubuntu iso or any other iso does not create anything.  The iso is used by different software programs to create a bootable USB.  Some of this software will create a 'persistent' data partition on which a user can place data (files/directories) which will remain on reboot.  Also, different software may be installed and remain on reboot but system setting will not change.

---

### Post by ajgreeny on 2024-11-22
As **grahammechanical** and **yancek** have said simply running the live system from a USB memory stick does not write anything to your current hardware or partitions, nor create any new partitions unless you ask it to install the new OS or, using the live OS itself, you open up something such as **gparted**, included in all the live systems, and ask it to create or edit partitions.
You can however read files on the hardware of the computer and also write to those files, though you would have to do that using root permissions, and are not able to write anything as the live user.

If you create a **persistent live OS** any new files or data you save while running the live system will be on the USB not on one of the disks sitting inside the computer. 

If you just run the live system and then shut it down, no changes will be written to disk and everything that was on the computer should be exactly the same.

---

### Post by hmomcm on 2024-11-23
> **grahammechanical said:**
> I do not agree with you. It is only the Ubuntu installer that creates partitions. And only then if we select Install alongside or Erase disk and install Ubuntu. When running the Try/Live Ubuntu session we have to open GParted to create partitions.

When using the Try/Live session we can use all the applications available, We can even download applications and create documents. Everything is stored into system memory (RAM) and when we close the session everything is lost as RAM is freed up for other uses.

This is why we do not understand what you want to do. 

Regards

I created live usb with '**dd if=ubuntu.iso of=/dev/sdX**'. What command at GRUB menu to avoid creating persistent partition?

---

### Post by yancek on 2024-11-23
> I created live usb with '**dd if=ubuntu.iso of=/dev/sdX** 

That command would write the iso to the disk and it would be read only, using the entire device so show what you have.  Run the command below either from the 'live' usb or from another LInux system and indicate which is the drive in reference.

```
sudo parted -l
``` 

No Linux system I have used creates a partition on boot so please explain in detail what you are referring to.

---

### Post by hmomcm on 2024-11-25
> **ajgreeny said:**
> 
If you create a **persistent live OS** any new files or data you save while running the live system will be on the USB not on one of the disks sitting inside the computer. 

If you just run the live system and then shut it down, no changes will be written to disk and everything that was on the computer should be exactly the same.

I'v never said it created a partition on hard disk, but on the usb thumb. By the way, what the new partition name the persistent live OS created?

---

### Post by hmomcm on 2024-11-25
If it is Xubunbu or Lubuntu, does '**dd if=ubuntu.iso of=/dev/sdX' create a **'persistent' USB?

---

### Post by yancek on 2024-11-25
>  If it is Xubunbu or Lubuntu, does '**dd if=ubuntu.iso of=/dev/sdX' create a **'persistent' USB? 				

No.  Some software that can be used to write an iso to a usb will give an option to create persistence but dd does not.  Run the command I suggested in my last post and post the output here so we can see what you mean.

---

### Post by him610 on 2024-11-25
One can use *mkusb* to create a bootable *buntu usb stick with persistence.
For more info on *mkusb*, you can find it here - [https://ubuntuforums.org/showthread.php?t=1958073]("https://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by hmomcm on 2024-12-04
Oh, you are right, my Xubuntu Live doesn't do this. Perhaps I use Linux based on Ubuntu, not Ubuntu flavors. Sorry for my mistake.

---


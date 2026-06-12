---
title: "No install along side windows option"
date: 2014-08-22
forum: Installation &amp; Upgrades
---

### Post by rajanpatel625 on 2014-08-22
I have a 2009 hp pavilion dv6 with a samsung evo 500 GB ssd. It has 2 partitions (according to windows 7). One is Data: NTFS/100 MB and the other is C: NTFS 444.91 GB. I also have 20.75 GB as unallocated space. 

I am trying to install Ubuntu 14 via usb drive but i'm not seeing the option to install along side windows.

---

### Post by yancek on 2014-08-22
Is this Ubuntu 14.04 you are trying to install?
Where were you planning to install Ubuntu?  The only available space is  the 20+GB at the end of the drive.  If you wanted to create a larger partition, you could shrink the main partition from inside windows.  You're not selecting a wubi install, I hope?  I would suggest you boot the Ubuntu medium and when you get to a Desktop, open a terminal (click the Ubuntu logo in the extreme upper left) by typing:  terminal in the search box.  From there enter this command:  sudo fdisk -l(Lower Case Letter L in the command) and post the output here.  You could also run:  sudo gparted and post that image so we have a clearer picture.  You will have much more control if you select the manual option which is called "Something Else" in the Ubuntu installer.

---

### Post by rajanpatel625 on 2014-08-22
Yes, I want to install Ubuntu 14.04 in the unallcoated space. Here is the screenshot you requested.[IMG]https://www.dropbox.com/s/rmaf6gqfxlovmg8/stuff.png?dl=1[/IMG]

---

### Post by kansasnoob on 2014-08-23
It's really not safe to use the automated install options anyway:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

You'll need to create the partitions manually using the Something else option, or you could create the partitions prior to installing using Gparted and then just select which partitions to use during installation using Something else .................. but lets take this one step at a time. How much RAM do you have, we could see if you posted the output of:

```
free -m
```

---

### Post by rajanpatel625 on 2014-08-23
[ATTACH=CONFIG]255755[/ATTACH]

---

### Post by sbnwl on 2014-08-23
Are you comfortable to the resizing (shrink) the partition /dev/sda2 to a smaller size and then creating an ext4 partition in the newly created free space? 

This can be done by booting the machine using Ubuntu 14.04 live usb stick and then choosing the option 'something else' at the bottom of the page on which you expect to find the "Install Ubuntu Alongside windows" option.

---

### Post by mastablasta on 2014-08-23
you can copy text from terminal no need to make screenshots....

select something else
select 
create root partition / about 18 GB big and format it as ext4
create another partition called /swap on the rest of free sapce and format it as swap.

then continue the install...

you can also enlarge empty unallocated space by reducing (shrinking) the /dev/sda2 if you go this path make sure you defragment that c: drive first and do a check disk on it after it is done.

if oyu have important data on the disk back it up first to external drive. you can use clonezilla or redo backup for that.

---

### Post by rajanpatel625 on 2014-08-23
I made a root partition called "/" and a swap partition called "/swap". I installed Ubuntu on the root partition. I restarted my computer and it booted into windows.

---

### Post by rajanpatel625 on 2014-08-23
> **sbnwl said:**
> Are you comfortable to the resizing (shrink) the partition /dev/sda2 to a smaller size and then creating an ext4 partition in the newly created free space? 

This can be done by booting the machine using Ubuntu 14.04 live usb stick and then choosing the option 'something else' at the bottom of the page on which you expect to find the "Install Ubuntu Alongside windows" option.


I want to install Ubuntu in the unallocated space.

---

### Post by yancek on 2014-08-23
> I made a root partition called "/" and a swap partition called "/swap". I  installed Ubuntu on the root partition. I restarted my computer and it  booted into windows.

That is expected behavior if you did not install the Ubuntu Grub bootloader to the master boot record.  There are a number of possibilities here but the best thing you could do is post more details on the system.  You can do this from the Ubuntu installation medium.  Boot it again and select the Try Ubuntu and when you get to the Desktop, open firefox and go to the site below:

 [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

There is a script which you can download there.  It must be run from Linux.  In the Description box at the top, there is a link to instructions which you should read before using.  It should output a file when run called results.txt, post it here.

---

### Post by Mark Phelps on 2014-08-23
> **rajanpatel625 said:**
> I made a root partition called "/" and a swap partition called "/swap". I installed Ubuntu on the root partition. I restarted my computer and it booted into windows.

You don't "name" the partitions that; instead, you use the partitioner in the Something Else option to "mount" the partitions, one as root (/) and the other as swap.  Naming them accomplishes nothing.

Besides, how did you create these partitions -- what tool did you use?

---

### Post by rajanpatel625 on 2014-08-23
[ATTACH]255776[/ATTACH]

---

### Post by kansasnoob on 2014-08-23
That looks like an easy fix, you installed grub in the Ubuntu pbr:

> sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda5 

It needs to be in the drives mbr to be able to boot both Ubuntu and Windows. Just use your live media with Boot Repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The recommended repair should do it.

---

### Post by rajanpatel625 on 2014-08-23
Ok. I only see Ubuntu in my grub menu. How do I fix this so it also shows windows? The "Repair windows boot files" option in boot repair in unavailable. Here is a sum from boot repair [http://paste.ubuntu.com/8127565/](http://paste.ubuntu.com/8127565/)

---

### Post by yancek on 2014-08-23
There is not entry in the grub.cfg file.  Boot Ubuntu and open a terminal and type this command:  sudo update-grub
enter your password when prompted, hit the Enter key and watch the output to see if windows is detected, reboot.

---

### Post by rajanpatel625 on 2014-08-23
I just needed to reboot. Windows boot normally from grub as well as Ubuntu. Thank you for you help.

---


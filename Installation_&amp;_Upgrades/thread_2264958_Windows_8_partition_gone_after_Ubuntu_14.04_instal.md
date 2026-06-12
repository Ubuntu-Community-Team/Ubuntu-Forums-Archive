---
title: "Windows 8 partition gone after Ubuntu 14.04 install"
date: 2015-02-11
forum: Installation &amp; Upgrades
---

### Post by very2 on 2015-02-11
Hi,
I know there is a lot of similar posts, but none of the solutions there helped me. I had Windows 8 running on a partition of my ssd and there was another empty partition. I wanted to install Ubuntu to that partition. During the installation it said that it hadn't found any OS on the hard drive so I thought "great it is already on the right partition, without me having to choose it." I guess I was wrong. Because after the first reboot I got into Ubuntu directly. No boot loader appeared. 

After some research I commented out this line in the etc/default/grub file:

```
#GRUB_HIDDEN_TIMEOUT=0
```

at the next reboot grub 2 appeared, but had no Windows option. Also the dell boot options had no Windows option.

I ran boot repair and clicked on the "recommended repairs" button. After that a Windows Option is available in the dell boot options, but it leads me straight back to the grub menu, where I still don't have a Windows option. 
Here is the result link, that boot repair gave me: [http://paste.ubuntu.com/10156983/](http://paste.ubuntu.com/10156983/)

I also ran ubuntu on a bootable flash drive and did the "recommended repairs" in boot repair there. It didn't change a thing. 
Here is the result link from that: [http://paste.ubuntu.com/10171829](http://paste.ubuntu.com/10171829)
I then clicked on "advanced options" and wanted to change the default OS to load from there, but it only showed the option Ubuntu.

I also tried what is suggested here: [http://askubuntu.com/questions/210914/grub-does-not-show-a-windows-8-option-after-dual-boot?lq=1](http://askubuntu.com/questions/210914/grub-does-not-show-a-windows-8-option-after-dual-boot?lq=1)
with the exact entry suggested:
> Second, you may be able to get GRUB to chainload Windows by adding a suitable entry to /etc/grub.d/40_custom and then doing a sudo update-grub. An entry might look something like this:

  menuentry "Windows 8" {
    set root='(hd0,gpt1)'
    chainloader /EFI/microsoft/BOOT/bootmgfw.efi
}

and I tried this from that same thread:
> Try making a file called /etc/grub.d/30_windows that contains this: 

#! /bin/bash
cat << EOF
menuentry "Windows 8" {
    insmod part_gpt
    insmod chain
    set root='(hd0,gpt1)'
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
EOF
 Then run sudo update-grub and reboot.
I then had a Windows option in grub but it leads me back to the grub menu.

I tried installing grub to the right place but got this error: 
```
sudo grub-install --boot-directory=/mnt/ /dev/sda
Installing for x86_64-efi platform.
grub-install: Fehler: cannot find EFI directory.
```



Now I'm no expert and I really hope that someone who knows how to interpret the boot repair details can tell me what the actual problem with my laptop is and can help me solve this. I still have some data on the Windows partition, that I didn't backup. All suggestions are welcome! But please give me step by step solutions, that I can understand. ;)
Thanks a lot!!

---

### Post by carl4926 on 2015-02-11
> [COLOR=#000000]I still have some data on the Windows partition, that I didn't backup[/COLOR]
It looks like it's gone

---

### Post by yancek on 2015-02-11
> During the installation it said that it hadn't found any OS on the hard  drive so I thought "great it is already on the right partition, without  me having to choose it." I guess I was wrong.

Yes, you were.  Which install option did you choose?  The 'Something Else' is the best one as it gives you control over the install.  Whichever option you chose, you have overwritten windows as there is not sign of any windows partition in the boot repair output with the exception of the windows boot code in the master boot record of the drive.

You also have an efi partition, sda1, and it shows efi files for windows and Ubuntu but that's it.  You might be able to recover some data from the former windows partition but you probably installed Ubuntu over it.  I don't use windows so I don't know of any software to use, you might try test disk but the more you boot the system the less likely that is.

---

### Post by very2 on 2015-02-11
Alright, thank you for explaining. I didn't choose something else  because I didn't understand why there was suddenly so many partitions  with sdX names, when I thought there should only be two. 

So  after trying to recover my data, I have to change the partition sizes  again, to get space for a new windows installation again?

---

### Post by yancek on 2015-02-11
> Alright, thank you for explaining. I didn't choose something else   because I didn't understand why there was suddenly so many partitions   with sdX names, when I thought there should only be two. 

A linux installer will show all the partitions, or at least it should, whether they are Linux or windows so you had the efi partition (which you still have) plus your windows system partition plus any other data partitions you might have had for windows.  Now you just have the efi, the Ubuntu partition and the swap.  When you install windows 8, make sure you select the option to use UEFI.  I haven't used windows 8 so it might do that automatically.   You should also have something like an expert install option with windows although it may not be called that.  If you do, use that so it doesn't totally overwrite your Ubuntu install.  The 'Something Else' option is usually referred to as a Manual or Expert install in other Linux distributions and that naming convention was also used on earlier versions of Ubuntu but that' what it is.  It gives you some control over the install.

> So  after trying to recover my data, I have to change the partition  sizes  again, to get space for a new windows installation again? 		

Yes.  Use the installation media you used to install Ubuntu which has the GParted partition manager on it and shrink sda2 which takes up most of the drive, to a size you are comfortable with and either leave enough unallocated space or you can create a primary partition on which to install windows and format it as ntfs from GParted.

---

### Post by very2 on 2015-02-12
Thank you again!

---


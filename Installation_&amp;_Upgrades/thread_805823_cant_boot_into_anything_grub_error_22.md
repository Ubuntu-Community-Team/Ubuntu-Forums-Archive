---
title: "cant boot into anything grub error 22"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by uheaven on 2008-05-24
Hey there... I recently installed Ubuntu 8.04 nad loved it very much... i installed it with a dual-boot Vista. It went alright for a few days until i decided i needed more space for Ubuntu, so i deleted one of the Vista Partitions (was planning on deleting Vista someday). Then, the problem arised.. i restarted and it says:

Grub Loading Stage 1.5
Cant Load                  *(Or Something Like That)*
grub error 22

And that's all... what can I do?? :confused:
Plz.. urgent?

---

### Post by Pumalite on 2008-05-24
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)
Boot your Live CD and post:
sudo fdisk -l

---

### Post by cdtech on 2008-05-24
22 error code means no such partition. This error is returned if a partition is requested in the device part of a device- or full file name which isn’t on the selected disk.

No big deal. Boot into the live Ubuntu cd.

When you get to the desktop open a terminal and enter.

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

grub >find /boot/grub/stage1

Whatever was returned for the find command use it in the next step (you are still at grub>.

grub >root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

grub >setup (hd0)

Then exit the grub shell

grub> quit

Hope this helps....

---

### Post by Pumalite on 2008-05-24
22 : No such partition
        This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 

For example there might be a mistake in the menu.lst file in the partition number, if there is no such partition as specified in the 'root (hdx,y)' line.
example,
title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
Look at your partitions with your partitioning software or run 'sudo fdisk -lu' in a terminal and make sure you have the partition number correct here in your menu.lst boot entry.

This is also the error that people often see after they delete their Linux partition but they still have that partition's GRUB's stage1 written in the MBR.

They can easily cure that by overwritting the existing GRUB IPL code with code for another bootloader in another operating system.
In other words either re-install GRUB or re-install Windows bootloader or some other bootloader or boot manager. In Super Grub Disk, go 'English Super Grub Disk'-->'Windows'-->'Fix Boot of Windows', or see my 'Un-install Page'.
Don't bother doing anything if a new (Linux) operating system will soon be installed, the new operating system will install a new bootloader and cure this error automatically.

If there is another operating installed in the computer, re-writing the bootloader'e MBR code for that operating system's bootloader and overwriting the now useless GRUB code will cure the problem. This can be easily done with Super Grub Disk.
1) Re-install a GRUB to MBR from another Linux
2) Re-install a Windows Bootloader to MBR.
     (These two above items are both options in Super Grub Disk that can be selected and SGD will do it for you).

I got GRUB error 22 myself one time after doing quite a lot of work to the partitions in my wife's computer. I tried to fix the boot of grub with an older version of Super Grub Disk, not realizing her partition numbers had been unexpectedly changed somehow by disk partitioning software.
I installed grub from the wrong partition by accident.
Later I found out the real cause of all the trouble was a dirty DVD/CD-ROM drive that caused read problems from my partitioning CD.

 Anyway I got  Grub Loading Stage1.5
       Grub Loading Stage1.5
       Grub Loading Stage1.5
       Grub Loading Stage1.5...and so on, scrolling endlessly down the monitor.

I couldn't even boot with Super Grub Disk's 'English Menu'-->'Gnu-Linux'-->Boot Gnu/Linux Directly'.
After much mumbling and head scratching and trying various ideas I decided to run a file system check with my GParted -- LiveCD. When that was done I clicked on the triangular buttons for a report and found that GParted LiveCD had repaired quite a few problems in that filesystem.

So tried again, this time from the Super Grub Disk menu I pressed 'c' for a Super Grub Command Line Interface, and booted manually using a direct kernel style boot
The operating system booted and I was able to re-install Grub to MBR, and configure menu.lst with new partition numbers.

GParted LiveCD saved the day for me. I didn't have to sleep in the doghouse after all! :)
The lessons here are,
1. keep my CD-ROM drives clean, and
2. to try a filesystem check if I am having unusual troubles booting.

It's easy to run a file system check on any file system with a GParted -- LiveCD, just boot with the CD and click on the filesystem (partition) to be checked and click 'check'.
Click 'Apply' (on the toolbar), and then 'Apply' again (in the confirmation box).
Then wait a few minutes.
When it's finished it's a good idea to click on the arrow shaped 'Details' button in GParted to expand the output box. Make sure you click on all the subsequent arrow buttons too, so you will expand it all fully so you can read the report and see what was done to fix your file system.
See my File Systems and Mounting Page for more about file system checking in Ubuntu.

---

### Post by uheaven on 2008-05-25
> **cdtech said:**
> 22 error code means no such partition. This error is returned if a partition is requested in the device part of a device- or full file name which isn&#8217;t on the selected disk.

No big deal. Boot into the live Ubuntu cd.

When you get to the desktop open a terminal and enter.

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

grub >find /boot/grub/stage1

Whatever was returned for the find command use it in the next step (you are still at grub>.

grub >root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

grub >setup (hd0)

Then exit the grub shell

grub> quit

Hope this helps....

That recovers the GRUB, i can load into Windows Vista/LongHorn but when i load into ubuntu 8.04 it again says grub load error 22!!!

tryin' out the other option posted by pumalite now

---

### Post by linmalex on 2010-02-12
I have been having the same problem, except that putting in a LiveCD doesn't help, as in it won't boot even from the CD drive. Any tips from that point?

---


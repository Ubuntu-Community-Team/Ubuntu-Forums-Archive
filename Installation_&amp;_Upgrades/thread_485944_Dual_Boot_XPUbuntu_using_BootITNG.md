---
title: "Dual Boot XP/Ubuntu using BootITNG"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by GG_HTPC on 2007-06-27
I saw a few posts asking for help on dual boot. My experience with BootitNG is shared below. I was able to to dual boot (XP, Ubuntu) and image the HDD all from one tool. I used BootITNG as my partition managers, imaging and boot manager. Thanks to, [http://www.goodells.net/multiboot/index.htm](http://www.goodells.net/multiboot/index.htm) I was able to partition my HDD just the way I wanted (8MB Bootit EMBR, 10GB Ubuntu, 10 GB Windows XP and rest ~400 GB as extended partitions). In the extended partition, I have a 50GB OS backup for the images of OS, 10 GB Linux swap and rest for data. 

General steps that worked for me using BootitNG. I am sure there are other (better) ways to do:
1. Boot from BootITNG CD and install BootIT to HDD. In the settings, mark "Limit partitions", this will keep Ubuntu and other OS to create more than 4 primary partitions. Create partitions as desired making Ubuntu partition Ext3 and Windows as NTFS. 
2. Create Boot items from Boot Menu for Ubuntu and Windows. Make Windows item Active. From the Boot Menu, choose Windows partition to boot. You will be prompted for bootable media. Insert the Windows installation disk in the CD drive.
3. Install Windows from the Windows CD in its all glory (updates, drivers, patches etc). Took me good 10 hours but I have a lot of programs and patches. I did not install the data at this point.
4. Boot from BootITNG. Go to the partition works dialog. Select the WIndows partition and click image. You will notice a message "* paste pending...". Select the OS backup logical partition and past the image where you like. I created a folder for Windows and another for Ubuntu and used dates as file name. As a backup, I also saved my image to a network drive.
5. Now set Ubuntu as Active partition. This time boot Ubuntu from the Boot Menu and insert Ubuntu LiveCD.
6. In Ubuntu installation process, choose "Manual" partitioning instead of Guided partitioning. Choose Linux partition and mount to root "/". You have to format the partition from Linux and choose Linux logical swap partition for Linux Swap. As long as Linux confirms the paritition numbers and capacity in general range, you are good. Ubuntu will automatically import Windows desktop and accounts.
7. After the installation is completed, you should get GRUB menu prompting you boot from Ubuntu or Windows. This is good news. Try booting Windows. I got an error message "Windows could not start... hal.dll". This is because I moved Windows partition and restored the image in a new partition while Windows remember the boot information from last time. Boot from BootitNG disk, go to partition works and click details on the Windows partitions. In the the Details dialog, click Edit file and goto the Windows folders. You can edit "Boot.ini" directly from within BootITNG. Update the partition number as explained by Dan Goodell.
8. At this point of time, GRUB will allow you boot between Windows and Ubuntu.
9. Instead of using GRUB, I wanted to use BootITNG as my boot manager so I can image the partitions as well. Install BootITNG again to HDD to restore the BootIT EMBR. 
10. Now Ubuntu will refuse to boot. I found another pointer on Ubuntu forum (Thanks). Boot from the LiveCD and initiated the terminal and follow the steps below:
a) sudo grub
b) find /boot/grub/stage1 (Note:this will give you location of the boot partition) For me it came back as (hd0,2)
c) root (hd0,2) (note: use whatever comes up in b above)
d) setup (hd0,2)
e) quit

After executing all the steps above, my system shows BootitNG menu and allow me to boot between Ubuntu and Windows. BootITNG also allows me to make an image of any partition and store it on any hard disk. I dont know if these exact steps will work for you or not. 

Thanks for everyone on this forum.

---

### Post by demonzrulaz on 2007-06-29
good tutorial! i just have one question. Will I be able to run Ubuntu AND windows XP from the same harddrive? i have only one hard drive with 147GB total space - 36GB currently being used for XP.

---

### Post by GG_HTPC on 2007-07-02
Yes. I have realtively large HDD but most of it is for data. Between Ubuntu and Windows XP, I am hardly using 20 GB.

Have fun!

---

### Post by derby007 on 2007-07-02
I have WinXP, Edgy Ubuntu/Kubuntu/Xubuntu, Fiesty Ubuntu on my system at the moment, ie. 3 * OS's, all on one HDD. Whats the best way of creating an 'iso' image of my whole system or is it possible ? or is it only possible to 'iso' a particular partition?

---

### Post by demonzrulaz on 2007-07-02
> **derby007 said:**
> I have WinXP, Edgy Ubuntu/Kubuntu/Xubuntu, Fiesty Ubuntu on my system at the moment, ie. 3 * OS's, all on one HDD. Whats the best way of creating an 'iso' image of my whole system or is it possible ? or is it only possible to 'iso' a particular partition?

im pretty sure you would have to create 3 seperate ISO's but don't take my word for it. (sorry)

i have another question. I already have data on my hard drive. I want to install ubuntu. Can i just create a new partition on my C drive? Will this affect my current Windows installation (like my files and folders)? I really don't feel like backing up 20 GB.

---

### Post by derby007 on 2007-07-03
What I did was : first > defragment your C drive, let it run overnight, then> I used Norton Partition Man to create 2 new partitions, (or use an extended partition if you have more than 4 primary ones) one partition for / & one for swap, ie. you are resizing your C drive's free space. Once you create the partitions just leave them unformatted. Then boot up the live CD and I think I then went into Manual mode in the CD's partitioner, root partition '/' is set to the EXT3 filesystem, and 'swap' is set to SWAP, usually 2* 'your Ram size'. 
note: I used Norton in WinDoze because it worked for me, it all ran smoothly, so why change..... :)

---

### Post by demonzrulaz on 2007-07-03
sorry but now im really confused. i have norton partition magic. can i use that? what do i exactly do? i really don't understand the terms u use...sorry (thanks for ur reply though). do i have total of 3 partitions?

---

### Post by derby007 on 2007-07-04
yep use Norton : create 2 new (blank) primary partitions :
1: use say 20GB (or whatever) for  /    
2: use 2* Ram for your  swap

Then boot up your Live CD (or Alternate CD).
Then 'manually' partition the 2 blank partitions as follows :
by using the CD partition manager program>
 /  to ext3
 swap to swap

That should do it. I'm writing this from memory, so I hope its right.

---


---
title: "Installing multiple OSes"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by nicnicman on 2008-05-24
Recently I attempted to install Ubuntu v8.04 from the Live Download but I had a couple of problems.  First while in the manual partitioner I was asked to assign a swap file but I am unsure of where or how to assign it.  Second, after continuing without the swap file (hoping to assign it later) I received the error message "unable to install grub. This is a fatal error".  

My system has 2 internal hard drives and one external.  It is set to dual boot with WinXP Media Center 32-bit and WinXP 64-bit edition.  WinXP Media Center is located on the first hard drive C and WinXP-64 is located on the second hard drive J.  Both of these internal hard drives are use SATA.

I would like to have Ubuntu as one of my OS options when booting the computer but I am unsure of the best way to do this.  
Recently downloaded the alternate text based Ubuntu hoping that this would work better.  If any one has any suggestions or solutions I would really appreciate it.

Thanks 
nicnicman

---

### Post by Pumalite on 2008-05-24
This might help:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Jack Shankle on 2008-05-24
I'm going to do the same thing you are.
There is a site that might help in the process:

      xxxx:/thevistaforums.com
  xxxx= http

in there in the general vista look for a sticky called
"dual boot in various combinations". 

It gives detailed instructions for installing various combinations
of OS.

Hope this helps,
JPS

---

### Post by nicnicman on 2008-05-24
After downloading the Ubuntu v8.04 Alternate Desktop (text based) CD I was successful installing Ubuntu.  Now my first hard drive holds WinXP Media Center and my second hard drive holds both WinXP 64-bit and Ubuntu.

Originally I partitioned two 20 GB logical drives (using Partition Magic) on my second hard drive.  One for WinXP64 and one for Ubuntu.  When I attempted to install Ubuntu on one of these partitions I was having difficulty setting up the swap file.  Eventually I broke up the 20 GB (actually came out to 21 GB) partition into two partitions.  The first is a 15 GB primary partion formatted as ext3 and the mountpoint is /.  The second is a 6GB logical partition (2 x my ram, which is 3GB = 6GB) formatted as swap.  

Once this was finished I installed Ubuntu with ease.  The first thing I see when I boot up is a list containing the Ubuntu OS, Ubuntu recovery mode, Ubuntu w/ Memtest86, and an option to boot into the Windows OSes on my computer.  When I select the last option I am brought to another list which has my WinXP Media Center and WinXP 64-bit.  

Actually I would like to simplify this list a little.  I was wondering if its possible to have just three options:  WinXP Media Center, Ubuntu, and WinXP 64-bit. In that order.

Thanks for all your suggestions and if you have any more please let me know.

---

### Post by Pumalite on 2008-05-24
Not a good idea. Leave it as it is.

---

### Post by lswest on 2008-05-24
One thing i would do is decrease the size of the swap you have, you won't ever use more than 3GB of swap, and i'd recommend just 2G, and putting the other 4GB to your root filesystem.  Just a thought.

Otherwise, best to keep the default GRUB entries, since you may need them.

---

### Post by pixel :-) on 2008-05-24
We do not recomend to remove the recovery thing and mem test.

You can change the order,you need to edit a file, but i'm whoried that you going to damage it.

send us the file /boot/grub/menu.lst, an attachment, don't copy paste the content in a post
we will edit it correctly for you

---

### Post by nicnicman on 2008-05-25
For some reason I am getting an error when trying to upload this file as an attachment.  It says "menu.lst Invalid File".  

I'll continue trying but if you have any suggestions as to what could be causing this please let me know.

Thanks

---

### Post by Pumalite on 2008-05-25
Post:
sudo fdisk -l

---

### Post by sir_napsalot on 2008-05-25
Is it possible to do a dual boot install using the normal install method (GUI) for Gutsy? other OS will be Win XP Pro.

---

### Post by Pumalite on 2008-05-25
Post your specs.

---

### Post by nicnicman on 2008-05-25
Here are the results when I type "sudo fdisk -l" into the terminal

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       18846   151332300    7  HPFS/NTFS
/dev/sda3           18847       19452     4867695   db  CP/M / CTOS / ...

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf571318

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       37089   297909360    f  W95 Ext'd (LBA)
/dev/sdb2           37090       38913    14651280   83  Linux
/dev/sdb5               2       33813   271594858+   7  HPFS/NTFS
/dev/sdb6           33814       36363    20482843+   7  HPFS/NTFS
/dev/sdb7           36364       37089     5831563+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2de93b0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

---

### Post by sir_napsalot on 2008-05-25
AMD Athlon 64 3000+
80GB HDD
2GB DDR 400 RAM
ATI Radeon x1600 series Video Card

---

### Post by Pumalite on 2008-05-25
> **sir_napsalot said:**
> AMD Athlon 64 3000+
80GB HDD
2GB DDR 400 RAM
ATI Radeon x1600 series Video Card

Use 8.04 64 bit Alternate CD to install. Let Grub install to MBR.

---

### Post by Pumalite on 2008-05-25
> **nicnicman said:**
> Here are the results when I type "sudo fdisk -l" into the terminal

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       18846   151332300    7  HPFS/NTFS
/dev/sda3           18847       19452     4867695   db  CP/M / CTOS / ...

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf571318

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       37089   297909360    f  W95 Ext'd (LBA)
/dev/sdb2           37090       38913    14651280   83  Linux
/dev/sdb5               2       33813   271594858+   7  HPFS/NTFS
/dev/sdb6           33814       36363    20482843+   7  HPFS/NTFS
/dev/sdb7           36364       37089     5831563+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2de93b0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

/boot/grub/menu.lst should be in sdb2
Post:
cat /boot/grub/menu.lst

---

### Post by meierfra. on 2008-05-25
> For some reason I am getting an error when trying to upload this file as an attachment. It says "menu.lst Invalid File". 
Change  ".lst" to ".txt"

Or just copy and past the context of the file to your post, but put it inside the CODE tags.

---

### Post by nicnicman on 2008-05-25
I've found the file but for some reason I receive the error "menu.lst, Invalid File" when I try to upload the file as an attachment.

Any suggestions?
I could copy and past the contents of the file?

---

### Post by nicnicman on 2008-05-25
Okay, I've got it now.  Thanks meierfra.  Anyway, here is the attachment.

---

### Post by Pumalite on 2008-05-25
Looks OK. to me.

---

### Post by nicnicman on 2008-05-25
I noticed that the Windows OSes (WinXP MC and WinXP Pro 64-bit) are represented under one title, "Windows NT/2000/XP (loader)"  When this item is selected at start up I am taken to another list which contains the two Windows OSes.

Does this selection start NTLDR?  Is it possible to combine the two lists into one?  Is it possible to then change the order of the options?

Thanks

---

### Post by Pumalite on 2008-05-25
Are you able to boot Windows and Ubuntu? If so; leave it as it is.

---

### Post by meierfra. on 2008-05-25
> Is it possible to combine the two lists into one? I

You cannot have separate items for  Windows on the Grub menu.
But you can add "Ubuntu" to the  Windows bootloader and end up with just one menu. It's a little bit tricky, but if you want I can show you how to.


To have Windows before Ubuntu on you Grub Menu,  move

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


between the line

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

and

### BEGIN AUTOMAGIC KERNELS LIST

---


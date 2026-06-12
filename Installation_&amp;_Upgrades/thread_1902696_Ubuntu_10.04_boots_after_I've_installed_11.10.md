---
title: "Ubuntu 10.04 boots after I've installed 11.10"
date: 2011-12-31
forum: Installation &amp; Upgrades
---

### Post by sallymc on 2011-12-31
This is really odd.  I created an ISO disk of 11.10 and ran it, picking the option where I delete everything and start from scratch.  The install process takes its time and then finishes, but when I reboot the machine, 10.04 opens!  Any ideas?

---

### Post by BC59 on 2011-12-31
What system was previously installed in the computer?

---

### Post by sallymc on 2011-12-31
10.04 was previously installed.  I suspect it has something to do with partitions.  10.04 is on sdb2 and 11.10 is on sda1.  I think the pc is booting from sdb2 and I need to change this to sda1.  Any ideas how?  Even better - I want to get rid of 10.04 and the partition completely - how do I do this?  Thanks!

---

### Post by BC59 on 2011-12-31
First check if it's like this, run in a monitor:

```
sudo parted /dev/sda print
sudo fdisk -l #(it's a lower case L)
```

and post the result.

---

### Post by darkod on 2011-12-31
First of all, in the partitioning step are you using manual option (Something Else) or one of the auto options.

If you use the Erase and use whole disk, that's what it will do.

If you want to set it up manually for bigger control, or to set up separate /home partition, you have to specify which partitions to use and for what (mount points).

---

### Post by sallymc on 2011-12-31
When I installed 11.10, I selected the auto option that supposedly deleted everything and then installed the new version.  But I guess this doesn't remove additional partitions.

Output from the 2 commands requested:

```
sally@sally-pc:~$ sudo parted /dev/sda print
Model: ATA WDC WD740ADFD-00 (scsi)
Disk /dev/sda: 74.4GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  73.3GB  73.3GB  primary   ext4            boot
 2      73.3GB  74.4GB  1072MB  extended
 5      73.3GB  74.4GB  1072MB  logical   linux-swap(v1)

sally@sally-pc:~$ sudo fdisk -l

Disk /dev/sda: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00049fbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8910    71564288   83  Linux
/dev/sda2            8910        9040     1046529    5  Extended
/dev/sda5            8910        9040     1046528   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004821b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         244     1951744   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sdb2             244        5107    39062528   83  Linux
/dev/sdb3            5107       10578    43944960   83  Linux

```

---

### Post by darkod on 2011-12-31
Yes, that's what it does but you never said you have two disks. You installed 11.10 on the other disk, so now you have both the 10.04 and 11.10. You are booting the disk with 10.04 first so it boots the 10.04.

---

### Post by sallymc on 2011-12-31
Thanks Darkod.  I'm definitely not clued up with this stuff.  Two disks you say... do you mean 2 partitions or 2 physical discs?  I don't know how to fix it.  I'm not interested in 10.04.  Ideally, I only want 1 partition with 11.10 on it.  How do I do this?  And how do I remove 10.04?  Or how do I boot using 11.10?  Thank you!

---

### Post by BC59 on 2011-12-31
Do you have connected an external hard drive?

---

### Post by sallymc on 2011-12-31
No external hard drive - it's all inside the box!

---

### Post by BC59 on 2011-12-31
@darkod, is it a RAID or something?

---

### Post by sallymc on 2011-12-31
I'm not sure if this is useful, but I've attached 2 screenshots of the gparted information that it displays for sda and sdb

---

### Post by darkod on 2011-12-31
No, doesn't look like a raid since one disk is barely 80GB.

Do you have any data you need to keep on any of the disks? We need to know.

Also, you need to decide whether to use the smaller for OS and the larger for data, is that gonna work for you?

---

### Post by sallymc on 2011-12-31
I have everything backed up onto disk - I did this before the upgrade so I am happy to trash everything on the pc - no probs.  I think it would be easier to install the OS on the bigger disk and I'll put my data there too.  But I'm not the expert here and am happy to listen to you.

---

### Post by darkod on 2011-12-31
On the contrary, you are the expert as to how you want/need to use your computer. :)
We can help with instructions, etc, but not make decisions for you.

If you are happy to trash everything, start another new 11.10 install and use the option Erase and use whole disk again. But this time pay attention in the next step, as it will ask which disk to use. Select the /dev/sdb, 250GB. Even if the device is different, like /dev/sda, pay attention to use the 250GB disk, larger one.

If I'm not mistaken it displays the size next to the device name.

Since your BIOS is set to boot from the 250GB, I guess after the new install you will boot into your new 11.10.

Note that the first time the boot menu might show the 11.10 from the other disk too, forget about it for a moment, you will delete it later. Lets see if it installs fine on the 250GB first.

Note that the auto install doesn't create a separate /home partition. You seem to have one now. Do you want to keep that king of layout or you don't care about it?

---

### Post by sallymc on 2011-12-31
Thanks Darkod for the suggestion.  When I installed Ubuntu from the boot disk, I didn't even realise that that was a dropdown box!  So I tried it again and picked the 250G option and the install completed (after 2 hours). But the pc won't start!  It gets stuck on a black screen with a single cursor in the top left corner and that's that!  I've been able to get onto the internet by running Ubuntu directly from the boot disk.  If I try the entire install again, it recognises that there is already an 11.10 installed and asks if I want to do the new installation alongside the existing 11.10.  Also, there's still mention of sda and sdb which I don't understand.  

It's about to bong midnight here in SA.  Will look again in the morning.  Any help would be greatly appreciated.

And happy new year to you all out there!

---

### Post by sallymc on 2012-01-01
I've reinstalled the whole thing again (now for the forth time!) and still the OS is unable to start up and gets stuck in a black screen with a single cursor prompt flashing... any ideas?

---

### Post by darkod on 2012-01-01
Can you post the ouput of:
sudo fdisk -l

again?

---

### Post by sallymc on 2012-01-02
This is the output :

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00049fbe
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   143130623    71564288   83  Linux
/dev/sda2       143132670   145225727     1046529    5  Extended
/dev/sda5       143132672   145225727     1046528   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001c810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   486303743   243150848   83  Linux
/dev/sdb2       486305790   488396799     1045505    5  Extended
/dev/sdb5       486305792   488396799     1045504   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
```

---

### Post by darkod on 2012-01-02
Just in case lets reinstall the grub2 on both disks, so it doesn't matter which one you boot from.

From live mode do:

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
sudo grub-install --root-directory=/mnt /dev/sda

That will install it on both disks. Reboot and see if you get a working grub2.

---

### Post by sallymc on 2012-01-02
IT WORKS!!!!!!!!!!!!!!!!

Oh Darkod you are such a superstar.  I feel like a huge load has dropped off my shoulders and getting on the next plane to Spain to give you a big long hug. :D Thank you, thank you.  I am delighted.

Have a wonderful 2012 with all good health, happiness and peace.

Sallymc  :D

---

### Post by darkod on 2012-01-02
I'm glad it works. Happy New Year too.

The next thing you need to think about is formatting the 74GB disk to use it as data disk. That will erase the ubuntu on it but you don't care about it anyway. It's up to you when you want to do it and how.

---

### Post by sallymc on 2012-01-03
I think we need to format the 74GB disc please.  Everything is extremely slow and seems to be doubled.  My Evolution Mail, for instance, has 2 Inboxes.  I am sallymc, but the computer refers to sallymc@sallymc.

I also received the following message after sending an email (don't know whether this has anything to do with this) :

Your message was sent, but an error occurred during post-proceeding
The reported error was "Failed to append to mbox:/home/sallymc/.local/share/evolution/mail/local#Sent/Sent: Invalid folder URI 'mbox:/home/sallymc/.local/share/evolution/mail/local#Sent/Sent'
Appending to local 'Sent' folder instead.".

Look forward to hearing from you.
Sally

---

### Post by darkod on 2012-01-03
The two operating systems are independent of each other. You shouldn't have two Inbox's because of that.

It might be related to how Thunderbird is configured. Sometimes it creates local folders as default, but you can also set it to use other folders. I'm not familiar with the options for Thunderbird in details.

---

### Post by sallymc on 2012-01-03
It is not only Evolution that is doubled, all sorts of things are.  On startup, when it shows the maroon screen, each line of the white writing  in the top left hand corner is repeated. 
 
Can you work me through the formatting  of the 74GB disk?
Sallymc

---

### Post by darkod on 2012-01-03
Copy all the data you need from that disk first.

Boot your ubuntu on the 250GB disk.
Install Gparted in terminal with:
sudo apt-get install gparted
After that open Gparted and look at the drop-down box in the top right corner, select the 74GB disk.
Select one by one all the partitions and hit the Delete button in the toolbar of Gparted.
Then when there are no partitions present, hit the Create button and create one ext4 primary partition on the whole disk.
Hit the green tick mark button in the toolbar, until you do this no changes are executed.

That should be it. To get rid of the other ubuntu in the boot menu, in terminal do:
sudo update-grub

Also, in the boot menu some things might just look doubled. For example, there is one entry for the main ubuntu system, and one for recovery mode, etc.

---

### Post by sallymc on 2012-01-05
Hi Darko,
I do appreciate your help.  The problems continued, so sent my computer to a computer man and he discovered there was a problem with the smaller hard drive, so he  removed it.  After re-installing Ubuntu everything now works perfectly.
I guess these things happen but feel embarrassed that I could have wasted your time.  If so, my apologies.
Yours
Sallymc

---


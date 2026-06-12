---
title: "Question about installation (new partitions)"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by romaDa on 2008-11-18
Hello everyone I am a new user and I have some questions about the installation of ubuntu 8.10. I've looked around the forums but could not find an answer.

First of all I shrinked my hdd to make some space for ubuntu since I already have vista. 

The problem I run in to is after I choose the 'manual' option to set-up my partitions I am not quite sure what to do though I know I need ext3, swap, and something else I think.

I would greatly appreciate it if someone could tell me step by step how to proceed in order to correctly install ubuntu and keep my vista sine the only tutorials I could find online were the ones where ubuntu uses the whole disk and erases everything else.

Thank you for taking your time to read this. :)

---

### Post by zwygart on 2008-11-18
If you shrinked your partition, you have some free space.
During Installation, you will be asked where you want to install Ubuntu. Choose the option "Use free space". NOT "use sdx" or something. Be sure to choose Free space. This is one thing to be carefull.
The second thing is where to install the Bootloader GRUB. At the last page of the wizard or 6/7, it will have a option "Advanced" in the right bottom corner. In this you choose where to install GRUB. I suggest you choose sda2. If you make an error in this step windows will not be bootable. To fix this you need a windows CD (XP or Vista) and execute the command fixmbr and fixboot.

Don't be afraid of this. As long as GRUB is NOT on your Vista partition (sda1), it will be easy to help you. Otherway they are solutions. Keep writing on forums. Have you a laptop or desktop? If you have to HD, it will be easier to install on the other disk(hdb).

So install on the free space and you should be OK.

---

### Post by em4r1z on 2008-11-19
Actually, you don't need *'ext3, swap and something else'* but, at least, a system partition to install the system to. The file system used by this partition may be ext2, ext3, JFS, XFS, ReiserFS, etc., and if you have 2 GB of RAM you'll only need a swap partition if you use the hibernate function (I haven't used ext3 in years and I only use a swap partition in my laptop.)

I recommend you to create a separate partition for your documents, in case you need/want to reinstall. The root partition should be around 5-8 GB, the swap partition (if required) should be slightly bigger than your RAM, and the documents partition could use the remaining space.

To set this up in the installer:
- Use the manual configuration.
- Select the free space.
- Create the swap partition (if needed).
- Set the desired space for the system partition, choose its file system and select '/' as its mounting point.
- Do the same for the documents partition but select '/home' as its mounting point.

---

### Post by romaDa on 2008-11-19
Thank you all for the replies.

To answer some of the questions:

I did use the free space that I made and selected the following options (off the top of my head I may forget one or two): Primary, ext3, beginning, /boot.

The place where I'm getting stuck is I'm not sure how to create the swap partition after that since the ext2 or ext3 is taking the whole free space that I made.

If it would help my system is a

Dell Studio 15
Windows Vista SP1 32-bit
3Gb RAM
320GB HDD

---

### Post by romaDa on 2008-11-20
Anyone? :)

---

### Post by icanfly0307 on 2008-11-20
Set the ext3 partition to a smaller size, I'd say around 3.5 GB less. That will leave the remaining 3.5 GB for swap.

---

### Post by zwygart on 2008-11-20
If you automatic install by saying install on free space, that should all be done. If you setted it manually, check to be sure that it doesn't created a swap before making another.

It would be helpfull if you post the output of fdisk -l
This print the partition table.
P.S.: To copy from a terminal press CTRL + SHIFT + C.
In the forum press CTRL + V

---

### Post by romaDa on 2008-11-24
I will try the automatic option and if not I will print the partition table.

Thank you very much for all your help guys :)

---

### Post by romaDa on 2008-11-24
So I did as you said I let the automatic option use the free space I made and now it's working except my update manager or the add/remove don't work anymore and my graphic card driver doesn't download/install at all and stays at 0%.

As for the problem with the update-manager the error I get is the following:

E: Could not get lock/var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

If anyone knows how to fix this I'd be very thankful for now I'll keep looking around the forums. :)

---

### Post by romaDa on 2008-11-24
PROBLEM SOLVED!

I solved both of my problems by entering this in the terminal:

sudo rm /var/cache/apt/archives/lock

Big thank you to all who helped me! :)

---


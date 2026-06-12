---
title: "Error while installing Ubuntu on Macbook: partitions overlap"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by billybobby2010 on 2010-08-04
Having lost a couple days on installing Ubuntu, I now definitively need some help before giving up... 

I installed Ubuntu on my Macbook, but I cannot boot it from rEFIT, nor can I sync the partitions with rEFIT. When I do, it says: 

"error: not found returned from gptsync.efi
status: MBR partition table is invalid, partitions overlap"

So, here is how I proceeded to install:

1. A clean install of Mac OS X 10.5
2. Installation of rEFIT
3. Bootcamp to partition the drive in 2
4. Boot Ubuntu CD Live and with Gparted, I deleted the second (windows) partition created with bootcamp so to have free space.
5. I installed Ubuntu with the installer.
6. On the last step, I clicked on 'advanced' and choose to install boot loader (grub) to dev/sda, which was by default. 
7. Reboot
8. Partition tools in rEFIT to sync. I got the error described above.

After all that, I thought I made a mistake in the choice of the partition on which to install grub. Thus, I wiped out everything from my drive except Mac OS X and started again from the beginning the reinstallation of rEFIT and Ubuntu. 

This time, I choose 'dev/sda2' which is my Mac OS X partition. Yet, it didn't solve the problem: I still got the same error when I try to sync my partitions.

Following something I read on the net, I reboot from the Ubuntu Live CD and tried the following command in the terminal:

sudo apt-get install gptsync 

 The terminal added: impossible to find the gptsync package. 

Well, I'm really lost right now, I don't even have a clue what can be the problem... please help me. Thx

---

### Post by lechien73 on 2010-08-04
I don't know if you've seen this thread, but it seems to describe similar symptoms to yours: [http://uri.tl/u](http://uri.tl/u) - post #71 has instructions on how to overcome this error.

You could always try downloading gptsync directly from the Ubuntu repository: [http://packages.ubuntu.com/lucid/gptsync](http://packages.ubuntu.com/lucid/gptsync)

But maybe you should check System > Administration > Software Sources before you do. Also make sure you have a mounted partition to install gptsync to.

---

### Post by billybobby2010 on 2010-08-04
Thx lechien, I'll have a look on the link you gave me and see what I can do...

---

### Post by billybobby2010 on 2010-08-04
The comments #73 in the thread you indicated me says:

"It appears that the dual mac/ubuntu instructions are incorrect. They tell you to install Grub to sda3. the "bug" in the installer appears to create a separate partition for Grub rather than installing it on the linux partition itself. So it installs grub on a 917kb partition with no format. Hence the error from GPT."

This is indeed what happens to me: the installer creates a separate partition for Grub rather than installing it on the linux partition. I guess it's where the problem comes from. 

So  I booted into my livecd, deleted sda3(917Kb grub partition), I wanted to reinstalled grub through the ubuntu installation but I didn't know how to do so without reinstalling Ubuntu itself so I finally decided to just reboot and see want happens now that I deleted the grub partition... rEFIT is now able to sync the partitions! I guess this is kind of a progress...

The problem is that I still not have access to Ubuntu from rEFIT. There is 1 icon for Mac OS X, and 2 from Linux (which I guess is unusual). The first says "Boot Linux from DD" and the second says "Boot Linux from Apple (which is the name of my Mac OS X partition).  

In both case, when I click the icon there is a black screen kind of terminal with a grub rescue line waiting for some commands... 

I guess I have to reinstall grub? I would greatly appreciate if someone can guide me in the process...

---

### Post by billybobby2010 on 2010-08-04
Ok. I found a tuto for installing grub2, then tried it, but it doesn t work. Here is what I did in terminal. Please help me with this:


ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26       21157   169738240   af  HFS / HFS+
/dev/sda3           21158       30040    71350272   83  Linux
/dev/sda4           30040       30402     2903040   82  Linux swap / Solaris

ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
mount: special device /dev/sda3 does not exist
ubuntu@ubuntu:~$ sudo mount /dev/sda4 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# grub-install /dev/sda
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
root@ubuntu:/# grub-update
grub-update: command not found
root@ubuntu:/# grub-install --recheck /dev/sda
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
root@ubuntu:/#

---

### Post by lefevre00 on 2010-11-01
Hye,

I had the same problem and succeed to reinstall grub2.

What I did is adding a new small bios-grub partition at the end of my disk. I've got
-sda1 : efi
-sda2 : osX
-sda3 : swap
-sda4 : /
-sda5 : /home
-sda6 : shared space between linux and osX
-sda7 : small bios-grub.

I created it with gparted, booting from the live-CD.
Then chrooting following the thread mentionned above, grub-install /dev/sda doesn't complain any more, and it's booting.

---

### Post by martine.ginette on 2010-11-16
Hi,

Can you detail the steps please?

Thanks,

Martin.

---

### Post by elzipa on 2011-11-01
lefevre,
could you specify how you did that procedure...I been trying to do it unsuccessfully.

I have a Mac with rEFIt installed and screwed all after I fixed Win 7 MBR... Mac OSX is working good and windows as well but Linux Ubunto does not show up.


I gparted as follows:

-sda1 : efi
-sda2 : 
-sda3 : 
-sda4 : Ubunto
-sda5 : Swap
-sda6 : Bios-Grub Partition ext3


Check erros below

Thanks for your help 



Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5fce6fb1

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      409639      204819+  ee  GPT
/dev/sda2          409640   136405135    67997748   af  HFS / HFS+
/dev/sda3       136669184   800729087   332029952    7  HPFS/NTFS/exFAT
/dev/sda4   *   800729088   898383871    48827392    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ sudo mount /dev/sda4 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot
Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only
be installed in this setup by using blocklists.  However, blocklists
are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.
ubuntu@ubuntu:~$

---


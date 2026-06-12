---
title: "How to add extended partion in GUID partition scheme"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by coolcatco888 on 2011-05-12
Hi,
I am not really sure if the title makes any sense or if it even possible.  Basically I am currently triple booting with Mac osx on the first partition windows 7 on the second and ubuntu linux on the 3rd with a swap partition.

So basically on my 2TB harddrive
Mac (200gb)
Windows (200gb)
Linux (200gb)
Swap (8gb)
NTFS(1592gb)

The last partition is formatted as ntfs using Gparted, windows cannot detect it.

The windows disk partitioner shows the swap and ntfs partitions as unformatted.  I can unformat the space and use the windows partition to add format it as ntfs but it would format the linux swap partition as well.  I am worried that it could potentially screw up everything on my harddrive.

My question is.  What do I need to do to get the ntfs parition recognized by windows (should I use the windows partitioner)?

Hope this makes sense, I'm bad at explaining things.

---

### Post by srs5694 on 2011-05-13
I'm glad you asked; you could have dug yourself into a deep, deep, deep hole!

Chances are you've got a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) which is an ugly and dangerous hack used by Apple to enable Intel-based Macs to dual-boot with Windows. In a hybrid MBR configuration, up to three of your real GUID Partition Table (GPT) partitions are duplicated in the Master Boot Record (MBR) partition table. (GPT and MBR are just two different ways of defining the same thing. They can sort-of coexist on one disk.) OS X and Linux both read the GPT partitions in this configuration, but Windows reads the MBR partitions. Because of the 3-partition limit, though, it's impossible to fit all five of your partitions in the hybrid MBR. (In fact, you've probably got six partitions, including an EFI System Partition that many utilities hide from view.) Most tools that create hybrid MBRs do so by blindly copying the data from the first three partitions (excluding the EFI System Partition). In your case, this is not the best thing to do; you want to copy your Windows and NTFS partitions into the hybrid MBR. You can do so with my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) utility; see the page on hybrid MBRs I referenced earlier for usage details. It's possible you'll need to re-install GRUB or the Windows boot loader when you finish with this, so be prepared for that possibility. Once you've made this change, don't run the gptsync utility or use the option in rEFIt to synchronize the GPT and the MBR (I've forgotten exactly what it's called). If you do, you'll lose your NTFS partition in Windows again, and you'll have to use gdisk's hybrid MBR option to get it back.

Do *not*, under *any* circumstances, attempt to use Windows to modify the disk's partitions! Do *not*, under *any* circumstances, attempt to create logical partitions on the disk! Either action will end up modifying the MBR data (which, as I've said, is just a copy of the *real* GPT data) without modifying the GPT data. The result will be inconsistencies between the GPT and the MBR that will almost certainly lead to lost data. If you use GParted on the disk, chances are you'll lose all the hybrid MBR entries and you'll need to re-create them with gdisk.

I realize all this is a pain. Complain to Apple for using such an ugly and dangerous hack rather than coming up with something better; and complain to Microsoft for not supporting Apple's variety of EFI, or at least supporting the ability to boot from GPT on BIOS-based computers (which is what a Mac seems to be in order to boot Windows).

---

### Post by coolcatco888 on 2011-10-25
Hey,

Wow, I know it's been a long time but I am too chicken to do it.  Anyways so I have it installed now.

Here is the output of the program:

```
cley@hackintosh:~/Downloads$ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with hybrid MBR; using GPT.

Command (? for help): p
Disk /dev/sda: 3907029168 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): CBC86EEB-C878-4C46-9963-120433EB0BED
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Partitions will be aligned on 8-sector boundaries
Total free space is 269477 sectors (131.6 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640       293378391   139.7 GiB   AF00  Mac OSX
   3       293642240       684265471   186.3 GiB   0700  WINDOWS 7
   4       684265472      1075085311   186.4 GiB   0700  LINUX
   5      1075085865      1087375589   5.9 GiB     8200  
   6      1087375590      3907024064   1.3 TiB     0700  

Command (? for help): q
cley@hackintosh:~/Downloads$ 

```

According to this the guide 
[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

I should type:
```
h
```
then
```
2 3 6
```
right?  (because 5 is my Linux swap and 6 is my EXT3 data drive, I decided to format it this way since both Windows and MAC OSX have EXT3 drivers)

Because this will NOT work since there is a 3 partition limit on the hybrid MBR?
```
1 2 3 4 5 6
```

Since you have experience with the tool, could you tell me if I am correct or shed more details on the exact commands I should be running?  Or whether or not there is a way to add extended partitions to the hybrid MBR (I doubt there is after a bit of reading).

I don't wanna screw things up.

But thanks so much for the advice!!!  Much appreciated!

---


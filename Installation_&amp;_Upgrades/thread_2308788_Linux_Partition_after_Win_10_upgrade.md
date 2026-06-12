---
title: "Linux Partition after Win 10 upgrade"
date: 2016-01-05
forum: Installation &amp; Upgrades
---

### Post by christian-pietzsch on 2016-01-05
I have ben searching for a lot of topics regarding my problem but most are esier fixable than mine.
After Win 10 Upgrade the dual boot was broken. Using the Live CD using gparted I noticed that the Linux partition was shown as unallocated. With testdisk i was able to recover it to ext4 and it shows that the partition is filled (so my data should still be there)
```
 sudo parted /dev/sda print
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  209GB  209GB   primary   ntfs            boot
 2      209GB   210GB  472MB   primary   ntfs
 3      210GB   498GB  288GB   primary   ext2
 4      498GB   500GB  2146MB  extended                  lba
 5      498GB   500GB  2144MB  logical   linux-swap(v1)

```
But if I mount it, there is almost nothing (just an lost&found folder). Testdisk also doesn't show anything more if I do quick search.
I deep searche there is another partition found but I allways the error: structure:bad
I used intel partition table structure. Might this be the problem?

---

### Post by oldfred on 2016-01-06
Intel is BIOS boot with MBR(msdos) partitions. 
Only if you have gpt whether UEFI or BIOS boot would you use the EFI/gpt option.

You are showing partition as ext2?

Windows major updates often do not write the Linux partition(s) back into partition table when MBR(msdos). 
Many have been able to restore with testdisk or parted rescue, but better to backup partition table first. And then data is normally correct. If data is correct then reinstall grub and it works.

A few have issues. 
Did you change size of Ubuntu partition more than once, so testdisk found multiple versions of partition table. It finds all the old versions also. 
Was Linux partition logical or inside extended partition originally? That  often is the case, but it looks like your restore partition is a primary partition.

 sudo parted /dev/sda unit s print
[http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

### Post by christian-pietzsch on 2016-01-06
thank you for your answer. Ill try it this evening
For the moment I used Photorec to get a lot of my data out of the partition (most files seem fine). But there are many duplicates and so an so it would be still pretty good if I could restore the partition.

---

### Post by oldfred on 2016-01-06
If a deeper search with testdisk works that may show files with names. Of course backups before a major upgrade are always the best choice.

When I used photorec, it also found the same file I edited and saved many times as it also found the deleted copies. It took forever to sort to find the same file and then compare all the versions to see which may be the newest.

---

### Post by christian-pietzsch on 2016-01-06
The problem is that Testdisk didn't find any files even using deeper search. so I think the chances of repairing aren't that high.
I couldn't imagine that Windows would muddle with partitions that don't belong to it. But ones more MS proved me wrong -.-

---

### Post by christian-pietzsch on 2016-01-07
```
sudo parted /dev/sda unit s print
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start       End         Size        Type      File system     Flags
 1      2048s       408680447s  408678400s  primary   ntfs            boot
 2      408680448s  409602047s  921600s     primary   ntfs
 3      409602048s  972580863s  562978816s  primary   ext2
 4      972580864s  976773119s  4192256s    extended                  lba
 5      972582912s  976771071s  4188160s    logical   linux-swap(v1)

lubuntu@lubuntu:~$ sudo parted
GNU Parted 3.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s                                                           
(parted) rescue                                                           
Start? 409602048                                                          
End? 972580862
(parted) 
(parted) rescue                                                           
Start? 409602047
End? 972580862
(parted)                                                                  
(parted) rescue                                                           
Start? 409602049
End? 972580862                                                         
(parted)                                                                  
(parted) rescue                                                     
Start? 409602049
End? 972580864
(parted)          

```

I can't get parted rescue to work. If I understood correctly it should find the partition if  insert start and endnumbers smaller than what is shown in the partition table. But it doesn't seem to find any. As you can see I also tried a few other combinations.
Do I do somehing wrong or are there other problems.

Thanks in advance for your patience.

edit: what I also don't understand is why parted shows it as an ext 2 (which I'm pretty sure isn't true) and in gparted it is shwon as ext4

---

### Post by oldfred on 2016-01-07
It is already showing the partition, so parted rescue cannot restore another into that space.

Not sure then if repairs to partition like fsck or others now may help or just create more issues.

---

### Post by christian-pietzsch on 2016-01-07
fsck says everything is fine:
```
sudo fsck.ext4 /dev/sda3
e2fsck 1.42.12 (29-Aug-2014)
Linux: sauber, 793404/17596416 Dateien, 18484801/70372352 Blöcke

```

edit: okay forcing recheck now

---

### Post by christian-pietzsch on 2016-01-07
getting multiply-claimed inodes.
```
Running additional passes to resolve blocks claimed by more than one inode...
Pass 1B: Rescanning for multiply-claimed blocks
Multiply-claimed block(s) in inode 4195819: 9377 9377 9377 9377 9377 9377 9377 9377 9377 9377 9377 9377 9377 9377
Multiply-claimed block(s) in inode 4196645: 9380 9380 9380 9380 9380 9380 9380 9380 9380 9380 9380 9380 9380 9380
Multiply-claimed block(s) in inode 4197513: 9381 9381 9381 9381 9381 9381 9381 9381 9381 9381 9381 9381 9381 9381
Multiply-claimed block(s) in inode 4197540: 9382 9382 9382 9382 9382 9382 9382 9382 9382 9382 9382 9382 9382 9382
Multiply-claimed block(s) in inode 4197563: 9383 9383 9383 9383 9383 9383 9383 9383 9383 9383 9383 9383 9383 9383
Multiply-claimed block(s) in inode 4197644: 9386 9386 9386 9386 9386 9386 9386 9386 9386 9386 9386 9386 9386 9386
Multiply-claimed block(s) in inode 4197669: 9387 9387 9387 9387 9387 9387 9387 9387 9387 9387 9387 9387 9387 9387
Multiply-claimed block(s) in inode 4197745: 9388 9388 9388 9388 9388 9388 9388 9388 9388 9388 9388 9388 9388 9388
Multiply-claimed block(s) in inode 4197828: 9390 9390 9390 9390 9390 9390 9390 9390 9390 9390 9390 9390 9390 9390
Multiply-claimed block(s) in inode 5377266: 9391 9391 9391 9391 9391 9391 9391 9391 9391 9391 9391 9391 9391 9391
Multiply-claimed block(s) in inode 5377268: 9392 9392 9392 9392 9392 9392 9392 9392 9392 9392 9392 9392 9392 9392
Multiply-claimed block(s) in inode 5377316: 9393 9393 9393 9393 9393 9393 9393 9393 9393 9393 9393 9393 9393 9393
Multiply-claimed block(s) in inode 5377334: 9394 9394 9394 9394 9394 9394 9394 9394 9394 9394 9394 9394 9394 9394
Multiply-claimed block(s) in inode 5377346: 9396 9396 9396 9396 9396 9396 9396 9396 9396 9396 9396 9396 9396 9396
Multiply-claimed block(s) in inode 5377366: 9397 9397 9397 9397 9397 9397 9397 9397 9397 9397 9397 9397 9397 9397
Multiply-claimed block(s) in inode 5768247: 9398 9398 9398 9398 9398 9398 9398 9398 9398 9398 9398 9398 9398 9398
Pass 1C: Scanning directories for inodes with multiply-claimed blocks
Pass 1D: Reconciling multiply-claimed blocks
(There are 16 inodes containing multiply-claimed blocks.)

File /lost+found/#4199281/4c08b4c70c5be7cb6c402efa92fdb6ee.png (inode #4195819, mod time Thu Aug 28 03:52:48 1969) 
  has 14 multiply-claimed block(s), shared with 0 file(s):
Clone multiply-claimed blocks<y>? 


```
I had that when I used it early and told it to fix it. Might have done more bad than good as you mentioned.```

```

---


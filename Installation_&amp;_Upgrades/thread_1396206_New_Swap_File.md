---
title: "New Swap File"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by jtuckerxo on 2010-02-01
Hi all,

This is my first post on the forums although I regularly search for help here.  Just want to say thank you to start.  This place has been a lot of help for me.

My Issue:
I want to move my swap file onto a new extended hard drive.

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1243     9984366   83  Linux
/dev/sda2            1244        1305      498015    5  Extended
/dev/sda5            1244        1305      497983+  82  Linux swap / Solaris

I want to put a 2Gb swap file on sda2.

> dd if=/dev/sda2 of=/mnt/2Gb.swap bs=1M count=2048
0+1 records in
0+1 records out
1024 bytes (1.0 kB) copied, 0.000388458 s, 2.6 MB/s

Why is this only copying 1.0kB?  Do I need to format the extended drive first? I have tried specifying the block size and count a number of different ways with the same results.

Any help would be greatly appreciated.

Thanks,
J

---

### Post by suseendran.rengabashyam on 2010-02-02
Hi,


       While creating the swap file, there is no need to copy the contents  from any existing partition. You will just need to fill zeros into the  swap file.
       

Please follow these steps to set up a new swap file:
       

1) Use the following command to create a file, where count=X defines  the file size in gigabyte blocks
       

```
sudo dd if=/dev/zero of=/mnt/swap_file bs=1024M count=X
```       2) Run mkswap to create the swap signature
       

```
sudo mkswap /mnt/swap_file
```3) Swap file can be activated immediately using the command
       

```
sudo swapon /mnt/swap_file
```       4) Make the following entry to your /etc/fstab so that your swap  file gets activated on boot


       ```
/mnt/swap_file swap swap defaults 0 0
```       Now if you wish to turn off the swap partition, in your case it is  /dev/sda5, you can do so by using


       ```
swapoff /dev/sda5
```       To permanently disable use of /dev/sda5 as swap, remove or comment  out the entries related to /dev/sda5 in your /etc/fstab file.
                   [URL="http://10.10.43.151:3000/issues/show/122#"]
[/URL]

---

### Post by jtuckerxo on 2010-02-02
Thank you for the great instructions Suseendran,

These would work fine normally, but I don't think you understand what I want to achieve.

I need the swap file to be located on the extended HD, /dev/sda2.

I would guess it would be something like /dev/sda2/2Gb.swap or something like that.

I am still having problems with the dd command.

Thanks,
J

---

### Post by jtuckerxo on 2010-02-02
Opps. seems /dev/sda2 is not the drive I added.  For some reason I thought it was.

I added a 4g HD onto my ubuntu VM.  My goal is to use the 4gb drive to put a 2gb swap on for now.

---

### Post by jtuckerxo on 2010-02-02
Ok so in some of my fooling around I tried to write something to /dev/sda2 using dd.

I think it was like:
dd if=/dev/zero of=/dev/sda2 bs=1024M count=2

Now when i run fdisk -l I get a problem with /dev/sda5 and it doesnt appear in the list.

>sudo fdisk -l
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000654cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1243     9984366   83  Linux
/dev/sda2            1244        1305      498015    5  Extended

Im really not very familiar with the way linux handles devices.  Any help or information about what is going on would be great.

Thanks,
J

---

### Post by jtuckerxo on 2010-02-02
Talking to myself here now....:)

Found the 4gb drive /dev/sdb after restarting.  Couldn't do a hot swap.

Here's what I have done:
fdisk /dev/sdb
n (new primary partition 1)
w (write)

dd if=/dev/zero of=/dev/sdb1 bs=1M count=2048

Now I want to do this but getting an error:
 mkswap /dev/sdb1
/dev/sdb1: Device or resource busy

Can anyone help me from here? Maybe I'm going about this the wrong way.

Thx,
J

---

### Post by suseendran.rengabashyam on 2010-02-03
Hi,


       SWAP space is a supplement to the system RAM. The SWAP space can be  in a Partition or you can use a file as a SWAP space.


       A SWAP partition will be created during the Ubuntu installation. If  you feel that the existing SWAP partition is not sufficient, you can  create a new SWAP file or you can create a new SWAP partition.


       There is no way to move around the SWAP file or SWAP partition, you  either turn it on or turn it off. Look at the man page of "swapon" for  the syntax.


       The instructions which I had given in my previous post was related  to creating a SWAP file, follow these instructions to create a new 2GB  SWAP partition:


       1) Enter the following command in the terminal:


       ```
sudo fdisk /dev/sdb
```A prompt will appear:
       

```
Command (m for help):
```       Entering "n" will create a new partition ( Do this )
Entering "p" will list out the partitions
Entering "d" will delete a partition


       Then enter "p" to create a new primary partition and enter a  partition number.
       

For First Cylinder enter the Default value and for last Cylinder  enter "+2G"
       

You will again get this prompt
       

```
Command (m for help):
```       Enter "w" to save and exit fdisk .


       2) The changes which you have made in the partition table needs to  be notified to the OS. So you need to enter the command


       ```
sudo partprobe /dev/sdb
```       3) Now you can create the SWAP signature using


       ```
sudo mkswap /dev/sdb1
```       If it is a different partition change sdb1 to sdb2 or sdb3 in  this step and also in the next few steps.


       4) The partition can be activated immediately using the command


       ```
sudo swapon /dev/sdb1
```       5) Make the following entry to your /etc/fstab so that your swap  partition gets activated on boot


       ```
/dev/sdb1 swap swap defaults 0 0
```       Try to be really careful while using the "dd" command otherwise you  will end up wiping your Ubuntu Installation. Please refer to [http://tldp.org/HOWTO/Partition/](http://tldp.org/HOWTO/Partition/)  to know more about the Linux Partitions.

---

### Post by jtuckerxo on 2010-02-03
Suseendran,

Thank you very much for your excellent instructions.  These worked perfectly except I had to perform a restart on the machine when I tried to do mkswap on /dev/sdb1.  

It was complaining again that the device was busy.

Thank you for taking the time to detail this process on Linux.  I've done this plenty of times on Windows based servers, but never on a nix.

-J

---

### Post by suseendran.rengabashyam on 2010-02-04
Hi,

Please mark the thread as solved so that it will be useful for others.

---


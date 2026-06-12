---
title: "Problems with GRUB after using HD as external USB HD for backup HELP!!!"
date: 2014-07-07
forum: Installation &amp; Upgrades
---

### Post by julianoys on 2014-07-07
Hi all,

I write this to ask some help to recover my Ubuntu system after disconnecting the HD from my laptop and using it with a USB HD Case to perform copies of some files.
When I reconnected it to my laptop, I got an error from GRUB, showing the GRUB Rescue prompt and showing the error "unknown filesystem".

I already tried some steps as in: [http://www.akkiri.com/dicas/grubrescue.php](http://www.akkiri.com/dicas/grubrescue.php) and [www.youtube.com/watch?v=jc_y7OYzXtQ]("http://www.youtube.com/watch?v=jc_y7OYzXtQ")
After issuing the insmod command, I get the unknown filesystem error again.

I used boot-repair application to generete the boot-info URL: [http://paste.ubuntu.com/7758631/](http://paste.ubuntu.com/7758631/)
But I could not use it to repair from live-cd... anyhow I am downloading the boot-repair CD to try applying the repair process.

In the meanwhile I was wondering if someone could help analysing the boot-info URL if maybe there is some more direct information and understand what happened to my hard disk...

REALLY SCARED TO LOOSE LOT'S OF INFORMATION!!!
PLEASE HELP!!!

Really appreciate any help!

Thanks and Br,

Juliano.

---

### Post by julianoys on 2014-07-07
I just used the boot cd for boot-repair and the button to apply "Recommended repair" is NOT shown...

Ahhh, some expert please! Really desperate, I can't loose data from this hard disk...

---

### Post by Bucky Ball on 2014-07-07
According to this:
```

=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
```

... you don't appear to have Ubuntu installed on that disk. Looks like it should be in sda5. What exactly did you do when you had it in the external case? Delete anything? sda5 should be EXT4 and it is showing 'Unknown filesystem type'. Not great.

Unsure where the 'Recommended repair' button is in Boot Repair. That sounds like something is awfully wrong. I suggest you boot from a LiveDVD/USB and install it that way, then launch and run. Second option here:

[https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

Don't know that will make much difference, though, because, as mentioned, I don't see a Ubuntu install on that drive. Boot from a LiveDVD/USB and have a look in Gparted, perhaps. See if that throws some light ...

Just a thought. What happens if you boot from Live media and run these commands:


```
sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
```

Does the disk mount at all? Please report any and all errors.

---

### Post by julianoys on 2014-07-07
Hi Bucky,

Here is what I did... maybe you can point out something stupid I did... and that now I regret a LOT!

I bought a new 1TB HD "B" to replace the current HD 250GB "A" I had with Ubuntu and several virtual machines running on it.
I disconnected the HD "A" and connected the HB "B" to the laptop. Then I installed Ubuntu to it. It was working fine, so next step would be to backup contents from HD "A" to a storage "C" I have and then copy back from "C" to "B".
However this would take some time and I though about skipping it... so I bought also a USB HD Case and I attached HD "A" to it and the plugged into the laptop with the drive "B" and the fresh Ubuntu running in it also.

It worked fine... it took some seconds, but then showed the USB Drive in the left task bar. I could even browse to the files.
It was late so I decided to continue the next day. I disconnected the drive and shutdown Ubuntu.

Next day I decided I should try Ubuntu 14.04 and reinstalled the HD "B" with new release of Ubuntu. At first usage, I did not like some of the looks and though it was a bit slower...
I think I had connected the USB Case with drive "A" to the laptop with this Ubuntu release also and it did not show the USB Disk icon anymore. I think I even tried mounting the disk manually, but was unsuccessful.
So I decided to go back and reinstall 12.02 back again.

But with the old Ubuntu release again, I tried connecting the USB Case with drive "A" and again it did not show the USB Disk icon. I tried mounting again unsuccessfully.
So as last resort, I took out the HD "A" from the USB case and attached to the laptop again and booted up.
Then I started receiving that "GRUB Rescue - Unknown Filesystem".

Rest of the history, you know already...

This is what happens when I try to mount the partition:

root@5T08ZN1:/media# mkdir sdb5
root@5T08ZN1:/media# mount /dev/sdb
sdb   sdb1  sdb2  sdb5  
root@5T08ZN1:/media# mount /dev/sdb5 /media/sdb5/
mount: you must specify the filesystem type
root@5T08ZN1:/media# mount -t ext4 /dev/sdb5 /media/sdb5/
mount: wrong fs type, bad option, bad superblock on /dev/sdb5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


root@5T08ZN1:/media# 

I used TestDisk ([http://www.opensourceforu.com/2012/05/how-to-recover-deleted-files-linux-1/](http://www.opensourceforu.com/2012/05/how-to-recover-deleted-files-linux-1/)) to try accessing the files directly, and this is what I get:

TestDisk 7.0-WIP, Data Recovery Utility, June 2014
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)


Disk /dev/sdb - 250 GB / 232 GiB - CHS 30401 255 63


     Partition                  Start        End    Size in sectors
  1 * Linux Swap               0  32 33  1215 203 12   19529728
  2 E extended              1215 235 43 30401  75 10  468862978
> 5 L Linux                 1215 235 45 30401  75 10  468862976

If I try to list contents from the logical unit, I get this:

TestDisk 7.0-WIP, Data Recovery Utility, June 2014
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)


 5 L Linux                 1215 235 45 30401  75 10  468862976


Can't open filesystem. Filesystem seems damaged.



For the logical unit, there is this option "Locate ext2/ext3/ext4 backup superblock", which gives me this:

TestDisk 7.0-WIP, Data Recovery Utility, June 2014
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)


Disk /dev/sdb - 250 GB / 232 GiB - CHS 30401 255 63


     Partition                  Start        End    Size in sectors


  Linux                 1215 235 45 30401  75 10  468862976
superblock 32768, blocksize=4096 []
superblock 98304, blocksize=4096 []
superblock 163840, blocksize=4096 []
superblock 229376, blocksize=4096 []
superblock 294912, blocksize=4096 []
superblock 819200, blocksize=4096 []
superblock 884736, blocksize=4096 []
superblock 1605632, blocksize=4096 []
superblock 2654208, blocksize=4096 []
superblock 4096000, blocksize=4096 []


To repair the filesystem using alternate superblock, run
fsck.ext4 -p -b superblock -B blocksize device



Do you think I should do it? I have no idea what it means...

Thanks again and Br,

Juliano.

---

### Post by julianoys on 2014-07-07
BTW, what I am interested now is to recover a Oracle VirtualBox Virtual Machine I use a LOT...
I don't care booting that HD anymore, but only the files!!!
I am not a Linux noobie, but I do have some experience with Linux... but I never handled deep down these GRUB, partitioning issues...

I though that using the original HD as external disk would not be a problem, but this is a nightmare!!!!
I do have a backup of my VM, but it is from end of last year... I have 6 months of data missing...

Really appreciate ANY help given!

---

### Post by sudodus on 2014-07-07
> **julianoys said:**
> ...

I used TestDisk ([http://www.opensourceforu.com/2012/05/how-to-recover-deleted-files-linux-1/](http://www.opensourceforu.com/2012/05/how-to-recover-deleted-files-linux-1/)) to try accessing the files directly, and this is what I get:

TestDisk 7.0-WIP, Data Recovery Utility, June 2014
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)


Disk /dev/sdb - 250 GB / 232 GiB - CHS 30401 255 63


     Partition                  Start        End    Size in sectors
  1 * Linux Swap               0  32 33  1215 203 12   19529728
  2 E extended              1215 235 43 30401  75 10  468862978
> 5 L Linux                 1215 235 45 30401  75 10  468862976

If I try to list contents from the logical unit, I get this:

TestDisk 7.0-WIP, Data Recovery Utility, June 2014
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)


 5 L Linux                 1215 235 45 30401  75 10  468862976


Can't open filesystem. Filesystem seems damaged.



For the logical unit, there is this option "Locate ext2/ext3/ext4 backup superblock", which gives me this:

TestDisk 7.0-WIP, Data Recovery Utility, June 2014
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)


Disk /dev/sdb - 250 GB / 232 GiB - CHS 30401 255 63


     Partition                  Start        End    Size in sectors


  Linux                 1215 235 45 30401  75 10  468862976
superblock 32768, blocksize=4096 []
superblock 98304, blocksize=4096 []
superblock 163840, blocksize=4096 []
superblock 229376, blocksize=4096 []
superblock 294912, blocksize=4096 []
superblock 819200, blocksize=4096 []
superblock 884736, blocksize=4096 []
superblock 1605632, blocksize=4096 []
superblock 2654208, blocksize=4096 []
superblock 4096000, blocksize=4096 []


To repair the filesystem using alternate superblock, run
fsck.ext4 -p -b superblock -B blocksize device



Do you think I should do it? I have no idea what it means...

Thanks again and Br,

Juliano.

I guess what happened is that you shut down the system too quickly (or removed the external drive too quickly) before it had flushed the buffered data to the disk.

Testdisk might succeed. Repairing the file system with might also succeed (I would say is likely to succeed).

***If you want to play safely***, clone the drive to another drive of at least the same size or clone the partition to another partition of at least the same size and located on another drive. You can use ***ddrescue*** for that task.

Then you can try different ways to repair the file system on the cloned copy.

Before trying the advanced method with explicit superblocks, I would try (booted from another drive and with the partition ***un***mounted)

```
sudo e2fsck -f /dev/sdxy
```

where x is the drive letter and y is the partition number.

---


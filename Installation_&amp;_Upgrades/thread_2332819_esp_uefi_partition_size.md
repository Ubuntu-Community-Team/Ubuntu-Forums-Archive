---
title: "esp uefi partition size?"
date: 2016-08-04
forum: Installation &amp; Upgrades
---

### Post by c_xy on 2016-08-04
Hello,

We are setting up the partition for our r730 dell server. We are installing Ubuntu 16.04.1 LTS server. This is a single operating system installation. Only Ubuntu 16.04.1 server LTS. No dual boot involved.

Storage capacity is Hardware RAID6 with 32 TB available (2 8 TB drives as spares). 

We are more familiar with BIOS but are now trying to install using UEFI mode.

In configuring the partitions, a separate ESP boot partition is required now. The other configured partitions will be ext4

However, we are unsure of what size to allocate to the partition given are planned setup. Looking online, we've seen recommendations from 150 MB minimum to  250 MB recommended.

What is the rule of thumb for the amount of space used for the ESP? 

Thank you.

c.

---

### Post by Dennis N on 2016-08-04
> However, we are unsure of what size to allocate to the partition given are planned setup. Looking online, we've seen recommendations from 150 MB minimum to 250 MB recommended.

What is the rule of thumb for the amount of space used for the ESP?

For Ubuntu family of distros, very little space is needed on the EFI system partition. In the details below for this machine, only 3.5 MB is used for the boot files in the ESP. The size for the partition was (probably) set at 520 MB during install, and that proved to be more than enough.

```
dmn@Sydney:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           383M  6.4M  377M   2% /run
/dev/sda5        27G   11G   16G  41% /
tmpfs           1.9G  164K  1.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
[COLOR="#FF0000"]/dev/sda1       511M  3.5M  508M   1% /boot/efi[/COLOR]
/dev/sda4       120G   49G   65G  43% /mnt/Common-Files
tmpfs           383M  4.0K  383M   1% /run/user/108
tmpfs           383M   40K  383M   1% /run/user/1000

```

On newer installations, I allow 80 MB so it can be used by other Linux distros as well in the future - the ESP depicted above currently contains files for only one OS. Use 500 MB if you have Windows in play.

---

### Post by oldfred on 2016-08-04
Part of reason for larger ESP is that is it difficult to resize as it is first partition on drive.
There are some that want the capability in the future to add things into ESP.
If not a server like yours, you might want rEFInd for a nice gui to dual boot.
And some very advanced configurations, can use UEFI to boot a kernel in ESP. I have not seen that other than some discussion that it is possible.

So I typically suggest 300MB which on new TB sized drives is not large. But as Dennis N points out the use of the ESP - efi system partition is normally very small.

The author of gdisk suggests 550MB.
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

---

### Post by c_xy on 2016-08-04
Thank you both for your replies. Both of your responses helped a great deal.

Thanks again.

c

---


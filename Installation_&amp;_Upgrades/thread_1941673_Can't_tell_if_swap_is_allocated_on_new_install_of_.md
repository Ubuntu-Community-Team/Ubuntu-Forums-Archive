---
title: "Can't tell if swap is allocated on new install of 11.10"
date: 2012-03-16
forum: Installation &amp; Upgrades
---

### Post by ToshibaLaptoplinux on 2012-03-16
Just noticed something quirky.

When I look at "top" in my terminal it shows the following,


Mem:   8105132k total,  1961136k used,  6143996k free,   222352k buffer
Swap:    15356k total,        0k used,    15356k free,  1039764k cached

Because I assigned 16MB to swap during the install, and did select "swap", and because none of it is apparently being used according to top, I took a look in gparted again and saw the following:

sda1 100.0 MiB ntfs Samsung quick boot partition
sda2 101.0 GiB ntfs Windows 7 OS (C)
sda3 (Extended)
---sda5 50.0GiB ntfs ([Windows D:];[Linux /Windows_D])
---sda6 190MiB ext4 /boot
---sda7 19.07GiB ext4 /
---sda9 740.37GiB ext4 /Home encrypyted

Unallocated 2MiB
sda8 15MiB Unknown
sda4 20.77GiB ntfs Samsung Recovery Partition

What is going on? Is swap allocated and recognized or not? How could this have happened and if it isn't recognized do I have to repartition from scratch because the unallocated sda8 precedes my encrypted HOME partition sda9? And why will it only let me expand the swap by 1MiB even though 2MiB are free preceeding it?

---

### Post by papibe on 2012-03-16
Hi ToshibaLaptoplinux.

I have 4Gb of RAM and at this very moment I'm running Firefox, Thunderbird, Pidgin, and 2 terminals. When I run top, I also see 'Swap:... 0k used'. It basically means that all my applications fit inside the physical RAM, so no swap it is needed so far.

I see that you have around 8Gb of RAM, so I wouldn't worry about not using swap.

In case you are really concern, check if the swap partition is being mounted on /etc/fstab. You should have a line like this:
```
# swap was on /dev/sda7 during installation
UUID=61d8bda3-2b03-4920-b9f3-99a3fa1c9f8d   none  swap    sw   0       0

```
Another thing you can do is check the kernel log to see if the swap partition is being mounted without problems:
```
dmesg | grep -i swap
```
The output should be something like this:
```
[   15.894542] Adding 3998712k swap on /dev/sda7.  Priority:-1 extents:1 across:3998712k 
```
I hope that helps.
Regards.

---

### Post by scruffyeagle on 2012-03-16
> **ToshibaLaptoplinux said:**
> Just noticed something quirky.
<snipped the rest...>


I suspect something went wrong during your installation. When I look at my HD using gparted, my swap partition shows up as a "linux-swap" filesystem. If yours isn't showing that as having that filesystem, then I suspect it wasn't properly formatted during the installation. I think you can correct that by selecting sda8 in gparted, and changing it's filesystem to become linux-swap.

That said, I think it would be smart of you to back up your data from sda9, then use part of that space to increase the size of your swap partition. (Back up your data from sda9, turn swap off, delete both sda8 & sda9, then re-create the partitions using new sizes to reallocate space from sda9 as part of sda8.) I've read that as a general rule, your swap partition size should be at least equal to your installed RAM for the sake of being able to put your system into Hibernation.  By that rule, your swap partition should be at least 4GB. In my case, I allocated 3GB for a 2GB RAM machine - plenty of extra space, for the sake of program data that might be hanging around there before calling for Hibernation. Once you've finished, and are satisfied that your swap is properly allocated & in use, then you can reload your data back into sda9.

It's possible that your OS is running a swap file, instead of using a swap partition. That would explain the discrepancy between swap space reported as existing, and swap-formatted partition not showing up as such in gparted.

The limitation of swap partition expansion is probably because of the partition map recordkeeping overhead on the disk.

Hope this was helpful...

---

### Post by scruffyeagle on 2012-03-18
> **ToshibaLaptoplinux said:**
> Just noticed something quirky.
<snipped the rest>


Whoops! I made a mistake. I just re-read the 2 posts preceding mine, and realized I mistook the other poster's stated RAM as being yours. Because of that, I need to correct what I wrote. You shouldn't be allocating just 4GB of space for the swap partion - you should be allocating at minimum 8GB to match the installed RAM in your machine. (I'd suggest allocating 10GB, just to be on the safe side.)

Sorry about the mistake. Good luck!

---

### Post by ToshibaLaptoplinux on 2012-03-23
Thanks for the replies.

The underallocation of swap space size was a brain fart on my part and will indeed require me to re-install. It was my intention to allocate 16GB.

It turns out that the reason gparted shows the allocated swap space as "unknown" is due to the fact that my file system is encrypted. When doing so apparently the swap space is encrypted as well, thus showing as "unknown". However I have been assured that is being used but not sure how one could verify that.

---

### Post by oldfred on 2012-03-23
To see use and reread papibe post above:

```
fred@fred-MavericDT:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3960       1108       2852          0        153        363
-/+ buffers/cache:        591       3369
Swap:         6000          [COLOR=Red]0[/COLOR]       6000


```If you have 8GB of RAM you only need 8GiB of swap if you are hibernating or planning on editing large videos while running every program you have. Some use no swap, many just assign some swap as a just in case. Someone commented that system boots a bit faster with some swap.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---


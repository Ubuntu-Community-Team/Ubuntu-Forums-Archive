---
title: "Ubuntu 13.04 on Asus K56CM (Intel Rapid + Flashcache SSD + Bumblebee)"
date: 2013-10-07
forum: Installation &amp; Upgrades
---

### Post by tupacsoul on 2013-10-07
Hi guys. After 2 days trying to create the perfect configuration for my Asus K56CM, I want to share a guide done by me with help of another guides like this: [http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)

My laptop configuration:
- Intel i5
- nVidia 635m Optimus
- 500Gb HD
- 24Gb SSD
- 6Gb Ram

I do this tutorial because my laptop came with Windows 8, and it uses Expresscache for SSD cache of the system. In linux, Expresscache is not supported, so I used Flashcache.

The configuration of this tutorial is going to be:
- Ubuntu 13.04
- Intel Rapid (for quick start)
- Flashcache (for ssd cache)
- Bumblebee (for nVidia Optimus cards)

Step 0: download the Ubuntu image you want to use. In my laptop I used Xubuntu 13.04 ([http://xubuntu.org/](http://xubuntu.org/))

Once downloaded, write it on an USB drive. I used LiLi to do it.

Step 1: Configure BIOS UEFI
- On start, press ESC until boot menu, then select System Setup.
- Go to Advance tab and on SATA operation, mark AHCI
- Go to Boot tab and un boot #1 select UEFI USB.
- Reboot

Step 2: preparing disk partitions.
- With the USB plugged, select Try ubuntu without installing.
This laptop came with 500Gb HDD and 24Gb SSD, so we are going to use HD to host the system and SSD to mount the cache and EFI.

I've used the next partitions for the SDA(HDD):
```
sda                      8:0    0 465,8G  0 disk 
&#9500;&#9472;sda1                   8:1    0   5,9G  0 part [SWAP]
&#9500;&#9472;sda2                   8:2    0 117,2G  0 part /
&#9492;&#9472;sda3                   8:3    0 342,7G  0 part 

```
And in SDB(SSD):
```
sdb                      8:16   0  22,4G  0 disk &#9500;&#9472;sdb1                   8:17   0   250M  0 part /boot/efi
&#9500;&#9472;sdb2                   8:18   0   5,9G  0 part 
&#9492;&#9472;sdb3                   8:19   0  16,3G  0 part 

```

- Open Gparted.
- Delete all partitions (this will erase all your data)
- In SDA make the next partitions:
-- 4Gb for SWAP
-- 120Gb for /
-- The rest for /home

- In SDB make the next partitions:
-- 256mb for EFI
-- 6Gb for Intel Rapid
-- The rest for Flashcache

Of course, you can change sizes as your thought.

- Download Gdisk. Open Terminal and:
```
sudo apt-get install gdisk
```
- Now we are going to select the disk to use Intel Rapid:
```
sudo gdisk /dev/sdb
type P and take the 6Gb disk number
type T and use the number taken before
As HEX CODE, use: [COLOR=#000000]D3BFE2DE-3DAF-11DF-BA40-E3A556D89593
[/COLOR]Confirm
Type W and confirm again
```

Step 3: Install Ubuntu

Now, Install Ubuntu. In the installation, you're going to be asked where to install. Select the next partitions:
- SDA1 as Swap
- SDA2 as /
- SDA3 as /home
- SDB1 as EFI

Then, finish the installation.

Step 4: Install flashcache for /home
Flashcache is used to cache any partition to powerboost your laptop, making not to write everytimes on HD. Our SSD is very small to cache all the system, so we are only goint to cache /home

- Install git and dev tools:
```
apt-get install git-core git build-essential dkms linux-headers-`uname -r` uuid-dev
```
- Clone the Flashcache git:
```
git clone https://github.com/facebook/flashcache.git
```
- Make install
```
cd flashcache
sudo make -f Makefile.dkms all boot_conf
sudo make install
sudo modprobe flashcache
sudo echo "flashcache" >> /etc/modules 

```
- Verify the installation:
```
dmesg | tail
```
- Activate root user for unmount /home
```
sudo su
passwd (AND SET A PASSWORD)
```
- Logout from Ubuntu and login as root
- Open Terminal and unmount /home
```
umount /home
```
- Create the flashcache for /home
```
lsblk (and sure which partition is going to be the cache)
blkid (and take the ID of /home partition)
flashcache_create -p back home_cached /dev/sdb3 /dev/disk/by-uuid/THEUUID
```
- Now set it to FSTAB. Comment the /home mounting and add:
```
# 
FLASHCACHE/dev/mapper/home_cached /home   ext4    defaults        0       2
```
- And now, we make a script to reload flashcache every reboot:
```
sudo nano /etc/init.d/flashcache.sh
```
- We put this:
```
#!/bin/sh#
flashcache_load /dev/sdb3
```

- Change the permissions:
```
sudo chmod +x /etc/init.d/flashcache.sh
```
- And we add to rc.local
```
sudo nano /etc/rc.local
```
```
#!/bin/sh -e#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


sh /etc/init.d/flashcache.sh


exit 0
```

- Now, only reboot. You will be caching.

Step 5: Installing bumblebee for nVidia Optimus

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia linux-headers-generic 
reboot
```

---

### Post by oldfred on 2013-10-08
Nice write-up.

But my question is what is the advantage of flashcache over just having entire / (root) in SSD? 
System files are accessed more than data files normally and you want the files used the most on fastest device.
And Linux caches recent activity in RAM so that is even faster than SSD.

---

### Post by tupacsoul on 2013-10-08
Yes, you have the reason, but 16gb of SSD for caching I think is too low for /. My goal was basically that Ubuntu boot so quickly than Windows 8, and with this configuration, i got it.

BTW, your suggestion is very interesting... i'll try in next installation :)

---

### Post by oldfred on 2013-10-08
Just for info, I have a full install in my SSD and all data on hard drive. My 64GB SSD is configured with 2 root partitions, once current install and one for future or test install. I keep /home inside / but have .wine with Windows version of Picasa in .wine which uses about 2GB and is growing. I had only 9GB used a few months ago.

Filesystem      Size  Used Avail Use% Mounted on
/dev/sde3        28G   11G   16G  41% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           791M  1.1M  790M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  128K  2.0G   1% /run/shm
/dev/sdd2       100G   38G   63G  38% /mnt/shared
/dev/sdd6        97G   49G   43G  54% /mnt/data

---

### Post by tupacsoul on 2013-10-09
> **oldfred said:**
> Just for info, I have a full install in my SSD and all data on hard drive. My 64GB SSD is configured with 2 root partitions, once current install and one for future or test install. I keep /home inside / but have .wine with Windows version of Picasa in .wine which uses about 2GB and is growing. I had only 9GB used a few months ago.

Filesystem      Size  Used Avail Use% Mounted on
/dev/sde3        28G   11G   16G  41% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           791M  1.1M  790M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  128K  2.0G   1% /run/shm
/dev/sdd2       100G   38G   63G  38% /mnt/shared
/dev/sdd6        97G   49G   43G  54% /mnt/data

Hmmmm... I'm going to try to install / on SSD and /home on HDD... but then, where to cache /home? I cache /home because all internet history and cache from chrome (for example), all personal configuration and all things saves there. My desktop is about 2 secs to load when i enter the password. It was my goal...

---

### Post by oldfred on 2013-10-09
I leave /home in / but have data in my hard drive. I then link data folders from data partition into my /home. I do move Firefox & Thunderbird to hard drive as I used to share same profiles with XP. The only reason my /home is 2GB is I have .wine with Picasa which is 1.5GB, so the hidden . files are small. I am pretty sure you could leave chrome in /home on SSD but may want to houseclean a bit more regularly and must then have all data on hard drive.

The main reason I split my /home is I mult-boot. Originally just XP so I have a NTFS data partition but then less XP and more different versions of Ubuntu so I have a Linux formatted data partition for all new data.

 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

### Post by archimede.29 on 2013-11-05
Hi Tupacsoul. I'm new here. I really appreciated your guide. I think it's very well written and understandable also by unexperienced like me. Anyway even if I planned many times of switching to a Linux distro on my ASUS k56cm, I always stopped because of a problem reported on many distributions, especially that using latest kernels, the high power usage. For now, with a battery wear level of about 10% (data from hwnfo64 portable) that correspond to about 38.6Wh, using windows 7 whith only 2 pdf opened with Adobe Reader, WiFi swithed off and the lowest brightness of the monitor I have about 3 hr and 50 minutes of autonomy. I'd lke to know if you noticed changes to battery autonomy passing from windows to xubuntu with the configuration you have described in your guide and if you know any solution to improve it.

---

### Post by epicfeil on 2013-11-07
Hello, i did read your guide (its fantastic) , what if i want to cache the root partition???  do i have to use a live cd?

---

### Post by tupacsoul on 2013-11-10
> **archimede.29 said:**
> Hi Tupacsoul. I'm new here. I really appreciated your guide. I think it's very well written and understandable also by unexperienced like me. Anyway even if I planned many times of switching to a Linux distro on my ASUS k56cm, I always stopped because of a problem reported on many distributions, especially that using latest kernels, the high power usage. For now, with a battery wear level of about 10% (data from hwnfo64 portable) that correspond to about 38.6Wh, using windows 7 whith only 2 pdf opened with Adobe Reader, WiFi swithed off and the lowest brightness of the monitor I have about 3 hr and 50 minutes of autonomy. I'd lke to know if you noticed changes to battery autonomy passing from windows to xubuntu with the configuration you have described in your guide and if you know any solution to improve it.

Sorry for my missing time. Yes, i've noticed very high consume on Linux, and I decided to turn back to W8 sadly :(

---

### Post by epicfeil on 2013-11-10
[COLOR=#333333][FONT=Lucida Grande]Here is what i did step by step :[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]1) apt-get install git-core git build-essential dkms linux-headers-`uname -r` uuid-dev[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]2) git clone [/FONT][/COLOR][https://github.com/facebook/flashcache.git](https://github.com/facebook/flashcache.git)

[COLOR=#333333][FONT=Lucida Grande]3) cd flashcache[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]sudo make -f Makefile.dkms all boot_conf[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]sudo make install[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]sudo modprobe flashcache[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]sudo echo "flashcache" >> /etc/modules (had to sudo -i for this one )[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Now theorically i have to set up wich partition has to be cached, and i want root to be cached, i suppose i cant unmount root from a running system, can i? [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]anyway this is the procedure : [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]- lsblk : take a look at partitions to be sure you are pointing to the right one[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]- blkid : get the ID of the partition to be cached[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]- final command : sudo flashcache_create -p back root_cached /dev/sda1 /dev/disk/by-uuid/f040e22a-8602-43c1-87e0-83e1703702ec[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Problem is root is in use so i cant do it, any suggestion ??[/FONT][/COLOR]

---

### Post by archimede.29 on 2013-11-10
> **tupacsoul said:**
> Sorry for my missing time. Yes, i've noticed very high consume on Linux, and I decided to turn back to W8 sadly :(

That's just what I was worried of. Thanks anyway! :)

---

### Post by dannyboy79 on 2013-11-14
> **epicfeil said:**
> [COLOR=#333333][FONT=Lucida Grande]Here is what i did step by step :[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]1) apt-get install git-core git build-essential dkms linux-headers-`uname -r` uuid-dev[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]2) git clone [/FONT][/COLOR][https://github.com/facebook/flashcache.git](https://github.com/facebook/flashcache.git)

[COLOR=#333333][FONT=Lucida Grande]3) cd flashcache[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]sudo make -f Makefile.dkms all boot_conf[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]sudo make install[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]sudo modprobe flashcache[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]sudo echo "flashcache" >> /etc/modules (had to sudo -i for this one )[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Now theorically i have to set up wich partition has to be cached, and i want root to be cached, i suppose i cant unmount root from a running system, can i? [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]anyway this is the procedure : [/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]- lsblk : take a look at partitions to be sure you are pointing to the right one[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]- blkid : get the ID of the partition to be cached[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]- final command : sudo flashcache_create -p back root_cached /dev/sda1 /dev/disk/by-uuid/f040e22a-8602-43c1-87e0-83e1703702ec[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Problem is root is in use so i cant do it, any suggestion ??[/FONT][/COLOR]

i believe you have to do it from a liveusb or livecd since you're correct, you can't do it for / of the system that's running.

---

### Post by dannyboy79 on 2013-12-08
thanks for this tutorial. i performed all the steps and when I rebooted I was getting a failure, it said it couldn't mount /home, here's the output from the terminal
[IMG]https://lh6.googleusercontent.com/-8IMHqKUNhGM/UqSwHut2o_I/AAAAAAAACUo/35iuL9SQSCk/w787-h590-no/IMAGE_22.jpg[/IMG]
so i looked at my fstab once again and I had the exact line that the tutorial shows, it was ```
FLASHCACHE/dev/mapper/home_cached /home   ext4    defaults        0       2
``` and when I googled around for fstab entries for flashcache entries i saw that people were just putting ```
/dev/mapper/home_cached /home   ext4    defaults        0       2
``` so I fixed up my fstab by removing "FLASHCACHE" and then i saved the file and then I hit ctrl-d to continue booting. All is well and I am using flashcache for my /home partition and WOW is it lighting fast. I ran some dd commands writing to a normal external usb 2.0 drive, writing to my / partition which is NOT cached and then finally writing to my /home partition.

Writing to / partition (ext4)
```
1000000+0 records in
1000000+0 records out
4096000000 bytes (4.1 GB) copied, 56.8478 s, 72.1 MB/s
```

Writing to /home (ext4 flashcache)
```
1000000+0 records in
1000000+0 records out
4096000000 bytes (4.1 GB) copied, 9.34889 s, **438 MB/s**

```

Writing to an external usb 2.0 drive (ext4)
```
1000000+0 records in
1000000+0 records out
4096000000 bytes (4.1 GB) copied, 118.532 s, 34.6 MB/s

```

That's AWESOME. Thanks for this guide!

---


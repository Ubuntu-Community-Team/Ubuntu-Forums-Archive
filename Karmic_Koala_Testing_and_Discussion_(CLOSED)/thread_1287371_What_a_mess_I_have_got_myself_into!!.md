---
title: "What a mess I have got myself into!!"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dunbrokin on 2009-10-10
I have 2 PCs, 1 (an old dell D610) I use for my weather station. I upgraded this one to Karmic using the upgrade facility. It had some early problems with accessing the net but now these are sorted out.

With my main PC I did a clean reinstall to take advantage of ext4 etc. The only problem now is that I cannot access the net to get any upgrades...so I am stuck!! It is a Dell Latitude E4300. I cannot access the net using cable or wireless....how can I get the latest downloads which will have fixed this connection bug?

---

### Post by agurk on 2009-10-10
Grab a [daily live cd](http://cdimage.ubuntu.com/daily-live/current/) and reinstall again?

---

### Post by dunbrokin on 2009-10-10
Thanks....you just might have saved my sanity....I owe you a cold one!

---

### Post by TrueTom on 2009-10-10
It is usually sufficient to boot from a LiveCD and chroot into the existing installation. Had to do that yesterday... :)

---

### Post by dunbrokin on 2009-10-10
> **TrueTom said:**
> It is usually sufficient to boot from a LiveCD and chroot into the existing installation. Had to do that yesterday... :)

How do you do that?....the latest daily will not work on my system for some reason...it gets as fare as Checking Battery State and then just dies.

---

### Post by ronacc on 2009-10-10
follow the instructions here [http://ubuntuforums.org/showthread.php?t=1156240&highlight=chroot](http://ubuntuforums.org/showthread.php?t=1156240&highlight=chroot)   then once you are in you can update .

---

### Post by slakkie on 2009-10-10
> **dunbrokin said:**
> How do you do that?....the latest daily will not work on my system for some reason...it gets as fare as Checking Battery State and then just dies.

Create a script.sh file, put the following code in it.

```

#!/bin/bash

mnt=/mnt/karmic-chroot
root_disk=/dev/sdb1
mnt_devices="proc dev dev/pts sys"

start() {
        sudo mkdir "$mnt"
        sudo mount $root_disk "$mnt"

        for i in $mnt_devices ; do
                sudo mount -o bind /$i "$mnt"/$i
        done

        sudo mv "$mnt"/etc/resolv.conf "$mnt"/etc/resolv.conf.orig
        sudo cp /etc/resolv.conf "$mnt"/etc/resolv.conf
        sudo chroot "$mnt" /bin/bash

}

stop() {
        for i in $mnt_devices; do
                sudo umount "$mnt"/$i
        done
        sudo mv "$mnt"/etc/resolv.conf.orig "$mnt"/etc/resolv.conf
        sudo umount "$mnt"
        sudo rmdir "$mnt"
}

$1

```

Executing it
```

# Make script executable
chmod +x script.sh
./script.sh start # To start chroot
./script.sh stop # To cleanup chroot

```

---

### Post by dunbrokin on 2009-10-10
~$ ./script.sh start 
[sudo] password for pj: 
mount: mount point /mnt/karmic-chroot/proc does not exist 
mount: mount point /mnt/karmic-chroot/dev does not exist 
mount: mount point /mnt/karmic-chroot/dev/pts does not exist 
mount: mount point /mnt/karmic-chroot/sys does not exist 
mv: cannot stat `/mnt/karmic-chroot/etc/resolv.conf': No such file or directory 
cp: cannot create regular file `/mnt/karmic-chroot/etc/resolv.conf': No such file or directory 
chroot: cannot run command `/bin/bash': No such file or directory

---

### Post by kansasnoob on 2009-10-10
To others, dunbrokin is trying to chroot into his Karmic to try and fix it. I was trying to help him here:

[http://ubuntuforums.org/showthread.php?t=1156240&page=3](http://ubuntuforums.org/showthread.php?t=1156240&page=3)

My instructions:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

From the other thread:

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3b53557

Device Boot Start End Blocks Id System
/dev/sda1 * 1 243 1951866 83 Linux
/dev/sda2 29186 30401 9767520 83 Linux
/dev/sda3 28943 29185 1951897+ 82 Linux swap / Solaris
/dev/sda4 244 28942 230524717+ 5 Extended
/dev/sda5 244 2675 19535008+ 83 Linux
/dev/sda6 2676 5107 19535008+ 83 Linux
/dev/sda7 5108 28942 191454606 83 Linux

Partition table entries are not in disk order

Disk /dev/sdc: 4005 MB, 4005527552 bytes
124 heads, 62 sectors/track, 1017 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Disk identifier: 0x0001e525

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 1017 3909317 c W95 FAT32 (LBA)
__________________

Still leaves me stumped. Do you just know what your partitioning/drive arrangement is?

Also curious what sdc is?

Let me reread everything and try and get my mind around this.

---

### Post by kansasnoob on 2009-10-10
OK, so you can boot into Karmic but just not get on the internet?

If so boot into Karmic and run the command:

```
df -H
```

**[COLOR="Red"]Sample output only[/COLOR]** (I can see that sda3 is /):

> lance@lance-desktop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
**/dev/sda3              6.3G   3.3G   2.7G  55% /**
udev                   1.1G   279k   1.1G   1% /dev
none                   1.1G   115k   1.1G   1% /dev/shm
none                   1.1G    95k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock
none                   1.1G      0   1.1G   0% /lib/init/rw
/dev/sda10              11G   3.0G   7.3G  30% /home


Anyway, if you can boot Karmic post that output.

Regarding that sdc drive, do you have any external drives plugged in, memory cards inserted????????

---

### Post by VMC on 2009-10-10
> **dunbrokin said:**
> ~$ ./script.sh start 
[sudo] password for pj: 
mount: mount point /mnt/karmic-chroot/proc does not exist 
mount: mount point /mnt/karmic-chroot/dev does not exist 
mount: mount point /mnt/karmic-chroot/dev/pts does not exist 
mount: mount point /mnt/karmic-chroot/sys does not exist 
mv: cannot stat `/mnt/karmic-chroot/etc/resolv.conf': No such file or directory 
cp: cannot create regular file `/mnt/karmic-chroot/etc/resolv.conf': No such file or directory 
chroot: cannot run command `/bin/bash': No such file or directory

Output ```
sudo fdisk -l
```. I'm not sure why, but that script has an arbitrary [FONT="Courier New"]sdb1[/FONT]. Do you even have [FONT="Courier New"]/dev/sdb1[/FONT]?

---

### Post by kansasnoob on 2009-10-10
VMC, this is his:

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3b53557

Device Boot Start End Blocks Id System
/dev/sda1 * 1 243 1951866 83 Linux
/dev/sda2 29186 30401 9767520 83 Linux
/dev/sda3 28943 29185 1951897+ 82 Linux swap / Solaris
/dev/sda4 244 28942 230524717+ 5 Extended
/dev/sda5 244 2675 19535008+ 83 Linux
/dev/sda6 2676 5107 19535008+ 83 Linux
/dev/sda7 5108 28942 191454606 83 Linux

Partition table entries are not in disk order

Disk /dev/sdc: 4005 MB, 4005527552 bytes
124 heads, 62 sectors/track, 1017 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Disk identifier: 0x0001e525

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 1017 3909317 c W95 FAT32 (LBA)

Didn't help me much.

**[COLOR="Red"]NOTE: That "df -H" later on is just a sample I posted.[/COLOR]**

sda1 would be my best guess, but I don't like to quess.

---

### Post by dunbrokin on 2009-10-10
pj@pj:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda2              9.9G   2.2G   7.3G  23% /
udev                   1.9G   418k   1.9G   1% /dev
none                   1.9G   209k   1.9G   1% /dev/shm
none                   1.9G    95k   1.9G   1% /var/run
none                   1.9G      0   1.9G   0% /var/lock
none                   1.9G      0   1.9G   0% /lib/init/rw
/home/pj/.Private      9.9G   2.2G   7.3G  23% /home/pj

At this stage, I am completely confused myself and don't know where to go from here....

---

### Post by kansasnoob on 2009-10-10
OK, you see in bold:

> pj@pj:~$ df -H
Filesystem Size Used Avail Use% Mounted on
**/dev/sda2 9.9G 2.2G 7.3G 23% /**
udev 1.9G 418k 1.9G 1% /dev
none 1.9G 209k 1.9G 1% /dev/shm
none 1.9G 95k 1.9G 1% /var/run
none 1.9G 0 1.9G 0% /var/lock
none 1.9G 0 1.9G 0% /lib/init/rw
/home/pj/.Private 9.9G 2.2G 7.3G 23% /home/pj

I now know that **/dev/sda2** is / (aka:root) so I know what partition to mount and [COLOR="Red"]chroot **from the live CD** to try and update, upgrade, or whatever[/COLOR]. Run each of the following commands:

```
sudo mount /dev/sda2 /mnt
```

```
sudo mount --bind /dev /mnt/dev
```

```
sudo mount --bind /proc /mnt/proc
```

```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
``` 

```
sudo chroot /mnt
```

Now you can run whatever commands needed (no sudo needed) like:

```
apt-get update
```

```
apt-get upgrade
```

When done running commands:

```
exit
```

```
sudo umount /mnt/dev
```

```
sudo umount /mnt/proc
```

```
sudo umount /mnt
```

That should work if you have internet from the live CD.

---

### Post by dunbrokin on 2009-10-10
Thanks for that...very clear and concise....

Ran through all the commands...got root but on apt-get update it died...timed out trying to connect to  nz.archive.ubuntu:80 (1.0.0.0) - connection timed out....unable to connect

---

### Post by kansasnoob on 2009-10-10
I'd change to the main server. Exit the chroot and reboot, then go to System > Administration > Software Sources and change the "Download from" to Main Server.

Then try again. There was a lot of trouble with the Australian server, maybe the NZ server also.

---

### Post by ronacc on 2009-10-10
can you reach anything from the chroot ? for example this forum ? if you can, try switching your archive to main and try again . and as a hint , in the future make a note of where you put your / and /home  especialy if you are multi boot , it saves confusion .

---

### Post by kansasnoob on 2009-10-10
If it turns out to be just an internet problem look here:

[http://ubuntuforums.org/showpost.php?p=8005139&postcount=12](http://ubuntuforums.org/showpost.php?p=8005139&postcount=12)

and here:

[http://ubuntuforums.org/showpost.php?p=8002349&postcount=7](http://ubuntuforums.org/showpost.php?p=8002349&postcount=7)

That happened about 2 weeks ago so it took me a while to dig it up.

---

### Post by ranch hand on 2009-10-10
I have DSL and had to do this a couple weeks ago myself.  Had trouble with not being connected.
```

start network-manager

```
was all it took to get me up and running.

---

### Post by dunbrokin on 2009-10-11
> **kansasnoob said:**
> If it turns out to be just an internet problem look here:

[http://ubuntuforums.org/showpost.php?p=8005139&postcount=12](http://ubuntuforums.org/showpost.php?p=8005139&postcount=12)

and here:

[http://ubuntuforums.org/showpost.php?p=8002349&postcount=7](http://ubuntuforums.org/showpost.php?p=8002349&postcount=7)

That happened about 2 weeks ago so it took me a while to dig it up.

could not get the first one to work....the second one worked after a fashion ....but keeps getting timed out....very frustrating...but thanks for the pointer.

I managed to get a new kernal downloaded using this method...but it did not really make much difference...and not this method has stopped working.

---

### Post by dunbrokin on 2009-10-11
> **ranch hand said:**
> I have DSL and had to do this a couple weeks ago myself.  Had trouble with not being connected.
```

start network-manager

```
was all it took to get me up and running.

Thanks...but made no difference in my case.

---

### Post by dunbrokin on 2009-10-11
> **ronacc said:**
> can you reach anything from the chroot ? for example this forum ? if you can, try switching your archive to main and try again . and as a hint , in the future make a note of where you put your / and /home  especialy if you are multi boot , it saves confusion .

Will do...thank you for your help.

---

### Post by dunbrokin on 2009-10-11
> **kansasnoob said:**
> 
```
sudo mount /dev/sda2 /mnt
```

```
sudo mount --bind /dev /mnt/dev
```

```
sudo mount --bind /proc /mnt/proc
```

```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
``` 

```
sudo chroot /mnt
```

Now you can run whatever commands needed (no sudo needed) like:

```
apt-get update
```

```
apt-get upgrade
```

When done running commands:

```
exit
```

```
sudo umount /mnt/dev
```

```
sudo umount /mnt/proc
```

```
sudo umount /mnt
```
.

Thank you very much for your very helpful suggestions and support..it is much appreciated...I will try this again....I had some luck earlier in downloading a new kernal with the

sudo /etc/init.d/networking restart
sudo apt-get update && sudo apt-get upgrade

suggestions....but the kernal does not seem to have improved things very much....the internet connection has gone from zero to very sporadic. I am using NM on the other machine and wicd on this one....I think wicd is managing to get through more often than NM...but is still far from perfect.

---

### Post by dunbrokin on 2009-10-11
> **kansasnoob said:**
> 
```
sudo mount /dev/sda2 /mnt
```

```
sudo mount --bind /dev /mnt/dev
```

```
sudo mount --bind /proc /mnt/proc
```

```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
``` 

```
sudo chroot /mnt
```

Now you can run whatever commands needed (no sudo needed) like:

```
apt-get update
```

```
apt-get upgrade
```

When done running commands:

```
exit
```

```
sudo umount /mnt/dev
```

```
sudo umount /mnt/proc
```

```
sudo umount /mnt
```
.

Thank you very much for your very helpful suggestions and support..it is much appreciated...I will try this again....I had some luck earlier in downloading a new kernal with the

sudo /etc/init.d/networking restart
sudo apt-get update && sudo apt-get upgrade

suggestions....but the kernal does not seem to have improved things very much....the internet connection has gone from zero to very sporadic. I am using NM on the other machine and wicd on this one....I think wicd is managing to get through more often than NM...but is still far from perfect.

---

### Post by dunbrokin on 2009-10-11
> **kansasnoob said:**
> I'd change to the main server. Exit the chroot and reboot, then go to System > Administration > Software Sources and change the "Download from" to Main Server.

Then try again. There was a lot of trouble with the Australian server, maybe the NZ server also.

Tried that...same problem....timed out.

---

### Post by kansasnoob on 2009-10-11
I've been thinking about this.

Are you able to connect to the internet using the live CD on that computer?

---

### Post by dunbrokin on 2009-10-11
> **kansasnoob said:**
> I've been thinking about this.

Are you able to connect to the internet using the live CD on that computer?

Yes I am....I think that there must be a bug in the kernel which affects Dell computers...because this one runs real slow after the upgrade and the other one now connects to the the net under Karmic (after I had installed medibuntu and a range of other stuff in the repository) but also runs very intermittently.

---

### Post by ranch hand on 2009-10-11
Well you could wait 4 hours and a new kernel update;-)

It does seem like they are coming in pretty fast.  I don't think they will slow down much real soon.

---

### Post by kansasnoob on 2009-10-11
> **ranch hand said:**
> Well you could wait 4 hours and a new kernel update;-)

It does seem like they are coming in pretty fast.  I don't think they will slow down much real soon.

The thing is, he doesn't seem to be able to update that computer with no internet.

I'm just trying to think - why if he has internet from the live CD - he can't get networking using the "sudo cp /etc/resolv.conf /mnt/etc/resolv.conf" part of chrooting that system.

It has me more than a bit boggled:confused:

---

### Post by kansasnoob on 2009-10-11
> **dunbrokin said:**
> Yes I am....I think that there must be a bug in the kernel which affects Dell computers...because this one runs real slow after the upgrade and the other one now connects to the the net under Karmic (after I had installed medibuntu and a range of other stuff in the repository) but also runs very intermittently.

Have you tried "cabled" connection rather than wireless using the chroot procedure?

I just know this can be sorted out. I might not be the one to get it done, but I feel there's something simple I'm overlooking.

---

### Post by dunbrokin on 2009-10-11
> **kansasnoob said:**
> The thing is, he doesn't seem to be able to update that computer with no internet.


It has me more than a bit boggled:confused:

Sorry, I should have posted as I went along....I can now get to the net without the live CD...but it only runs very sporadically. I have managed to update fully....but it still runs very very slowly.

To get to the net through Karmic, I installed medibuntu and some other stuff in the repository (why this should make a difference I do not know) and followed the bug fix of Sep 24th (the second one) referred to above.

But a hearty thanks to everybody for your help...it is much appreciated...now that I have some kind of net access my next problem is this!!

[http://ubuntuforums.org/showthread.php?p=8089361#post8089361](http://ubuntuforums.org/showthread.php?p=8089361#post8089361)

---

### Post by ranch hand on 2009-10-11
Mark this one as "solved" under "thread tools"

---

### Post by dunbrokin on 2009-10-11
> **ranch hand said:**
> Mark this one as "solved" under "thread tools"

Thanks for the reminder....will do.

---

### Post by dunbrokin on 2009-10-11
> **kansasnoob said:**
> Have you tried "cabled" connection rather than wireless using the chroot procedure?

I just know this can be sorted out. I might not be the one to get it done, but I feel there's something simple I'm overlooking.

Cable will not work with NM at present...it is greyed out and has the message - device not managed.

---

### Post by kansasnoob on 2009-10-11
It might also be helpful to others to know how you finally got connected.

---

### Post by dunbrokin on 2009-10-11
> **kansasnoob said:**
> It might also be helpful to others to know how you finally got connected.

See above where I say...

To get to the net through Karmic, I installed medibuntu and some other stuff in the repository (why this should make a difference I do not know) and followed the bug fix of Sep 24th (the second one) referred to above.

---

### Post by dunbrokin on 2009-10-11
The latest upgrade has sent me back to square one!!...none of the tricks I used the last time are working now....no internet again from the latest Karmic build.My pc is a Dell Latitude E4300....this may be part of the problem.

---

### Post by ranch hand on 2009-10-11
Can you get to the menu?  If so you should be able to boot to an older kernel, might work if you don't go too far back.

---

### Post by dunbrokin on 2009-10-11
> **ranch hand said:**
> Can you get to the menu?  If so you should be able to boot to an older kernel, might work if you don't go too far back.

Does not seem to be a kernel problem as I am using the same kernel on this PC....the only difference (apart from the model type - they are both Dell) is that this one has wicd installed the the other one (which is giving me the problem) has NM installed.....whether that is the difference or not, I don't know. The other one does start a download in starts and stops...currently it has dowloaded 370kb of a 1,661kb download and has now stopped dead!...and has been stopped dead for 5  minutes.

---

### Post by ranch hand on 2009-10-12
I now have DSL but up until about 6 months ago had never anything but dialup.

I can tell you that if you have a shakey connection the best thing to do is download through apt-get.  It seems to recover most gracefully and holds onto the packages better if you have to restart.  You may want to go to synaptic after that to pick up stuff that apt held back but that will be a lot smaller download.

---

### Post by VMC on 2009-10-12
> **dunbrokin said:**
> Does not seem to be a kernel problem as I am using the same kernel on this PC....the only difference (apart from the model type - they are both Dell) is that this one has wicd installed the the other one (which is giving me the problem) has NM installed.....whether that is the difference or not, I don't know. The other one does start a download in starts and stops...currently it has dowloaded 370kb of a 1,661kb download and has now stopped dead!...and has been stopped dead for 5  minutes.

Do you get any errors on pinging. For example:

```
ping google.com
```

---

### Post by nystire on 2009-10-13
Not really part of the on going discussion, but I had to mount an install with chroot to try and repair it with the whole 'apt-get update && apt-get dist-upgrade' routine, and there were many complaints that '/dev/pts' was not mounted. It may be worthwhile adding this to the list of the mounts which were given earlier on in this thread to be mounted with '--bind'.

---

### Post by ranch hand on 2009-10-13
+1

---


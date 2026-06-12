---
title: "Well, my grub disappeared!"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-10-24
Never thought it would happen to me as all was going good on this multi-boot system.
Ran updates this evening, and restart was required. Upon reboot, grub menu was present, so I updated the other 2 Ubuntu partitions. After all 3 ubuntu partitions were updated and reboot, I got the grub and selected  and was dumped to a command line login. After reboot a couple of times trying other partitions, I did a hard restart and was presented with the following message at the top of my screen every time I start my machine

[B]GRUB Loading.
error invalid arch independent ELF magic
grub rescue>[/B] and flashing cursor

Sorry, but I do not know how to handle this situation. 
I am using Jaunty live cd.
I have been using grub2 for quite some time with out any issues at all. When I installed it, all partitions were detected and all was working great.
Please any help would be great.

---

### Post by dino99 on 2009-10-24
hi,
you scared me !!!

i've done the upgrades too, but not the reboot !!! Maybe wait some time and see post on forum before rebooting.

In case, maybe this can help a little:

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

---

### Post by philinux on 2009-10-24
> **DougieFresh4U said:**
> Never thought it would happen to me as all was going good on this multi-boot system.
Ran updates this evening, and restart was required. Upon reboot, grub menu was present, so I updated the other 2 Ubuntu partitions. After all 3 ubuntu partitions were updated and reboot, I got the grub and selected  and was dumped to a command line login. After reboot a couple of times trying other partitions, I did a hard restart and was presented with the following message at the top of my screen every time I start my machine

[B]GRUB Loading.
error invalid arch independent ELF magic
grub rescue>[/B]

Sorry, but I do not know how to handle this situation. 
I am using Jaunty live cd.
I have been using grub2 for quite some time with out any issues at all. When I installed it, all partitions were detected and all was working great.
Please any help would be great.

This does the trick.
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by DougieFresh4U on 2009-10-24
> **philinux said:**
> This does the trick.
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

Thanks. 
I had gone to that and went through all the steps and get this:

```
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      204800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       18168   145724609+   7  HPFS/NTFS
/dev/sda3           18169       38913   166634212+   5  Extended
/dev/sda5           38067       38913     6803496   82  Linux swap / Solaris
/dev/sda6           20781       25447    37487646   83  Linux
/dev/sda7           25448       38066   101362086   83  Linux
/dev/sda8           18169       20779    20972794+  83  Linux

Partition table entries are not in disk order

ubuntu@ubuntu:~$ sudo mkdir /mnt/karmic
ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt/karmic
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/karmic/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/karmic/dev
ubuntu@ubuntu:~$ sudo mount -o bind /dev/pts /mnt/karmic/dev/pts
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/karmic/sys
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/karmic/etc/resolve.conf
ubuntu@ubuntu:~$ sudo chroot /mnt/karmic /bin/bash
chroot: cannot run command `/bin/bash': Exec format error
ubuntu@ubuntu:~$ 
```

Did I not follow it correctly? :confused:

---

### Post by dino99 on 2009-10-24
well, i've rebooted now & no trouble.

I've you recently used parted or gparted or partmagic ?

---

### Post by DougieFresh4U on 2009-10-24
OK, so sda7 is 64 bit, so I tried the sda6 and got in, ran updates and I end with this:
```
Fetched 10.3MB in 2min 1s (84.6kB/s)                                                                                                            
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

E: Could not open file /var/lib/dpkg/status - open (116: Stale NFS file handle)
E: The package lists or status file could not be parsed or opened.
root@ubuntu:/# sudo aptitude dist-upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (116: Stale NFS file handle)
E: The package lists or status file could not be parsed or opened.
root@ubuntu:/# sudo dpkg --configure -a
dpkg: failed to open package info file `/var/lib/dpkg/status' for reading: Stale NFS file handle
```

---

### Post by drs305 on 2009-10-24
DougieFresh4U

Try reverting to the backup status file:
```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status

```

---

### Post by DougieFresh4U on 2009-10-24
> **drs305 said:**
> DougieFresh4U

Try reverting to the backup status file:
```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status

```

Thanks, gives me this:
```
root@ubuntu:/# sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
mv: cannot stat `/var/lib/dpkg/status': Stale NFS file handle
root@ubuntu:/# 
```

---

### Post by philinux on 2009-10-24
I'd unmount all your stuff then go through the chroot process again.

[http://sysunconfig.net/unixtips/stale_nfs.txt](http://sysunconfig.net/unixtips/stale_nfs.txt)

Unmount in this order
sudo umount /mnt/karmic/proc
sudo umount /mnt/karmic/dev/pts
sudo umount /mnt/karmic/dev
sudo umount /mnt/karmic/sys
sudo umount /mnt/karmic

---

### Post by drs305 on 2009-10-24
The next step is to run an fsck on the partition. An easy way to set it up if you haven't tweaked the check interval is to use tune2fs to schedule it. This will put the max count above the limit and force a check on reboot: change the device if not sda6
```

sudo tune2fs -C 100 /dev/sda6

```
Reboot the computer.

---

### Post by DougieFresh4U on 2009-10-24
> **drs305 said:**
> The next step is to run an fsck on the partition. An easy way to set it up if you haven't tweaked the check interval is to use tune2fs to schedule it. This will put the max count above the limit and force a check on reboot: change the device if not sda6
```

sudo tune2fs -C 100 /dev/sda6

```
Reboot the computer.

Tried that, rebooted and still get
[B]
GRUB Loading.
error invalid arch independent ELF magic
grub rescue> (flashing cursor)[/B]

---

### Post by drs305 on 2009-10-24
> **DougieFresh4U said:**
> Tried that, rebooted and still get
[B]
GRUB Loading.
error invalid arch independent ELF magic
grub rescue> (flashing cursor)[/B]

Sorry I didn't make it clear. This was only fixing the "Stale NFS handle". You would still have to run the "dkpg" fix again. That should resolve your APT problem, but I'm not familiar with the ELF problem.

You could try manually entering the data via the Grub 2 command line, but I can't tell you what you might have to input there other than the standard entries:
[https://help.ubuntu.com/community/Grub2#Using%20CLI%20&%20Rescue%20Mode%20to%20Boot]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20&%20Rescue%20Mode%20to%20Boot")

ADDED: Getting the "grub rescue" prompt means that Grub2 either cannot find the grub.cfg file or that the file is not usable.

---

### Post by DougieFresh4U on 2009-10-24
Still getting the 'stale file' error.
I am downloading a daily 64 bit and gotta go out and get some DVD's in a bit. Gonna try installing on one of my partitions and see if it can find grub for me. Don't really know what else to try. I am sure there is some 'sudo' magic for the 'grub-rescue' messege I am getting, but just don't know what it is. 
Going to wait a bit for people to wake up and join the fun here at the forum this rainy cold morning here in New York state!! I am sure some one will have a good solution for me.

---

### Post by philinux on 2009-10-24
Dont forget that grub2 doesn't like being installed to a partition. 

You'll get the Bad Idea message but I've been running it like this for ages without a hitch. But forewarned is forearmed eh. :P

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/445416](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/445416)

---

### Post by DougieFresh4U on 2009-10-24
> **philinux said:**
> Dont forget that grub2 doesn't like being installed to a partition. 

You'll get the Bad Idea message but I've been running it like this for ages without a hitch. But forewarned is forearmed eh. :P

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/445416](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/445416)

Thanks for that. I recall seeing that messege one time a while back.
I am not sure where grub2 installed here. I have 2-64bit and 1-32 bit and Windows 7 installed here. . I have grub2 on all 3 Ubuntu partitons. I am pretty it's that way.Have had no problems until this. 
Thanks

---

### Post by DougieFresh4U on 2009-10-24
When I start machine and get:
[B]
GRUB Loading.
error invalid arch independent ELF magic
grub rescue> and flashing cursor[/B]

what could I possibly type to get any thing as it seems to be prompting for something? I have tried some 'usual commands' but get 'command not found'

---

### Post by autocrosser on 2009-10-24
You could try looking at this page for commands-- [http://grub.enbug.org/CurrentStatus](http://grub.enbug.org/CurrentStatus)  & the Wiki link could have the info you need---Luck my friend!!!

The other link is: [http://grub.enbug.org/CommandList](http://grub.enbug.org/CommandList)

---

### Post by drs305 on 2009-10-24
You can try typing "help" to see if it generates a list. If it doesn't, try "insmod normal" to see if it will load the normal G2 commands. 

To prevent scrolling off the screen: "set pager=1" - Don't know if it will work in rescue mode.

The rescue commands can be found here, as well as how to boot from the rescue prompt:
[https://help.ubuntu.com/community/Grub2#Using%20CLI%20&%20Rescue%20Mode%20to%20Boot](https://help.ubuntu.com/community/Grub2#Using%20CLI%20&%20Rescue%20Mode%20to%20Boot)

---

### Post by VMC on 2009-10-24
> **DougieFresh4U said:**
> 
[CODE]  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      204800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.

Have you checked why your getting this message?
> **dino99 said:**
> well, i've rebooted now & no trouble.
I've you recently used parted or gparted or partmagic ?
I'm not sure if dino was referrring to the above message when he asked the question, but I've heard reports that pmagic causes that error.

This this [link]("http://www.linuxquestions.org/questions/linux-newbie-8/partition-1-does-not-end-on-cylinder-boundary-282563/") completely on the subject. Not Ubuntu but addresses the situation.

---

### Post by DougieFresh4U on 2009-10-25
I have made some progress!!
I made a fresh cd and chroot into system, thanks to those that provided links and info, as it was very useful.
Ran updates and when I ran 'update-grub2' it listed all the kernels on this partition and then it said 'cannot find any more partitions'. There should have been 3 more. I rebooted system and it booted into the partition I had chroot in.I ran updates and then I did an update-grub2 and got this:

```
dougie@bit64party:~$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found linux image: /boot/vmlinuz-2.6.31-13-generic
Found initrd image: /boot/initrd.img-2.6.31-13-generic
Found linux image: /boot/vmlinuz-2.6.31-9-generic
Found initrd image: /boot/initrd.img-2.6.31-9-generic
Found linux image: /boot/vmlinuz-2.6.31-8-generic
Found initrd image: /boot/initrd.img-2.6.31-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Ubuntu 9.10 (9.10) on /dev/sda6
Found Ubuntu 9.10 (9.10) on /dev/sda8
done
dougie@bit64party:~$
```

Don't know why it didn't find then when I was using live cd.
I haven't work up the nerve to reboot yet as I am in no hurry to get dumped back into 'grub rescue>' mode.
I guess I can say the problem is partially settled. :) :confused:

---

### Post by autocrosser on 2009-10-25
Hang in there!!!! This is why we test---Yes??????

---

### Post by dino99 on 2009-10-25
> **DougieFresh4U said:**
> I have made some progress!!
I made a fresh cd and chroot into system, thanks to those that provided links and info, as it was very useful.
Ran updates and when I ran 'update-grub2' it listed all the kernels on this partition and then it said 'cannot find any more partitions'. There should have been 3 more. I rebooted system and it booted into the partition I had chroot in.I ran updates and then I did an update-grub2 and got this:

```
dougie@bit64party:~$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found linux image: /boot/vmlinuz-2.6.31-13-generic
Found initrd image: /boot/initrd.img-2.6.31-13-generic
Found linux image: /boot/vmlinuz-2.6.31-9-generic
Found initrd image: /boot/initrd.img-2.6.31-9-generic
Found linux image: /boot/vmlinuz-2.6.31-8-generic
Found initrd image: /boot/initrd.img-2.6.31-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Ubuntu 9.10 (9.10) on /dev/sda6
Found Ubuntu 9.10 (9.10) on /dev/sda8
done
dougie@bit64party:~$
```

Don't know why it didn't find then when I was using live cd.
I haven't work up the nerve to reboot yet as I am in no hurry to get dumped back into 'grub rescue>' mode.
I guess I can say the problem is partially settled. :) :confused:

That's make me remind some of my own problem:
I have 3 hdds with each a different distro owning their grub2, that way i have 3 independent hdd in case one fail.
What happen in that case:
- the "master" hdd (1rst booting) run fine all the upgrades on each hdd.
- if i make changes on the others hdd & run os-prober, update-grub2, every os is detected but finally the grub menu is not updated because we need to chainload each hdd with the others: actually grub2 don't do that automatically by itself. So, i need to reboot with the "master" and update-grub2 to have a real menu.

---

### Post by DougieFresh4U on 2009-10-25
> **autocrosser said:**
> Hang in there!!!! This is why we test---Yes??????
I still need to find out why grub broke.
Also when I was chroot into the system, I had errors about a broke cylinder on my Windows 7 partition. Is that why I am getting the warning flags in gparted?

---

### Post by autocrosser on 2009-10-25
I have been hearing problems with multi-boot and Win7...have you searched LP for bugs?

---

### Post by ranch hand on 2009-10-25
> **dino99 said:**
> That's make me remind some of my own problem:
I have 3 hdds with each a different distro owning their grub2, that way i have 3 independent hdd in case one fail.
What happen in that case:
- the "master" hdd (1rst booting) run fine all the upgrades on each hdd.
- if i make changes on the others hdd & run os-prober, update-grub2, every os is detected but finally the grub menu is not updated because we need to chainload each hdd with the others: actually grub2 don't do that automatically by itself. So, i need to reboot with the "master" and update-grub2 to have a real menu.
I beg to differ.  I boot sdb and my external from the menu on sdb22.  I do not now, nor have I ever, chainloaded anything.

---

### Post by ranch hand on 2009-10-25
> **DougieFresh4U said:**
> I still need to find out why grub broke.
Also when I was chroot into the system, I had errors about a broke cylinder on my Windows 7 partition. Is that why I am getting the warning flags in gparted?
I would boot to Win JerryLewis Pro and run a disk test from there for a second opinion.  

There could be a problem that has been detected, however, this is another new feature in 9.10 and it is possible that it is wrong.

I would check with something else to be sure.

---

### Post by DougieFresh4U on 2009-10-25
> **autocrosser said:**
> I have been hearing problems with multi-boot and Win7...have you searched LP for bugs?

I have had no problems with multi boot, surprisingly, but now all of a sudden theres this 'cylinder' problem with the windows partition, which I know nothing about....off to some more reading....

---

### Post by dino99 on 2009-10-25
hi ranch,

what i've descrided above is what i got each time; but unlike your install, mine is not tweaked at all: no custom, only basic install.

---


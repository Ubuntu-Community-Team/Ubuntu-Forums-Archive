---
title: "Step by Step Instructions--need to chroot into lucid to boot"
date: 2010-02-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2010-02-25
Can someone patiently walk me through the steps (as I have never chrooted before) into my system so I can restore a kernel so I can boot into my lucid system without having to completely reinstall my system twice?

Thank you.

---

### Post by sports fan Matt on 2010-02-25
Or at the very least let me see if I can just readd then try & update to see if it works so I do not have to reinstall twice :) I am running a karmic live cd if that helps.

---

### Post by VMC on 2010-02-25
```
#!/bin/bash
## copy 7 commands below then paste:
sudo mount /dev/sdaX /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount -o bind /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt/ /bin/bash
=============
Remove CHROOT
=============
#!/bin/bash
## Ctrl+d to exit chroot,
## copy 6 commands below then paste.
sudo umount /mnt/etc/resolv.conf
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt
```

I keep this file on my desktop for just that reason. I open with gedit copy & past into a terminal, as I stated above. When done you Ctrl+d to get out of the  chroot then copy & paste the second half to remove mounts.

---

### Post by sports fan Matt on 2010-02-25
I am looking through posts about chrooting.  I don't know.  I guess the fact I have access to a bare system and I'm pretty sure I can solve this easily, is driving me batty.

---

### Post by sports fan Matt on 2010-02-25
Thank you VMC:) I shall try this.

---

### Post by sports fan Matt on 2010-02-25
mount: special device /dev/sdaX does not exist

---

### Post by VMC on 2010-02-25
> **sox fan Matt said:**
> mount: special device /dev/sdaX does not exist

I'm sorry, that sd**X** is a substitute for the partition you need to chroot into. 

If its sda3, for example. change sd**X** to sda**3**.

Of course you know to use:

```
sudo fdisk -l
and
sudo blkid
```

to find out which one you want, unless of course you know already.

---

### Post by sports fan Matt on 2010-02-25
Yep..its on /dev/sda1 according to Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60053   482375691   83  Linux
/dev/sda2           60054       60801     6008310    5  Extended
/dev/sda5           60054       60801     6008278+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 

So i'd do sudo mount /dev/sda1 /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount -o bind /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt/ /bin/bash

Then add the latest kernel and then:
#!/bin/bash
## Ctrl+d to exit chroot,
## copy 6 commands below then paste.
sudo umount /mnt/etc/resolv.conf
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt

?

---

### Post by sports fan Matt on 2010-02-25
Do you have to know what the latest kernel is for lucid?
I am in root@ubuntu:/#

---

### Post by VMC on 2010-02-25
> **sox fan Matt said:**
> Do you have to know what the latest kernel is for lucid?
I am in root@ubuntu:/#

```
$ uname -r
2.6.32-14-generic

```

---

### Post by sports fan Matt on 2010-02-25
E: Couldn't find package 2.6.32-14-generic

Is it because im running from the live cd?  Im confused.

---

### Post by sports fan Matt on 2010-02-25
sudo apt-get install linux-headers-2.6.31-14 generic

It couldnt find it..how odd

---

### Post by VMC on 2010-02-25
> **sox fan Matt said:**
> sudo apt-get install linux-headers-2.6.31-14 generic

It couldnt find it..how odd

```
$ aptitude show linux-headers-2.6.32-14-generic
Package: linux-headers-2.6.32-14-generic
State: installed
```

---

### Post by sports fan Matt on 2010-02-25
So its there?  My concern is if I boot, it may not find a kernel.

---

### Post by sports fan Matt on 2010-02-25
I just restarted and it didnt work..:lolflag: What do i need to do to get it to boot with that kernel?

---

### Post by sports fan Matt on 2010-02-25
Generating grub.cfg ...
Found memtest86+ image: /boot/memtest86+.bin

There is no kernel...Can anyone help me get a kernel so i can upgrade & update grub?

---

### Post by kansasnoob on 2010-02-25
Look here:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Of course you'll have to substitute /dev/sda3 with the proper destination, but once you're there try:

```
apt-get install --reinstall ubuntu-minimal
```

```
apt-get install --reinstall ubuntu-standard
```

```
apt-get install --reinstall ubuntu-desktop
```

It's bailed me out many times :)

---

### Post by sports fan Matt on 2010-02-26
I'm in the mounted Directory (sda1)
When I ran: ubuntu@ubuntu:~$ sudo mount /dev/sdaX /mnt/
mount: special device /dev/sdaX does not exist
ubuntu@ubuntu:~$  sudo mount /dev/sda1 /mnt/
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount --bind /dev/pts /mnt/dev/pts
ubuntu@ubuntu:~$ sudo mount -o bind /etc/resolv.conf /mnt/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt/ /bin/bash
It got me to root@ubuntu:/#

I tried all of those and got: root@ubuntu:/# sudo apt-get install --reinstall ubuntu-minimal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 38 not upgraded, on every single command.

Distributor ID:	Ubuntu
Description:	Ubuntu lucid (development branch)
Release:	10.04
Codename:	lucid
But I have no kernel to boot to.

---

### Post by VMC on 2010-02-26
> **sox fan Matt said:**
> I'm in the mounted Directory (sda1)
When I ran: ubuntu@ubuntu:~$ sudo mount /dev/[COLOR="Red"]**sdaX**[/COLOR] /mnt/
mount: special device /dev/sdaX does not exist
ubuntu@ubuntu:~$  sudo mount /dev/sda1 /mnt/
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount --bind /dev/pts /mnt/dev/pts
ubuntu@ubuntu:~$ sudo mount -o bind /etc/resolv.conf /mnt/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt/ /bin/bash
It got me to root@ubuntu:/#

I tried all of those and got: root@ubuntu:/# sudo apt-get install --reinstall ubuntu-minimal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 38 not upgraded, on every single command.

Distributor ID:	Ubuntu
Description:	Ubuntu lucid (development branch)
Release:	10.04
Codename:	lucid
But I have no kernel to boot to.

How do you know your in /dev/sda1 ? I told you to change sdaX to the desired sda number. Once you have chrooted then run command '**df**', and make sure the dev shown is the one you want.

---

### Post by sports fan Matt on 2010-02-26
My bad, i was using the generic from earlier :) It should read:

In sda1 as described by here: sudo mount /dev/sda1 /mnt/

Now in root: root@ubuntu:/# If I ran a sudo apt-get install 2.6.32-14-generic, it's already installed, but if i unmount/get out of root, will it be?

---

### Post by VMC on 2010-02-26
I'm now at a loss of what the problem is. Your topic wanted to know more about using chroot. So the OS in question has never booted or what?

I have another thing for you to try. Get hold of boot_info_script and run it. You will have a file RESULTS.txt. bring that back here so we see what's what.

---

### Post by sports fan Matt on 2010-02-26
Sorry for that.  I thought that was the original problem.  The machine booted normally until i accidently deleted all the kernels in grub.  All that is remaining is the memtest.  When I however go to loook for those kernels (they show up) As 2.6.31-14.48, but I suspect they would show up using the live cd.  My ultimate question is the issue is I have no kernels to be able to boot into lucid

1).  Can I get the kernels from Lucid and put them in so after I chroot (to add them, (even though they say they are installed)

---

### Post by sports fan Matt on 2010-02-26
I do appreciate the patience, like I said this is where I am a complete newbie.

---

### Post by sports fan Matt on 2010-02-26
I'll check in tomorrow morning..If anyone has any ideas, feel free to try and help. =)

---

### Post by dino99 on 2010-02-26
> **sox fan Matt said:**
> I'll check in tomorrow morning..If anyone has any ideas, feel free to try and help. =)

follow VMC post, then you need of course to UPDATE and UPGRADE with the latest packages.
If you grub.conf has been wrongly modified or destroyed, then run:
grub-mkconfig, then update-grub.

At that time, you have an updated system, and can now "unmount" your chroot.
Take time to do this step by step and slowly, that's not so difficult :D

---

### Post by VMC on 2010-02-26
Ok I see your problem now. No kernel. Can you boot the cd and copy the /boot kernel and initrd files, since you can't seem to install using apt-get.

What's the output of "/boot" and /usr/src":

```
ls /boot
ls /usr/src
```

Try this:

```
apt-get install linux-386
```

---

### Post by sports fan Matt on 2010-02-26
ubuntu@ubuntu:~$ ls /boot
abi-2.6.31-14-generic     grub            System.map-2.6.31-14-generic
config-2.6.31-14-generic  memtest86+.bin  vmcoreinfo-2.6.31-14-generic
ubuntu@ubuntu:~$ ls /boot
abi-2.6.31-14-generic     grub            System.map-2.6.31-14-generic
config-2.6.31-14-generic  memtest86+.bin  vmcoreinfo-2.6.31-14-generic
ubuntu@ubuntu:~$ ls /usr/src
linux-headers-2.6.31-14  linux-headers-2.6.31-14-generic

---

### Post by sports fan Matt on 2010-02-26
Thank you to all especially VMC.  Now I have a working system and best thing yet..saved about an hour worth of reinstalling =)

---


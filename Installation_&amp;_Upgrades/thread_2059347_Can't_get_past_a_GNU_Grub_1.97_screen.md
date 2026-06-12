---
title: "Can't get past a GNU Grub 1.97 screen"
date: 2012-09-17
forum: Installation &amp; Upgrades
---

### Post by milkyjoe on 2012-09-17
I have the latest version of Ubuntu, on a windows 7 computer. I did some upgrades for windows and now every time I try to boot Ubuntu it brings me to a Gnu grub screen which I can't get past.

I've been reading solutions on this forum all day, and so far none has worked.

The two most common solutions, which I've retried in different ways which haven't worked are:

1. Replacing wubildr with an updated version.

2. Typing into gnu grub : 

> grub>ls 
grub>ls (hdX,Y)             #find ubuntu partition  
grub>insmod ntfs           #load ntfs module 
grub>set root=(hdX,Y)  
grub>ls $Boot                   #find BOOT partition's UUID 
grub>search --no-floppy --fs-uuid --set UUID   
grub>loopback loop0 /ubuntu/disks/root.disk   
grub>set root=(loop0)       #reset loop to loop0 
grub>linux /boot/vmlinuzxxxxxxxxx  root=/dev/sda5 loop=/ubuntu/disks/root.disk ro quiet splash    #load kernel 
grub>initrd /boot/initrd.imgxxxxxxxxxxxx where (hdX,Y) is either (loop0) (hd0,1) (hd0,2) or (hd0,3) -I've tried them all, none seem to work.

If you can't tell from my jargon in this post, I'm not the most computer savy person when it comes to linux so I'm completely lost in how to fix this. So any advice on what I've been doing wrong here, or any better solutions will be greatly appreciated.

---

### Post by bcbc on 2012-09-17
The most likely cause is some corruption of the root.disk. See [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

---

### Post by milkyjoe on 2012-09-18
Nope, no go. Did exactly what that link said and the problem is still there.

---

### Post by bcbc on 2012-09-18
Can you view the contents of the root.disk with this? [http://ext2read.blogspot.ca/](http://ext2read.blogspot.ca/)

Once you've downloaded an run it you can File, Open the \ubuntu\disks\root.disk file.

Or alternatively, from the grub prompt try the following. Note it should fail because this is mirroring what a normal boot does and since that fails there ought to be no difference. But it will indicate the point of failure:
```
search -s -f -n /ubuntu/disks/root.disk
loopback loop0 /ubuntu/disks/root.disk
probe --set=diskuuid -u $root
set root=(loop0)
linux /vmlinuz root=UUID=$diskuuid loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot

```

PS explanation of commands:
1. find the file /ubuntu/disks/root.disk on any partition and set that partition as root
2. Create a loop device loop0 on the root.disk
3. Get the UUID of the root partition
4,5,6. Set root to the loop device (wubi install) so we can load the kernel and initrd and boot from it

---

### Post by milkyjoe on 2012-09-18
OK here's what comes up:

> search -s -f -n /ubuntu/disks/root.disk 
loopback loop0 /ubuntu/disks/root.disk 
probe --set=diskuuid -u $root 
error: unknown command 'probe'
set root=(loop0) 
linux /vmlinuz root=UUID=$diskuuid loop=/ubuntu/disks/root.disk ro quiet splash 
error: unknown filesystem
initrd /initrd.img
error: You need to load the kernel first 
boot
error: no loaded kernel

---

### Post by bcbc on 2012-09-18
> **milkyjoe said:**
> OK here's what comes up:

Maybe probe was added with a later release of grub - in any case the problem is the 'unknown file system'. You need to fsck the root.disk.

Instructions are [here]("https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F").
Basically you need to boot from an Ubuntu USB or CD, and then mount the windows partition that contains the root.disk. Then fsck it.

For example, if the root.disk is on /dev/sda2:
```
sudo mount /dev/sda2 /mnt
sudo fsck /mnt/ubuntu/disks/root.disk
sudo umount /mnt

```
Then reboot and try again.

Of course you need to know what partition the root.disk is on. If you want help, go back to grub, run these commands and post the output back here:
```
search -s -f -n /ubuntu/disks/root.disk 
echo $root
```

---

### Post by milkyjoe on 2012-09-21
yep that isn't working either.

---

### Post by bcbc on 2012-09-21
what part isn't working?

---

### Post by milkyjoe on 2012-09-21
not sure, did what you said, everything went thru without an error. I go try to boot up ubuntu, and it's on that Gnu Grub screen still.

I'm just going to uninstall ubuntu, and reinstall. which means I lose a months worth of work, but that's what I get for not backing up I guess.

---

### Post by bcbc on 2012-09-21
Did you try ext2read?

Why don't you keep a backup of the root.disk and then you can recover it later?

When you ran fsck, what happened. If it said it was clean try forcing the check:
sudo fsck -fyv /mnt/ubuntu/disks/root.disk

Post the output so I can see what is happening?

---

### Post by robtygart on 2012-09-21
If your going to reinstall you can save some files by accessing the drive using a live CD...

---


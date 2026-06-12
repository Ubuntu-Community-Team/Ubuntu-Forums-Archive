---
title: "Unable to install Grub2"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by pwaugh on 2010-07-02
On my laptop, I was forced to reinstall Windows Vista, and then "reduce" the partition size to create an empty partition to install Ubuntu.  I had to uninstall a "recovery" partition to free up even more space, once I was sure Vista was properly installed.  I have recovery DVDs in case.

Anyway, I then proceeded to install from my Ubuntu DVD, but it failed to install Grub.  I complete the install and am trying to install Grub manually to allow a dual boot.

I boot from the live CD, and do the following after mounting the Ubuntu partition from Places:

```

ubuntu@ubuntu:~$ mount | tail -1
/dev/sda5 on /media/a6a3e0fd-ff99-4051-89f1-7cd5295b3360 type ext4 (rw,nosuid,nodev,uhelper=udisks)

```

and....


```

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/a6a3e0fd-ff99-4051-89f1-7cd5295b3360 /dev/sda
Installation finished. No error reported.

```

however, 

```

ubuntu@ubuntu:~$ cat /boot/grub/device.map
cat: /boot/grub/device.map: No such file or directory

```

meaning Grub did not configure a device map.

and...

```

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

```

Ideas?  I am stuck.

Patrick

---

### Post by darkod on 2010-07-02
What do you mean failed to install grub2? Any specific error messages?
If grub2 is not installed at all, it's more complicated to add it. The commands you executed would just install it onto the MBR of the hdd, but if it wasn't installed at all into the OS there will be no config files to work from.

---

### Post by oldfred on 2010-07-02
If you have booted from the liveCD you cannot just run sudo update-grub. I think it would attempt to rewrite data on the liveCD which obviously you cannot do.

I am not sure but I could not find device.map on my lucid install. It may not be required now.

---

### Post by pwaugh on 2010-07-02
> **darkod said:**
> What do you mean failed to install grub2? Any specific error messages?
If grub2 is not installed at all, it's more complicated to add it. The commands you executed would just install it onto the MBR of the hdd, but if it wasn't installed at all into the OS there will be no config files to work from.

That was the "specific" error message.

I did however find the grub2 stuff on the drive partition, in /media/blahblah/boot/grub

and, as you can see was able to run grub commands.  If I boot from the internal drive /dev/sda, I get a grub> prompt, but have no idea what to do from there.

---

### Post by darkod on 2010-07-02
The grub-install is not a specific grub command if that's what you meant. You should always be able to run that from live mode. Whether you have grub installed into your ubuntu partition is another matter.

In this case I think it's best to run the boot info script. Just follow the link in my signature. It will show more details about the boot process. Post the content of the results file as explained there.

---

### Post by pwaugh on 2010-07-02
> **darkod said:**
> The grub-install is not a specific grub command if that's what you meant. You should always be able to run that from live mode. Whether you have grub installed into your ubuntu partition is another matter.

In this case I think it's best to run the boot info script. Just follow the link in my signature. It will show more details about the boot process. Post the content of the results file as explained there.

I am unable to run gedit for an unknown reason as well....

---

### Post by darkod on 2010-07-02
sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab /boot/grub/core.img


What ever happened, grub2 did not get fully installed. Probably hence the message it failed. You don't have a grub.cfg created. You will have to chroot into your hdd install from live mode and try to create it.

It would be like:

sudo -i
mount /dev/sda5 /mnt
mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
chroot /mnt
grub-mkconfig (to create the config files)
grub-install /dev/sda
update-grub (just in case)
exit (to exit the chroot)
umount /mnt/sys
umount /mnt/dev
umount /mnt/proc

Restart. See if that helps.

---

### Post by pwaugh on 2010-07-02
I see it all mounts, but then:

```

root@ubuntu:/# chroot /mnt
-bash: /usr/sbin/chroot: Input/output error
root@ubuntu:/#

```

---

### Post by pwaugh on 2010-07-02
Hmmm finally chroot worked... now I get this:

```

root@ubuntu:/# grub-mkconfig
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
root@ubuntu:/#

```

---

### Post by darkod on 2010-07-02
Of course it is mounted, because you did mount it. I'm running out of ideas. And I don't have enough experience to troubleshoot this last error/message. :(

What about trying the update-grub instead of the grub-mkconfig. But somehow I think it will say the same about / not there.

---

### Post by pwaugh on 2010-07-02
Yeah, something seems seriously wrong.

I think I'm going to completely start over again, but instead of installing Windows Vista first, I'm going to use Ubuntu to partition the disk, and then install Vista to one of the partitions that way it can't screw up the drive.

Thanks for trying to help,

Patrick

---

### Post by darkod on 2010-07-02
If you are happy with the size of the vista partition right now, you can use the existing setup. First boot live mode again and use Gparted in System-Administration to delete the ubuntu partitions, sda5, sda6 and sda2. If sda6 has key symbol, right click and select Swapoff so you can delete it. Hit the green button to execute changes.

Leave the space as unallocated. Then start the installer and simply use Use Largest Available Free space option.

---

### Post by pwaugh on 2010-07-03
Was able to solve my problem, so I thought I'd post what I did/noticed.

I went ahead and started from scratch again and used my Vista recovery disks to once again install Vista first, after failing to succeed by installing Ubuntu first, as the recovery disks will only allow a completely new partition table.

After the Windows install, this time I did not connect and update immediately.  First, I immediately resized the primary Vista partition, leaving the small recovery partition at this point which is at the end of the drive and about 20 gigs.  Doing this resize immediately allowed me to reduce the size to about half the 300 Gig disk, rather than 170 Gigs.

Once the resize was complete, I then booted from the Ubuntu CD and choose install.  I then elected to do the manual partition.  I then deleted the partition at the end of the drive to make the second half of the drive completely open.

I then "Added" a new primary partition less 4000 MBs checking primary, and mount point of "/".  This left 4000 MB for swap, which I again elected to setup as a primary.

All went smooth from there, expect that once I installed, I was forced this time to connect over eth0 first to be able install the proprietary driver required for my wifi to work.  Somehow in the past I was able to get this off the CD and then connect without having to use the eth0 connection first.

But, I now have a dual boot Vista/Ubuntu system so that I can at last run iTunes and manage my iPhone.  I seriously chewed out Apple for not letting me use ubuntu, haha.

Patrick

---


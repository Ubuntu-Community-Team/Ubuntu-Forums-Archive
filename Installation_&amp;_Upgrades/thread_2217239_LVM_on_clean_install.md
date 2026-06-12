---
title: "LVM on clean install"
date: 2014-04-16
forum: Installation &amp; Upgrades
---

### Post by npinn001 on 2014-04-16
Hi,

So I've never worked with LVM before and I could do with a bit of help please. I'm going to install a setup like follows:

/boot  200MB
LVM partition (spanning rest of drive and a 1TB drive)
/        20GB
/home 50GB
Swap
/files   rest of drive (1GB+)

Questions are as follows:

1) Do I need the seperate boot partition?
2) Should i format the /files drive as something other than EXT4 - ZFS?
3) When I come to do a clean install of Ubuntu at next release, can I use the existing LVM setup and just format /boot and /root?

Thanks so much!

---

### Post by Double.J on 2014-04-16
Hi there!

used lvm with my red hat a little bit.

you do need a seperate boot. Just like btrfs, the bootloader requires a standard primary/logical partition in ext2-4 to hand over to. Lvm translation comes in with the kernel as i understand it.

You can format the partitions a while range of filesystems. Is there a reason to? For example you can make an ntfs partition inside an lvm, but windows can't read it. I stick with ext4, but then I don't need anything else.

As i say, i've not used an LVM to install ubuntu, but I've had an lvm on my system whilst installing ubuntu. In short an lvm aware installer such as fedora/red hat lets me read and modify my old lvm just like normal partitioning.

unfortunately I can't remember if ubiquity can read lvm's, sorry!

Jj

---

### Post by steeldriver on 2014-04-16
Hmm... are you sure about that? The standard 12.04 Server ISO happily allowed me to install without a separate /boot:

```

$ df -h
Filesystem             Size  Used Avail Use% Mounted on
/dev/mapper/t60p-root   89G  6.3G   78G   8% /
udev                   1.5G  4.0K  1.5G   1% /dev
tmpfs                  303M  396K  303M   1% /run
none                   5.0M     0  5.0M   0% /run/lock
none                   1.5G     0  1.5G   0% /run/shm
$
$ mountpoint /
/ is a mountpoint
$ mountpoint /boot
/boot is not a mountpoint

```

It uses the whole disk as a single PV/VG with LVs for /dev/mapper/*hostname*-root and /dev/mapper/*hostname*-swap

Not that there's anything wrong with a separate boot of course. Regardless, the "best" partitioning / configuration will depend what the box is going to be used for imho.

---

### Post by npinn001 on 2014-04-16
Thanks both. Its going to be for a server. I want to run VMs on a base install of Ubuntu so I can have a test box etc. 

I presume I can set up VMs on the storage of the LVM partitions.

---

### Post by sudodus on 2014-04-16
I think you need a separate boot partition, if you use *encrypted* LVM.

---

### Post by Double.J on 2014-04-16
> **steeldriver said:**
> Hmm... are you sure about that?

Nope! :D

Thanks for the correction - I've looked further into this now (I got very confused for a bit back then). Turns out my fedora 20 install has no seperate /boot (I used default partitioning) However my red hat which i partitioned myself does. I wondered if I made a mistake with the documentation, but no, my Red Hat uses grub .97 which does require a seperate boot.

Jj

---

### Post by steeldriver on 2014-04-16
Yes pretty sure there was a time (not too long ago) when both (unencrypted) LVM and RAID needed separate /boot partitions - something to do with initramfs "hooks" I think...

---

### Post by Double.J on 2014-04-16
It looks like REHL 6 does now use grub 2 also. Must have happened around 6.2/.3 and with suse also finally moved off of legacy grub, it's pretty safe to say the days of separate boot for lvm are over... Well except for suse which uses btrfs ;)

---


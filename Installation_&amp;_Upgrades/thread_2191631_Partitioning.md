---
title: "Partitioning"
date: 2013-12-03
forum: Installation &amp; Upgrades
---

### Post by hloupy on 2013-12-03
Hiya

I wonder if someone could help me out with a rather eccentrically partitioned PC which I have just inherited. 

It's running Ubuntu 12.04 and I'd like to keep that, and install Debian as a dual boot. I'd be able to do that from scratch but at the moment there's quite a few partitions to sort out and I'm rather baffled.

So, pic attached..

sda1 is where i'd like to place debian
sda2 is an extended volume featuring:
-sda7 which has ubuntu on it
-sda8 seems to be a small slice of nothing
-there's 7mb unallocated
-sda 5 is 2gb of nothing
-sda 6 is unknown
sda4 is recovery
and there's an extra 3mb unallocated

so what i'm thinking is to delete everything except sda1 and sda2, then partition sda1 to make a home, swap and root for debian, then compile the rest of the space into a storage disk for films. does that make sense? woudl the debian swap also function as swap for ubuntu? that's pretty much putting me at the edge of what i know, so i'd like some advice before i do it. other suggestions welcome.

thanks for any help!

---

### Post by papibe on 2013-12-03
Hi hloupy.

I would review both /etc/fstab of Ubuntu and Debian to see if there's something unusual mount for a particular purpose.

Could you post both fstab files?

Also in order to map the current mounts to actual partitions disks, could you also post the result of this command?
```
sudo blkid
```
Regards.

---

### Post by hloupy on 2013-12-03
hi papibe

thanks for the response. sorry if it wasn't clear, debian isn't installed yet. my plan was to put it in sda1.

here's the fstab for ubuntu, or at least the result when i did cat /etc/fstab:

# /etc/fstab: static file system information. 
# 
# Use 'blkid -o value -s UUID' to print the universally unique identifier 
# for a device; this may be used with UUID= as a more robust way to name 
# devices that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    nodev,noexec,nosuid 0       0 
# / was on /dev/sda7 during installation 
UUID=5c04098c-3fac-41a4-875f-0470ea352e0f /               ext4    errors=remount-ro 0       1 
# swap was on /dev/sda6 during installation 
#UUID=1d581e83-d281-4a74-bdd4-213502ca361c none            swap    sw              0       0 
# swap was on /dev/sda8 during installation 
#UUID=456d7806-a7c9-4bde-9d0c-73c9cc51af99 none            swap    sw              0       0 
/dev/mapper/cryptswap1 none swap sw 0 0 
/dev/mapper/cryptswap2 none swap sw 0 0 

and the result of sudo blkid:

/dev/sda1: UUID="e6b45a71-3b7a-4ee6-94a3-46d6f1c639ba" TYPE="ext4" 
/dev/sda4: LABEL="Recovery" UUID="2C88743C8874071C" TYPE="ntfs" 
/dev/sda5: UUID="d120000f-cb63-49f4-a8d9-665eab0949a9" TYPE="ext4" 
/dev/sda7: UUID="5c04098c-3fac-41a4-875f-0470ea352e0f" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="161391ad-d64e-4c18-8f76-e35dff9a5d06" TYPE="swap" 
/dev/mapper/cryptswap2: UUID="a8011bc0-d92c-4952-ad19-db27684a3ba7" TYPE="swap"

---

### Post by papibe on 2013-12-03
Thanks.

We discovered something interesting: the computer is set to use a custom encrypted swap partition.

Could you post the results of these commands?
```
swapon --summary

sudo cryptsetup status cryptswap1

sudo cryptsetup status cryptswap2
```
Regards.

---

### Post by fantab on 2013-12-03
Yes /dev/sda6 and /dev/sda8 are encrypted swap partitions. I wonder why... (perhaps 'papibe' or someone else might be able to explain, why).
Also not sure why you have an NTFS Recovery partition. It is probable that originally the laptop came with Windows, which was later removed. In such a scenario, I don't think 'Recovery' would work. If it doesn't work then there is no point in having it there.

Since the laptop is 'inherited', I would advice you to customize the whole HDD setup according to 'YOUR' needs. And REINSTALL 12.04. 
**In a default install the Distro that is installed last gets control of the GRUB... 

If I were you I would 're-format' the HDD by creating a new 'Partition Table' with Gparted and repartition the HDD to suit 'MY' needs:

```
/dev/sda**1** 20-25Gb **Primary** Ext4 *Ubuntu* '[COLOR=#b22222]**/**[/COLOR]'
/dev/sda**2 **20-25Gb **Primary** Ext4 *Debian* '**[COLOR=#b22222]/[/COLOR]**'
/dev/sda**3 **20-25Gb **Primary** Ext4 *Free* (just in case I want to install any other distro or Ubuntu flavor or version, later)
/dev/sda**4 **'All the remaining Gb' **EXTENDED**
/dev/sda**5 **4Gb **Logical** SWAP
/dev/sda**6 **'All the remaining Gb' **Logical** Ext4 (shared DATA partition between all distros. Later I would setup this partition to mount with /etc/fstab).
```

---

### Post by hloupy on 2013-12-04
hi papibe,

here's the results-

hamish@hamish:~$ swapon --summary 
Filename				Type		Size	Used	Priority 
/dev/mapper/cryptswap1                  partition	914428	25656	-1 
/dev/mapper/cryptswap2                  partition	908284	0	-2 

hamish@hamish:~$ sudo cryptsetup status cryptswap1 
/dev/mapper/cryptswap1 is active and is in use. 
  type:    PLAIN 
  cipher:  aes-cbc-essiv:sha256 
  keysize: 256 bits 
  device:  /dev/sda6 
  offset:  0 sectors 
  size:    1828864 sectors 
  mode:    read/write 

hamish@hamish:~$ sudo cryptsetup status cryptswap2 
/dev/mapper/cryptswap2 is active and is in use. 
  type:    PLAIN 
  cipher:  aes-cbc-essiv:sha256 
  keysize: 256 bits 
  device:  /dev/sda8 
  offset:  0 sectors 
  size:    1816576 sectors 
  mode:    read/write

---

### Post by hloupy on 2013-12-04
hi fantab

it's a desktop and yes it had an ancient version of windows and then my grandad put ubuntu on it

not sure why he encrypted the swap! i didn't know you could do that.

yes a friend also suggested wiping and starting again, i'm a bit loathe to do that since i've got ubuntu configured how i want it, but it might be the easiest solution ultimately. ubuntu is quite slow so perhaps a reinstall is in order.

> **fantab said:**
> 

```
/dev/sda**1** 20-25Gb **Primary** Ext4 *Ubuntu* '[COLOR=#b22222]**/**[/COLOR]'
/dev/sda**2 **20-25Gb **Primary** Ext4 *Debian* '**[COLOR=#b22222]/[/COLOR]**'
/dev/sda**3 **20-25Gb **Primary** Ext4 *Free* (just in case I want to install any other distro or Ubuntu flavor or version, later)
/dev/sda**4 **'All the remaining Gb' **EXTENDED**
/dev/sda**5 **4Gb **Logical** SWAP
/dev/sda**6 **'All the remaining Gb' **Logical** Ext4 (shared DATA partition between all distros. Later I would setup this partition to mount with /etc/fstab).
```

a shared data partition sounds great, thanks for the suggestion. so i guess the swap can be used by any distro, that's good to know.

---

### Post by fantab on 2013-12-04
Yes SWAP can be shared between distors. However, some distros forcefully reformat same SWAP partition thereby changing its UUID. Ubuntu does not. 
If Ubuntu was installed earlier, you'd notice delayed boot because Ubuntu is looking for SWAP with a different UUID. Finally you will boot Ubuntu but SWAP will not be in use.
The solution is to find the new UUID of SWAP partition with:
```
sudo blkid
```
and then replacing the old UUID with NEW UUID by editing /etc/fstab:
```
gksudo gedit /etc/fstab
```

...then all will be back to normal. 

I think Debian will force format SWAP. So it will be good idea to install DEBIAN first if you intend to dual-boot it with Ubuntu. If you don't then be prepared for the above fix.

---

### Post by oldfred on 2013-12-05
If you use one swap for multiple systems, you cannot hibernate as the other system may overwrite it. But hibernating is not recommended when dual booting anyway.

If you choose to install with encrypted /home, it automatically sets up swap as encrypted. Then you cannot share that swap.

You can backup /home which has all your user settings and data and copy that back with a new install. That way your configuration is saved.

---

### Post by hloupy on 2013-12-05
> **oldfred said:**
> 
If you choose to install with encrypted /home, it automatically sets up swap as encrypted. Then you cannot share that swap.


yeah i think i'm veering towards doing that

---

### Post by hloupy on 2013-12-05
> **fantab said:**
> I think Debian will force format SWAP. So it will be good idea to install DEBIAN first if you intend to dual-boot it with Ubuntu. If you don't then be prepared for the above fix.

cool thanks for that

---


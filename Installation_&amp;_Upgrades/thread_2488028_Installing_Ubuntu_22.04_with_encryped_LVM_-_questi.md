---
title: "Installing Ubuntu 22.04 with encryped LVM - question about swap"
date: 2023-06-20
forum: Installation &amp; Upgrades
---

### Post by user1397 on 2023-06-20
I've installed Ubuntu 22.04 on my laptop with the default Erase and install Ubuntu option, with the encrypted LVM box ticked.  It gave me this:
```
NAME                  MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINTS
nvme0n1               259:0    0 238.5G  0 disk  
&#9500;&#9472;nvme0n1p1           259:1    0   512M  0 part  /boot/efi
&#9500;&#9472;nvme0n1p2           259:2    0   1.7G  0 part  /boot
&#9492;&#9472;nvme0n1p3           259:3    0 236.3G  0 part  
  &#9492;&#9472;nvme0n1p3_crypt   253:0    0 236.3G  0 crypt 
    &#9500;&#9472;vgubuntu-root   253:1    0 234.4G  0 lvm   /
    &#9492;&#9472;vgubuntu-swap_1 253:2    0   1.9G  0 lvm   [SWAP]
```

Question is, why does this option default to a swap partition and not just a swap file on the root volume, just like the default for the non-encrypted ext4 install option.  My understanding is swap files are a bit more flexible and I've generally liked them over swap partitions for a while (love how Ubuntu defaults to swap files as of several releases ago).  But I am not sure if in the case of an encrypted LVM setup, if there is something that wouldn't work with a swap file vs a swap partition.  Or, if I DO want to change to a swap file, what is the best way to go about that.

None of this is urgent or really matters all that much, more just curious than anything :)

---

### Post by TheFu on 2023-06-20
Those aren't partitions. They are logical volumes, which are extremely flexible.

First thing I'd do immediate after the install is to boot from the Install ISO, go into Try Ubuntu mode, and reduce the side of the "root" LV from 234G to 35G.  Then you'll have much more flexibility to use LVM to tremendous advantage.  Avoid allocating all the storage, especially for SSDs. Allocate only the storage you actually need for the next few months.  BTW, you probably want to create a "home" LV to mount /home onto and should seriously consider doing the same for /var and /tmp to improve system security.

Use these commands to see how LVM is being used:
```
sudo pvs
sudo vgs
sudo lvs
```
They output summaries for the physical volumes, volume groups and logical volumes that are used by LVM.

While you can setup a swap file, I wouldn't.  Using LVM has 20+ yrs of enterprise use and proof that it is stable. Swapfiles under Linux are fairly recent and don't handle all the situations, plus there's the overhead of dealing with a file system which an LV doesn't have.

I prefer using LVs.

BTW, there are lots of good options for the **lsblk** command.  Please setup an alias with the options you find useful. It isn't like the MAJ:MIN, RM,  RO columns are any use to anyone, so why bother with them when there are others that ARE extremely useful.  For example, 
```
alias lsblk='lsblk -e 7 -o name,type,size,FSAVAIL,FSUSE%,fstype,mountpoint'
``` is much more useful.

---

### Post by MAFoElffen on 2023-06-21
The practical method for that is sort of same thing with ZFS-on-Root, and BTRFS-on-Root, except as a separate encrypted pool or container (partition).

The reason why(?) It's an encryption security matter... If you have an encrypted root, then it is assumed that everything involved with it should be encrypted, including the swap partition. If it were not encrypted, then intruders could see what was happening by looking at the swap contents, which may give hints into decrypting the root.

You say fine, then why not just use a swap file inside the root LUKS container? (Which you just asked...) Because when you do an LVM2, ZFS, or BTRFS snapshot, you should exclude the swap... For the same reason that you exclude swap in backups. It is useless for most people to keep copies of, and it just will take up room that can be used for more useful purposes. That is hard to do that if it is a physical file inside of the root container...

Does that make sense now?

---

### Post by TheFu on 2023-06-21
> **MAFoElffen said:**
>  
Does that make sense now?

Not including a swap in the snapshot is an excellent point.  Swap definitely needs to be encrypted.

Extending an existing LV is trivial and fast. It doesn't require rebooting or bringing the system down.  While the system runs at full speed, use
```
sudo lvextend  -r -L +10G /dev/{path/to/LV device or link} 
``` 
With ext4, regardless of the size increase, it will finish in 2-5 seconds.  That's the power of LVM.
BTW, I practice this myself.  Here's a fresh install with LVM (not encrypted). Note how much empty space there is:
```
NAME                              SIZE TYPE FSAVAIL FSUSE% FSTYPE      MOUNTPOINT
nvme0n1                         931.5G disk                            
&#9500;&#9472;nvme0n1p1                         1M part                ext2        
&#9500;&#9472;nvme0n1p2                        50M part   43.9M    12% vfat        /boot/efi
&#9500;&#9472;nvme0n1p3                       700M part  342.6M    42% ext4        /boot
&#9492;&#9472;nvme0n1p4                     930.8G part                LVM2_member 
  &#9500;&#9472;vg01-swap01                   4.1G lvm                 swap        [SWAP]
  &#9500;&#9472;vg01-root01                    35G lvm      26G    19% ext4        /
  &#9500;&#9472;vg01-var01                     20G lvm    16.2G    12% ext4        /var
  &#9500;&#9472;vg01-tmp01                      4G lvm     3.7G     0% ext4        /tmp
  &#9500;&#9472;vg01-home01                    10G lvm       4G    53% ext4        /home
  &#9500;&#9472;vg01-libvirt--01              137G lvm     2.8G    98% ext4        /var/lib/libvirt

```
even with all those LVs for special uses, I've setup less than 50% for use by the system.  It is about flexible use and LVM makes that possible, since I've never guessed correctly where storage will be needed a year from now.

---

### Post by user1397 on 2023-06-21
Thanks for all the explanations gentlemen, some good tips in here.  I also saw in the arch wiki swap page there was a link to a Linus Torvals mailing list message where he seems to dispute the use of swap files altogether, makes me wonder now why Ubuntu went with that for the default non-encrypted ext4 auto format option.  It does seem like most other distros still use swap partitions...hmm

Anywho, thanks again for the tips!

---


---
title: "Full disk encryption on Natty"
date: 2011-07-21
forum: Installation &amp; Upgrades
---

### Post by graemev on 2011-07-21
I tried to post this on the WIKI, but could not seem to add pages...

Anyhow I wrote the following , as I discovered HOWTO  use the so called full disk encryption on Natty:

(I'll attach it as a text file also so you can just download that)

----------------------- cut here --------------------------
25-Jun-2011: Graeme Vetterlein.

I need to install "Full disk Encryption" on my office laptop.  I'm about to get
a new laptop, so this becomes urgent. 

Turns out FULL DISK ENCRYPTION is not what is seems, typically it's 'partition
encryption' . That said, I suspect FULL DISK encryption is possible, just not
for the initial (or only disk) as it needs to boot.

First off it's worth pointing out I'm coming to this late. There is a lot of
history relating to this. As a consequence much of what you find on the web is
historic and relates earlier attempts. Since change is the only constant, this
will be true of this information also, so all I can say is this is what we find
now.

Next the actual encryption. Much human effort has been expended here, there will
be some complex mathematical based algorithm able to translate cipher-text back
and forth to clear-text.  I'm going to skip all discussion of the algorithms.

So the basic trick is to have in your possession a 'volume' containing some
cipher-text and a key to decode it. When decrypted the clear-text is a filesystem or
similar.

What is the volume? :
------------------

Current flavour of Linux naming has things like:

    /dev/sda  -- 1st Hard Disk
    /dev/sdb  -- 2nd hard disk
    /dev/sda1 -- 1st (of up to 4**) primary partition on 1st hard-disk 
    /dev/sda5 -- 1st Logical on 1st hard-disk (Logical partitions are subdivisions INSIDE a primary)

All these are volumes. They are block devices, basically a large array of 512
byte blocks of data.
(**for fdisk style partition tables, with GUID Partition Table (GPT) this limit is lifted)

What goes into a volume? :
-----------------------

Well it could just be a very large block of text, but that's unlikely. Normally
you might find a 'filesystem' (e.g. ext3 , fat16 etc). Another possibility would
be am LVM physical volume. LVM further subdivides 'stuff' into volumes.

A maze of twisty passages all the same...
-----------------------------------------

So starting at the top:   TBD this oversimplifies !!!

   We have a volume (say /dev/sdb)
      Inside this volume we have primary partition (/dev/sdb3)
          Inside this we have a logical partition (/dev/sdb7)
             Inside this we have a Physical Volume, making part (or all) of a "volume group"
             Inside this volume group we have a logical volume , (/dev/vg1/home)
            Inside this logical volume we have a FILESYSTEM (e.g. ext4) LABEL=home


So at any of these levels (and we probably don't have them all) we may choose to
encrypt. So we might encrypt /dev/sdb3 . This would make /dev/sdb3 the cipher-text
and when it was decrypted to produce say /dev/sdb3.clear THAT would contain a
logical partition (/dev/sdb7). Right now I don't believe this is currently
implemented as it would have to exist in the disk driver.


Many ways to skin a cat
-----------------------

So what we are trying to do is insert and extra layer in the above volume
hierarchy. An M$ type approach might be to have some special program which
was need to 'understand' the cipher-text. On Linux/Unix however we tend to choose
a more generic approach. Two, which seem to have been used here include (chronologically):

  + Loopback
  + Device mapper

Loopback: [ LOSETUP(8) ] is a mechanism to allow a 'file' to appear as a device to
the Linux kernel (since a file exists on a filesystem, we are looping back,
going through the filesystem drivers twice). A common use of this is to allow a
CD/DVD ISO (image) to be mounted. The losetup(8) command has an option -E
(encryption) to allow encryption/decryption between the file and device. This is NOT
the scheme we are using today, so this ends my discussion (and knowledge) of it.

Device Mapper: Normally seen in conjunction with Logical Volume Manager (LVM2)
or Software Raid. Similar to loopback, except this maps a block device (like our
volumes) to another device. BTW it looks like cryptoloop can use device mapper,
again this is NOT what I'm discussing. 

In the crypto arena the weapon of choice is cryptsetup(8). This sets up the
mapping between the cipher-text volume and the clear-text volume. e.g:

    # cryptsetup create   cryptnattylvm  /dev/sdc3         (Basic)
    # cryptsetup luksOpen /dev/sdc3      cryptnattylvm     (LUKS)

Maps the (encrypted)  /dev/sdc3 to the clear-text /dev/mapper/cryptnattylvm

Now cryptsetup(8) has two styles, basic (aka plain) and LUKS style THEY ARE NOT COMPATIBLE.

This is the point at which the cipher-text to clear-text is defined, so this is the point
you get prompted for the KEY.


Where's the key?
----------------

Like cryptography algorithms, there is much intellectual capital in the area of
crypto keys. In general good keys are bigger and less human readable than poor
keys.  This is a bit unfortunate as an easy to remember key is just the
opposite.  This means typically people either settle for a poor key, or choose a
good key but write it down or they choose a good key don't write it down and so
lose it and their data.

With 'basic' cryptsetup this is one of the problems you face. It should not be
dismissed however, because one good use of this is to hold the key INSIDE
another secure storage, e.g. another encrypted filesystem.

However LUKS provides a 'solution' to this. The paper on this is quite readable
([http://cryptsetup.googlecode.com/svn-history/r500/wiki/LUKS-standard/on-disk-format.pdf](http://cryptsetup.googlecode.com/svn-history/r500/wiki/LUKS-standard/on-disk-format.pdf))
but in short, LUKS puts a header at the start of the volume.  This contains
eight slots for keys. Each slot contains the 'master key' encrypted with a
'password' so once you provide your password, software can extract the 'master
key' and so use this to decrypt your data. This sounds little odd at first, but
consider:

1: It is possible to change your password WITHOUT changing the MASTER KEY 

2: Since the MASTER KEY does not change, data does not need to be re-encrypted

3: The MASTER-KEY can be 'good' (strong) since you don't need to remember it.

4: While it appears that this is only as good as the password, the password is
   only used to encode a small(ish) random sequence of bytes not susceptible to any
   kind of content analysis (counting the number of 'e's in old Caesar ciphers)
   [ This is somewhat let down by a checksum for ease of use, so dictionary attacks
     would work well ... avoid dictionary words! ]

5: The presence of the header alerts software to the presence and type of
   encryption, thus systems like udev can spot an encrypted volume and prompt
   for a password. It's almost seamless!

Using LUKS carries a few responsibilities:

      i: Set up multiple 'passwords' (in case you DO still forget) and store one somewhere safe
         (locked in a safe for example , you won't normally use this one)
      ii: Backup the LUKS data , otherwise a few bytes of corruption can lose everything
      iii: Understand how to revoke old passwords



Where was I ... oh yes Full disk encryption
-------------------------------------------

So I have a system with 3 hard disks (sda,sdb,sdc). I have Ubuntu 10.10
(Maverick) installed on sda, sdb has some space and sdc is new (empty).  Using
the Ubuntu 11.04 (Natty) ALTERNATE INSTALL CD I installed a new instance on sdb
using a separate partition for /(root) and swap. This meant that each partition
was separately encrypted and contained a filesystem or swap.

What I have ended up with (partly as an experiment) is three sepeate installations
of Ubuntu on the same system:

   sda - Maverick unencrypted
   sbb - Natty encrypted            -- This is hd1 in grub parlance
   sdc - Natty encrypted (with LVM) -- This is hd2 in grub parlance

In each case I chose to install grub on the separate disk (sdb or sdc) so the
MBR was not updated. In order to boot these systems I used a chainloader boot
in the Maverick partition:

# cat /etc/grub.d/40_custom
#!/bin/sh
<...elided...>
menuentry "Encrypted Natty on 2nd disk" {
      set root=hd1
      chainloader +1
}

menuentry "Encrypted Natty on 3rd disk" {
      set root=hd2
      chainloader +1
}

Then a quick grub-update to install this setup.

At the the grub boot of Maverick I can additionally choose one of the two
entries. In both cases it launches the grub boot on the 2nd or 3rd disk.

For sdb, /(root) is in /dev/sdb2 and is LUKS encrypted  (a Primary partition)
         swap is in    /dev/sdb6 and is LUKS encrypted  (a Logical partition)
         /boot in in   /dev/sdb7 and is NOT encrypted

When this is booted, I get TWO prompts for passwords one for /(root) and another
for swap. This is a somewhat unusual setup for Natty (sdc is more typical)

The mapping & setup of these disks is done during boot of Natty. I cannot
trivially access these from by Maverick (sda) system since they are encrypted. To
access these drives I do:

SDB:

# cryptsetup luksOpen /dev/sdb2  cryptsdb2
Enter passphrase for /dev/sdb2: 

# mount /dev/mapper/cryptsdb2 /mnt

As should be clear, this 'maps' /dev/sdb2(cipher-text) to
/dev/mapper/cryptsdb2(plain-text) it can then be mounted in the normal way.

There is some syntactic sugar in the form of /etc/crypttab and
/etc/cryptmount/cmtab which will be useful if you need to do this a lot, but
does not aid in understanding.

SDC:

The mounting of /dev/sdc is more interesting. During Natty install the choice
made was full disk encryption with LVM. What appeared on disk was:

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34            1987   977.0 KiB   EF02  
   2            1988          501988   244.1 MiB   0700  <-------- Boot
   3          501989      3907029118   1.8 TiB     0700  <-------- LVM

 
(This is a GPT style partition table)

So we can try a similar trick with cryptsetup:

# cryptsetup luksOpen /dev/sdc3  cryptsdc3
Enter passphrase for /dev/sdc3: 
root@eddie:/data/ubuntu-home/graeme/Documents/Crypto# mount /dev/mapper/cryptsdc3 /natty/
mount: unknown filesystem type 'LVM2_member'

We can map it, but as you see it cannot be mounted. This is because the partition contains
a LVM 'physical volume' :

# pvdisplay /dev/mapper/cryptsdc3 
  --- Physical volume ---
  PV Name               /dev/dm-1
  VG Name               eddie
  PV Size               1.82 TiB / not usable 2.95 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              476870
  Free PE               238452
  Allocated PE          238418
  PV UUID               rzOr7Q-ioew-b0UM-rAp0-HEfz-04TH-ftQZyF

# lvscan
  ACTIVE            '/dev/eddie/root' [927.33 GiB] inherit
  ACTIVE            '/dev/eddie/swap_1' [3.99 GiB] inherit


So what we see are two more mapping have appeared, one is /(root) the other swap:

#mount /dev/mapper/eddie-root /natty/

This gives us access to the /(root) 'partition' inside the LVM on the encrypted
partition /dev/sdc3 (phew).

Now this works as long as we don't trash any of the LUKS data in the
header. Recall we don't really have the MASTER KEY which encrypts the data the
only place that is stored is INSIDE THE PARTITION.


#cryptsetup luksHeaderBackup /dev/sdb2 --header-backup-file sdb2.luks.backup

# file sdb2.luks.backup
sdb2.luks.backup: LUKS encrypted file, ver 1 [aes, cbc-essiv:sha256, sha1] UUID: a334bf67-3c95-4395-bfa3-27588f0

This file looks to be simply a 'bit prefect' copy of the 1st 1028 K of the block device.

Now if we lose the 1st few blocks of the volume we can restore it with
luksHeaderRestore option of cryptsetup.

But, in common with many backups, there is hidden danger here:

     1: The key file you now have makes a perfect vehicle to test hacking
        approaches a bad guy can take your backup and attack it on his super
        computer. He only need to find, one of, your passwords. You have no way
        of knowing this happening.

     2: If you subsequently revoke one of these passwords, then by restoring this
        header to the older copy. The old password will again work..
    (NB they need root access to write the header).

     3: Even without restoring the header. Simply possessing the header and any
        password makes it possible to extract the MASTER KEY. With this MASTER
        KEY the data can be read in only a slightly more clumsy fashion.


So backups are a two edged sword. Being careful is always a good idea but additionally
decide which is the greater risk:

       Commercial: Loosing access to the data is the worst outcome.
       Military:   Better to lose the data than allow anyone else to read it.

---


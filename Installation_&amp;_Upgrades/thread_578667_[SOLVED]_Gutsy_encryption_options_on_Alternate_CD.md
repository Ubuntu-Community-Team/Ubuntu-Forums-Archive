---
title: "[SOLVED] Gutsy encryption options on Alternate CD?"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by ruibernardo on 2007-10-17
Hi, I need some info about Gutsy installer (Alternate CD).

I've tested Gutsy encryption with the Alternate CD. Works fine with the default option - Guided LVM with encryption. It creates a boot partition (ext3) and a crypto partition for the rest of the disk, etc.

My questions are: 

- Can I create a different partition scheme, like having a separate /home partition also encrypted? (apparently not)

- Can I encrypt 2 discs, one for root, the other for /home?

- Because the installer deletes all the partitions on disk, can I, later, shrink the size of the encrypted partitions and install another OS (linux distro or windows?

I just ask this because I don't see any options on the installer, and when I try to «Go back» and change something, apparently I can't.

Am I missing some options? What can I do to have encryption and other OS and/or a separate /home partitions?

---

### Post by harun on 2007-10-18
I have the same questions, hope someone can answer them.

---

### Post by High Roller on 2007-10-18
You can manually partition the drive and then assign the partitions you want to be encrypted as such.  It's really flexible.

---

### Post by ruibernardo on 2007-10-19
Thanks for the replies. I got the first part of the questions answered, the part about the encrypted second disk as /home. Still looking for changing the size of the partitions to install another OS.

The installer is very flexible, yes. I thought it would be flexible enough to do what I wanted, but it doesn't. 

The way I found to set Gutsy all encrypted with a second disk as /home was to follow the "Guided - use entire disk and set up encrypted LVM" for the first disk, and after the install is complete then set up the second disk. The first part is easy, done by the installer, the second I did it this way:[LIST]
[*]  Boot the new encrypted Gutsy in recovery mode (so actual /home can be moved)[/LIST][LIST]
[*]  Move /home to a different name.[/LIST][INDENT]```
mv /home /home_bak
```[/INDENT][LIST]
[*]Put random data in the second disk (/dev/sdb in this case). A long wait here.[/LIST][INDENT]```
dd=/dev/urandom of=/dev/sdb
```[/INDENT][LIST]
[*]Create the partition for /home with fdisk[/LIST][INDENT]```
fdisk /dev/sdb
```Press "n" (new), "p" (primary), "1", "Enter" (first cylinder), "Enter" (last cylinder) to use the all disk. Press "w" to write to disk and exit. The new partition is /dev/sdb1.
[/INDENT][LIST]
[*]  Encrypt that partition for /home:[/LIST][INDENT]```
cryptsetup luksFormat /dev/sdb1
```Type the passphrase then type:
[/INDENT][INDENT] ```
cryptsetup luksOpen /dev/sdb1 home
```[/INDENT][LIST]
[*] Format it and mount it:[/LIST][INDENT]```
mkfs.ext3 /dev/mapper/home
mount /dev/mapper/home home
```[/INDENT][LIST]
[*] Copy the old home to the new home, then delete the old home:[/LIST][INDENT]```
cp -ax /home_bak/* /home
rm -rf /home_bak
```[/INDENT][LIST]
[*] Check the UUID of the new /home partition with blkid (/dev/sdb1 in this case):[/LIST][INDENT]```
user@gutsy$ blkid /dev/sdb1
/dev/sdb1: UUID="a720a1cf-e3e1-a484-9567-15049b853520" TYPE="crypt_LUKS#"
```[/INDENT][LIST]
[*] Add it to /etc/crypttab[/LIST][INDENT]```
/home /dev/disk/by-uuid/a720a1cf-e3e1-a484-9567-15049b853520 none luks
```[/INDENT][LIST]
[*] Add it to /etc/fstab (the UUID is commented, just there for info)[/LIST][INDENT]```
# UUID=a720a1cf-e3e1-a484-9567-15049b853520
/dev/mapper/home ext3    /home    defaults    0    1
```[/INDENT][LIST]
[*] Reboot as usual (you will be asked twice for the passphrase, once for root, the other for /home) and login.[/LIST]

---

### Post by High Roller on 2007-10-19
> **epimeteo said:**
> Thanks for the replies. I got the first part of the questions answered, the part about the encrypted second disk as /home. Still looking for changing the size of the partitions to install another OS.

The installer is very flexible, yes. I thought it would be flexible enough to do what I wanted, but it doesn't. 

The way I found to set Gutsy all encrypted with a second disk as /home was to follow the "Guided - use entire disk and set up encrypted LVM" for the first disk, and after the install is complete then set up the second disk. The first part is easy, done by the installer, the second I did it this way:[LIST]
[*]  Boot the new encrypted Gutsy in recovery mode (so actual /home can be moved)[/LIST][LIST]
[*]  Move /home to a different name.[/LIST][INDENT]```
mv /home /home_bak
```[/INDENT][LIST]
[*]Put random data in the second disk (/dev/sdb in this case). A long wait here.[/LIST][INDENT]```
dd=/dev/urandom of=/dev/sdb
```[/INDENT][LIST]
[*]Create the partition for /home with fdisk[/LIST][INDENT]```
fdisk /dev/sdb
```Press "n" (new), "p" (primary), "1", "Enter" (first cylinder), "Enter" (last cylinder) to use the all disk. Press "w" to write to disk and exit. The new partition is /dev/sdb1.
[/INDENT][LIST]
[*]  Encrypt that partition for /home:[/LIST][INDENT]```
cryptsetup luksFormat /dev/sdb1
```Type the passphrase then type:
[/INDENT][INDENT] ```
cryptsetup luksOpen /dev/sdb1 home
```[/INDENT][LIST]
[*] Format it and mount it:[/LIST][INDENT]```
mkfs.ext3 /dev/mapper/home
mount /dev/mapper/home home
```[/INDENT][LIST]
[*] Copy the old home to the new home, then delete the old home:[/LIST][INDENT]```
cp -ax /home_bak/* /home
rm -rf /home_bak
```[/INDENT][LIST]
[*] Check the UUID of the new /home partition with blkid (/dev/sdb1 in this case):[/LIST][INDENT]```
user@gutsy$ blkid /dev/sdb1
/dev/sdb1: UUID="a720a1cf-e3e1-a484-9567-15049b853520" TYPE="crypt_LUKS#"
```[/INDENT][LIST]
[*] Add it to /etc/crypttab[/LIST][INDENT]```
/home /dev/disk/by-uuid/a720a1cf-e3e1-a484-9567-15049b853520 none luks
```[/INDENT][LIST]
[*] Add it to /etc/fstab (the UUID is commented, just there for info)[/LIST][INDENT]```
# UUID=a720a1cf-e3e1-a484-9567-15049b853520
/dev/mapper/home ext3    /home    defaults    0    1
```[/INDENT][LIST]
[*] Reboot as usual (you will be asked twice for the passphrase, once for root, the other for /home) and login.[/LIST]

You can also just choose "manual" when selecting "partitioning method" during setup and then assign /boot to a 100mb partition followed by creating two encrypted partitions under which you would place the LVM partitions for / and /swap.  The second encrypted partition could then be assigned another LVM where you could place /home after booting up etc.  That'd work as well wouldn't it?

I don't think you can resize the encrypted partitions (easily) though.  Maybe someone else can provide some insight?  I have Windows installed on the same drive and I had to have it installed first before I could setup/encrypt Ubuntu.  The "easy" way (in my mind) would be to reserve space for you Windows/other OS partition before encryption.

My partitions go:

[NTFS]
[/boot *unencrypted*]
[encrypted LVM with both /swap and /]

---

### Post by mk1970 on 2007-10-22
> **epimeteo said:**
> Hi, I need some info about Gutsy installer (Alternate CD).
- Can I create a different partition scheme, like having a separate /home partition also encrypted? 

Take a look at [http://www.iki.fi/kuparine/comp/ubuntu/en/cryptolvm.html](http://www.iki.fi/kuparine/comp/ubuntu/en/cryptolvm.html)

---

### Post by ruibernardo on 2007-10-22
Thanks for your answers guys.

High Roller did point to the right direction and mk1970 have it very clearly explained in his site.

---

### Post by High Roller on 2007-10-23
> **epimeteo said:**
> Thanks for your answers guys.

High Roller did point to the right direction and mk1970 have it very clearly explained in his site.

Props to mk1970 for that sweet how-to!  :guitar:

---

### Post by davidfmartin on 2007-10-30
I have some questions about how this may work in a production environment.

1. How will key escrow be handled?
2. Can more than one account decrypt the drive?  Example: I may want to create an administrator account for decryption.
3. What tools are available for repairing encrypted partitions?  If my encrypted file system dies what can I do to repair it?   

Thanks.

---


---
title: "Encrypted install on external harddisk booted once only"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by Orky on 2008-06-07
I have used the Ubuntu Hardy 8.04 Alternate Install CD to install an encrypted system on an external harddrive (plain USB device). The problem is, it has only booted once so far. On the failed attempts, I get a busybox shell after a few minutes.

Error messages I get:
Setting up cryptographic volume sda5_crypt (based on /dev/disk/by-uuid/...
cryptsetup: Source device /dev/disk/by-uuid... not found

When I get the busybox shell, the partitions on the external drive are available with the correct UUIDs.

The motherboard is a recent Asus M2N-VM HDMI (cheapo AMD mobo with integrated GeForce7 and Nvidia chipset which seems to work just fine in a more plain Ubuntu install).
The motherboard does boot from USB properly.
The installation has several partitions:
sda1: /boot (plain)
sda5: lvm_crypt volume with three partitions:
* / (20G)
* swap (2G)
* /home (lots of Gs)

For some reason, the bootup sequence does not recognize the partitions until it is too late, I think. I have dug in the initramfs file, but the scripts all seem to be alright, although I am not a bootup script guru by any means.

---

### Post by Herman on 2008-06-07
Well you are not the only one, I tried using the Ubuntu Hardy Heron 8.04 Alternate CD's encrypted with LVM installation in a USB flash memory device two times and mine refused to boot both times.
The exact same installation process resulted in a perfectly good installation in an internal hard disk.

The advantages of  completely encrypted installation seem a little dubious to me anyway, since it introduces several other problems that I don't know how to deal with. For instance, how to run a file system check in an encrypted file system? How to rescue the system in an emercency, and how to recover files?

I think that it might be smarter (for me anyway), to just stick with the regular installation of Ubuntu Hardy Heron and use Seahorse to encrypt any sensitive files. Hardy comes with Seahorse as a standard program. 'Accessories'-->'Passwords and Encryption Keys', (aka Seahorse).
Once you set up your keys in Seahorse you can right-click on any file and encrypt it or decrypt it. You can also manage RSA keys for SSH Networking with Seahorse. 

For my own how-to on Seahorse: [Install Seahorse]("http://users.bigpond.net.au/hermanzone/p5.htm#Install_Seahorse") - encrypt sensitive files for greater security, send encrypted email  

I hope someone will chime in with info on encrypted file systems in Ubuntu though, I would like to learn more about that too.

Regards, Herman :)

---

### Post by Orky on 2008-06-09
[http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html](http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html)

These instructions enabled me to mount the partitions from an existing system.

The advantage of a completely encrypted system are that you don't need to remember to encrypt some files, and you won't accidentally save files in an unencrypted location.

---

### Post by Herman on 2008-06-10
I may have found something here about how to run a file system check, [Running fsck on a LUKS encrypted partition in LVM]("http://iquaid.org/2008/03/04/running-fsck-on-a-luks-encrypted-partition-in-lvm/").
I haven't tried it out yet, but I'm optimistic that it will work. :)

---

### Post by metal1633 on 2008-06-27
> **Orky said:**
> [http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html](http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html)

These instructions enabled me to mount the partitions from an existing system.

The advantage of a completely encrypted system are that you don't need to remember to encrypt some files, and you won't accidentally save files in an unencrypted location.
Well that is unhelpful. I get the exact same error ON FIRST BOOT of a fresh install. 

Ubuntu Server on a Dell Poweredge 2400. 6 scsi drives setup as Raid 5 using Adaptec onboard scsi controller card. I allowed the installer to create default partitions with Encryption.

---

### Post by wwqt0r on 2008-10-04
Any solutions for this problem? i hate that busybox :(

---


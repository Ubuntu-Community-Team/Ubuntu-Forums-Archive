---
title: "Question about the Home Encryption"
date: 2009-01-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Archmage on 2009-01-19
I notice that it is possible to turn on that the user password is required to log in and decrypt the home-partition.

This is a nice feature that I would like to use. However I want to use my old settings from the 8.10.-users to be transfered to my test-system.

Normaly I would just plug in my back-up-harddrive and copy the old /home-partition to the new /home-partition.

Is this also possible in this case or will it impossible to copy the files, since they destination is encrypted?

Will it work, although I have more than one user?

---

### Post by pressureman on 2009-01-19
Firstly, it's not encrypting the partition (because that wouldn't work well if you had multiple home dirs on one partition, belonging to different users). 

Encrypted home dirs encrypts all the files in YOUR home dir, using YOUR key, at a per-file level.

As long as you are logged in as the user with the encrypted home dir, at the time of copying your files from your previous install, any new file you create/copy to that home dir should be encrypted in the process.

---

### Post by LordVeovis on 2009-01-19
I currently have a fully encrypted install.  Encrypting a partition can be done by using the alternative CD and that will make it so that any data saved on the drive is encrypted and when the PC boots you enter your decryption key so the pc will be able to mount the encrypted drive.  So copying any data to the drive while it is mounted automatically encrypts the data.  And yes, the partition itself is encrypted, not just the files.

---

### Post by pressureman on 2009-01-19
Encrypting an entire partition works well if you're the only user of the computer, or if the partition resides in a server that users don't have physical access to.

Where you have multiple users with physical access to a certain computer however, you don't really want Alice's encryption key to also decrypt Bob's files, in case Alice can't be trusted and boots from external media to bypass the filesystem permissions.

Multi-user systems, where each user has physical access to the drive, is the main reason for each user having their own key, and their own encrypted home dir.

That said, encrypting a partition/drive is a neat idea for removable media such as external HDDs or USB sticks. LUKS makes this very user-friendly, and you no longer have to worry about people reading your files if you lose your USB stick.

---

### Post by Starks on 2009-01-19
Can the encryption be removed by the user?

---

### Post by Triggerhapp on 2009-01-19
> **Starks said:**
> Can the encryption be removed by the user?

Wouldnt that require formatting the partition for /home/user ? so i guess not?

---

### Post by LordVeovis on 2009-01-19
> **Starks said:**
> Can the encryption be removed by the user?

You could by just copying the data out of the encrypted space, but as for decrypting the data while leaving it in place, no.  Same goes for changing the encryption key.  You have to re-write the entire partition.

---

### Post by LordVeovis on 2009-01-20
If you are worried about having multiple users and didn't want 1 key to mount the whole drive, partition the drive for different users. This would cause problems with space if you do not know how much you want to give each user. If space is a concern, perhaps you can do what the alternative CD does for an encrypted private directory. That is to make a /home/.username/ folder and mount it to the /home/username/ folder. I am not sure how they make the folder encrypted, but I think it is just using the cryptsetup and mounted that way too.

EDIT: Yes, this is done with cryptsetup.  'man cryptsetup' and 'cryptsetup --help' has some helpful info.

---

### Post by pressureman on 2009-01-20
I'll say it again, since people seem to be a little confused about partition-level encryption.

Encrypted homedirs does not use partition-level encryption. Solutions such as dm-crypt (eg. cryptsetup), TrueCrypt and Loop-AES are block-device level encryption. That is, they sit between the filesystem (such as ext3) and the physical device. The filesystem is generally unaware that there is an encryption layer between it and the physical disk. This is why dm-crypt for example can be used for encrypted swap. The swap subsystem in itself knows nothing about encryption, but dm-crypt is transparently encrypting everything before it gets written to the physical swap partition.

Encrypted homedirs, as implemented in Ubuntu, uses eCryptfs, which sits ON TOP of a filesystem (not a block device), and looks to the kernel like a filesystem itself. This is why it's referred to as a stacked filesystem. With encrypted homedirs, the stacked eCryptfs is automatically mounted and unmounted when the user logs in and out. This avoids the need to have one home partition per user, as Lord Veovis suggests above.

At present, filenames are not encrypted, so somebody who mounted the disk in a different computer (or otherwise somehow bypassed filesystem permissions) would still see the names of files in your directory. The contents of the files would be encrypted however. This is one of the main differences between eCryptfs and partition-level encryption. With partition-level encryption, EVERYTHING is encrypted, since it's block-device level - file contents, filenames, symlinks, inodes, empty space even... the whole lot.

[https://launchpad.net/ecryptfs](https://launchpad.net/ecryptfs)
[http://ecryptfs.sourceforge.net/ecryptfs-faq.html](http://ecryptfs.sourceforge.net/ecryptfs-faq.html)

---


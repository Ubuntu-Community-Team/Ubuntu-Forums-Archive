---
title: "Please help (data recovery)"
date: 2015-11-17
forum: Installation &amp; Upgrades
---

### Post by mayurpathak6 on 2015-11-17
I just reinstalled Ubuntu 14.04 on my computer. Prior to reinstallation, I booted from a live CD and copied my home folder to an external HDD. But now I have two new problems. I am unable to copy the backed-up folder back to my computer, I think because its file name is too long. I also cannot view the contents of the backed-up folder. The folder also contains only two files, even though the properties window shows it to be over 200gb in size, as it should be. When I run ecryptfs-mount-private, I receive the following error: Encrypted private directory is not setup properly. 

Can someone please help me recover my data? Thanks.

---

### Post by egeezer on 2015-11-17
I suspect that when you did the copying to external HDD from the live CD, it stored the folder with some sort of permissions peculiar to the live CD.  You might try booting the live CD again and working from there - perhaps you could at least change the too-long file name.

---

### Post by oldfred on 2015-11-17
Did you copy /home with the encrypted file in it? Generally better to copy data after you have unencrypted it with your passphase.
The purpose of encryption is to prevent users from getting to data. So only your passphase will work.

I do not use nor know encryption, but some info here:
 Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

---

### Post by mayurpathak6 on 2015-11-19
> **oldfred said:**
> Did you copy /home with the encrypted file in it? Generally better to copy data after you have unencrypted it with your passphase.
The purpose of encryption is to prevent users from getting to data. So only your passphase will work.

I do not use nor know encryption, but some info here:
 Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

I don't have the "encryption passphrase," but I do remember the old password. Do you know how I can use that to access the data?

This is what I've tried so far, and the output:

goku@Nibiru:/media$ sudo ecryptfs-recover-private
[sudo] password for goku: 
INFO: Searching for encrypted private directories (this might take a while)...
INFO: Found [/home/goku/.local/share/Trash/expunged/4150860371/home/.ecryptfs/goku/.Private].
Try to recover this directory? [Y/n]: y
INFO: Could not find your wrapped passphrase file.
INFO: To recover this directory, you MUST have your original MOUNT passphrase.
INFO: When you first setup your encrypted private directory, you were told to record
INFO: your MOUNT passphrase.
INFO: It should be 32 characters long, consisting of [0-9] and [a-f].


Enter your MOUNT passphrase: 
mount: wrong fs type, bad option, bad superblock on /home/goku/.local/share/Trash/expunged/4150860371/home/.ecryptfs/goku/.Private,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


ERROR: Failed to mount private data at [/tmp/ecryptfs.p7lQEjgi].

---

### Post by Vladlenin5000 on 2015-11-19
Again, > The purpose of encryption is to prevent users from getting to data. So only your passphase will work.

---

### Post by mayurpathak6 on 2015-11-19
> **Vladlenin5000 said:**
> Again,

I think I found my old passphrase file. The location is : /media/goku/17a28166-cc97-4588-8148-469f24aa7f74/oldstuff/home/.ecryptfs/goku/.ecryptfs/wrapped-passphrase. Other files in this location are: auto-mount, auto-umount, Private.mnt, and Private.sig. I copied these old files to my current /home/.ecryptfs prior to running sudo ecryptfs-unwrap-passphrase, then used that passphrase to try to recover the data with ecryptfs-recover-private, but it didn't work. 

Any advice? Thank you in advance.

---

### Post by oldfred on 2015-11-19
I am sure you cannot copy one set of files with passphase into another encrypted partition to decrypt it. Otherwise encryption would be worthless as I just create my own encrypted files and copy my passphase files into your system. 
And now if you have moved files around inside your encrypted system, it probably is not recoverable.

---


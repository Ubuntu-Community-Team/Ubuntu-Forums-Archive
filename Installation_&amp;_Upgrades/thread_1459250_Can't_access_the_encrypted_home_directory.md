---
title: "Can't access the encrypted home directory"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by Jacks0n on 2010-04-21
Hi,

I tried upgrading to 10.04, and now when it boots it just goes into a grub2 terminal and doesn't display a boot menu. I tried re-installing grub2 from the live cd, but that didn't do anything.

I figured if I've hosed the last install I'll install from scratch, but I can't even access my files from the live cd! I did a bit of searching and everyone seems to just encrypt ~/Private, whereas I've encrypted the whole home directory. So much for security...

In the live cd, it has a readme.txt and says to type "ecryptfs-mount-private" to access the files, but it just gives the error "ERROR: Encrypted private directory is not setup properly". What do I do?


Thanks
Jackson

---

### Post by Jacks0n on 2010-04-21
I found a document about it in the Ubuntu wiki: [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory) and followed the instructions.

```

ubuntu@ubuntu:~$ sudo ecryptfs-add-passphrase --fnek 
Passphrase: 
Inserted auth tok with sig [8182118473f3f8cc] into the user session keyring
Inserted auth tok with sig [942b6d7c42d3ba9b] into the user session keyring
ubuntu@ubuntu:~$ sudo mkdir /media/oldhome
ubuntu@ubuntu:~$ sudo mount -t ecryptfs /media/c559d2a1-5b28-4abb-8dc1-0d2b92b44af8/jackson /media/oldhome
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: aes
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 16
Enable plaintext passthrough (y/n) [n]: n
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [8182118473f3f8cc]: 942b6d7c42d3ba9b
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=942b6d7c42d3ba9b
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=8182118473f3f8cc
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [8182118473f3f8cc] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : yes
Successfully appended new sig to user sig cache file
Mounted eCryptfs
ubuntu@ubuntu:~$ ls /media/oldhome
Access-Your-Private-Data.desktop  README.txt
ubuntu@ubuntu:~$ 

```

but it still doesn't work...


Jackson

---

### Post by progone on 2010-06-01
Jacks0n,

[https://answers.launchpad.net/ecryptfs/+question/46307](https://answers.launchpad.net/ecryptfs/+question/46307)

you are not the only one.  Have you found a solution yet?

---

### Post by COKEDUDE on 2010-12-12
> **Jacks0n said:**
> I found a document about it in the Ubuntu wiki: [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory) and followed the instructions.

```

ubuntu@ubuntu:~$ sudo ecryptfs-add-passphrase --fnek 
Passphrase: 
Inserted auth tok with sig [8182118473f3f8cc] into the user session keyring
Inserted auth tok with sig [942b6d7c42d3ba9b] into the user session keyring
ubuntu@ubuntu:~$ sudo mkdir /media/oldhome
ubuntu@ubuntu:~$ sudo mount -t ecryptfs /media/c559d2a1-5b28-4abb-8dc1-0d2b92b44af8/jackson /media/oldhome
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: aes
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 16
Enable plaintext passthrough (y/n) [n]: n
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [8182118473f3f8cc]: 942b6d7c42d3ba9b
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=942b6d7c42d3ba9b
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=8182118473f3f8cc
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [8182118473f3f8cc] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : yes
Successfully appended new sig to user sig cache file
Mounted eCryptfs
ubuntu@ubuntu:~$ ls /media/oldhome
Access-Your-Private-Data.desktop  README.txt
ubuntu@ubuntu:~$ 

```

but it still doesn't work...


Jackson

I also have this problem.

---


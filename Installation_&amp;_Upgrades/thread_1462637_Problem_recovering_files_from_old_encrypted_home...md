---
title: "Problem recovering files from old encrypted home..."
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by TerranAce007 on 2010-04-25
I purchased a larger hard drive to upgrade my HTPC running MythTV and a Samba file server. I put the old hard drive into an e-SATA enclosure and can still boot to it to access my files, but I can't seem to mount it correctly under the new installation to copy over my files even though I have the mount passphrase and encrypted filenames key.

I have tried using this [howto]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Storing%20Your%20Keys,%20Email%20and%20other%20Data%20in%20~/Private"), but I run into problems with the encrypted filenames.

This is how I'm doing it. I replaced the actual key data with A's and B's to protect my keys:
```

$ sudo -i

# ecryptfs-add-passphrase --fnek
Passphrase: *my mount passphrase*
Inserted auth tok with sig [AAAAAAAAAA] into the user session keyring
Inserted auth tok with sig [BBBBBBBBBB] into the user session keyring

#mount -t ecryptfs /media/disk-2/user/.Private /home/user/OLD
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [AAAAAAAAAA]: *BBBBBBBBBB*
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=BBBBBBBBBB
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=AAAAAAAAAA
Mounted eCryptfs

# mount
/dev/md0 on / type ext4 (rw,errors=remount-ro)
...
...
/home/.ecryptfs/user/.Private on /home/user/OLD type ecryptfs (rw,ecryptfs_sig=AAAAAAAAAA,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_fnek_sig=BBBBBBBBBB,ecryptfs_unlink_sigs)

#ls /home/user/OLD
ECRYPTFS_FNEK_ENCRYPTED.FWbWFuelqba3qUTTq-UTdHu5y1bfTl0J.c9F0j43jk8L7Ecpd2yb6jpuO---
ECRYPTFS_FNEK_ENCRYPTED.FWbWFuelqba3qUTTq-UTdHu5y1bfTl0J.c9F1KPFxL94O3tC8xTmumQARk--
ECRYPTFS_FNEK_ENCRYPTED.FWbWFuelqba3qUTTq-UTdHu5y1bfTl0J.c9F1Mwq0zTJeR-.x0gH90A3ZU--
ECRYPTFS_FNEK_ENCRYPTED.FWbWFuelqba3qUTTq-UTdHu5y1bfTl0J.c9F3rP8aEQGF7x0vql4i6-JVE--
....
....


```

As root, I can browse the files in Dolphin and can see the previews for things like image files. They open fine, but the filenames are not being decrypted. I have tried using both of the key signatures (AAAAAAAAAA and BBBBBBBBBB) as the filename key, but neither works. I get the same thing if I do not enable encrypted filenames - decrypted files with encrypted names.

As my normal user, I get this until I add the keys to my user's keyring:

```

$ ls OLD/
ls: cannot access OLD/Templates: No such file or directory
ls: cannot access OLD/Downloads: No such file or directory
ls: cannot access OLD/Pictures: No such file or directory
ls: cannot access OLD/Music: No such file or directory
ls: cannot access OLD/OLD: No such file or directory
ls: cannot access OLD/Videos: No such file or directory
ls: cannot access OLD/CloneZilla: No such file or directory
ls: cannot access OLD/Keepass: No such file or directory
ls: cannot access OLD/Public: No such file or directory
ls: cannot access OLD/Documents: No such file or directory
ls: cannot access OLD/Desktop: No such file or directory
CloneZilla  Desktop  Documents  Downloads  Keepass  Music  OLD  Pictures  Public  Templates  Videos

```

I think I'm missing something simple here but I've been messing with it all afternoon and nothing's coming to me. Any help would be greatly appreciated!

---

### Post by TerranAce007 on 2010-04-26
bump...

---

### Post by TerranAce007 on 2010-04-29
bump...

---


---
title: "Encrypted private directory problems"
date: 2008-08-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by cariboo on 2008-08-19
I created an encrypted private directory following the instructions here:

[https://wiki.ubuntu.com/EncryptedPrivateDirectory](https://wiki.ubuntu.com/EncryptedPrivateDirectory)

I was able to access the private directory when I created it, but since rebooting I get the following message when try to access the directory:

```
jimk@intrepid:~$ mount.ecryptfs_private
keyctl_search: Required key not available
```

I tried to create a new passphrase and I get this output:

```
jimk@intrepid:~$ ecryptfs-setup-private
ERROR: wrapped-passphrase file already exists, use --force to overwrite.
```

I can create a new passphrase using the force option, but I shouldn't have to do this every time I reboot. Can anybody throw any ligkt on what is happening here?

Jim

---

### Post by tamoneya on 2008-08-19
hmmm...
Ive really been looking forward to this feature and i tested it out in alpha 4 and it worked fine for me.  Anyways I dont know how to fix it and it sounds like a bug to me.
It seems as if currently it has no bugs so they need something to keep them busy.
[https://bugs.launchpad.net/ubuntu/intrepid/+source/ecryptfs-utils](https://bugs.launchpad.net/ubuntu/intrepid/+source/ecryptfs-utils)

---

### Post by cariboo on 2008-08-20
I created a bug report for my problem.

[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/259631](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/259631)

Jim

---

### Post by tawmas on 2008-08-20
I wonder... Did you set your passphrase the same as your login password?

---

### Post by cariboo on 2008-08-20
I solved my problem, by deleting .Private and .ecryptfrs and starting from scratch I now have access to my private directory. I created another user just to make sure I was doing it right and ran into another problem. When mounting the private directory as one user it also makes all the rest of the users private directories accessible at the same time.

Jim

---

### Post by cariboo on 2008-08-21
I tried duplicating the problems I was having with being able to open private directories system wide and can't seem to be able to do it today. I must have had my stupid hat on yesterday :). Today everything works as it should.

Jim

---

### Post by zerubbabel on 2008-10-04
Is it possible to use the new "encrypted private directory" feature to encrypt the entire home partition, or at least a particular user's home directory tree?

---

### Post by jfernyhough on 2008-10-04
When you first install you can set up an encrypted partition. Not sure if you can it afterwards, other than with something like TrueCrypt.

---

### Post by zerubbabel on 2008-10-04
Yes, I know. Right now I'm using LUKS to encrypt everything except my boot partition, but that is overkill. I really just need to encrypt my home directory tree. I was just hoping that when I upgrade to 8.10, I can do a clean install without LUKS, and use the new "encrypted private directory" mechanism instead.

---

### Post by inportb on 2008-10-04
You can just put what you want encrypted into your private directory and make symlinks out of the directory.

---

### Post by zerubbabel on 2008-10-04
I want *everything* in my home directory encrypted, including the contents of all subdirectories.

---

### Post by inportb on 2008-10-04
Well then, just put *everything* in your private directory :D

I don't see how LUKS would be overkill if what you want is LUKS functionality.

---

### Post by zerubbabel on 2008-10-05
It's overkill because I don't need the whole file system encrypted.

---

### Post by soleblaze on 2008-10-06
> **zerubbabel said:**
> It's overkill because I don't need the whole file system encrypted.

There's a pam mount module that you can use with dm-crypt + LUKS to automatically mount an encrypted home direcotry.  I vaguely recall it being easy to setup in ubuntu, but I haven't used it in at least a year.

---


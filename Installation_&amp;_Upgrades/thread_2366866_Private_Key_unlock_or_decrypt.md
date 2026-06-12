---
title: "Private Key unlock or decrypt"
date: 2017-07-22
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2017-07-22
How do I unlock a drive attached as an external device?

I backed up my /home of about 150 gigabytes to an external storage device. I want to unlock the device so I can use the contents. My OS of 16.04.2 was encrypted during installation and I had an install time screen (like a terminal screen) require a private key. Ubuntu generated this 32 wide string "passphrase". I wrote it down.

Per the README.txt on the encrypted external device:

"THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"
or
From the command line, run:
 ecryptfs-mount-private

If, for some reason, you have the data in question independent of the system it was used in, you will need the private key that Ubuntu's encryption wizard asked you to save on installation."

I do not have an icon named: "Access Your Private Data"

I tried: sudo ecryptfs-mount-private, entered the passphrase and saw:

```
Enter your login passphrase:
Inserted auth tok with sig [de0357543abe6969] into the user session keyring
**fopen: No such file or directory**
```

Does the above mean the device is unlocked? If it is unlocked, how can I copy the contents of the encrypted data to a second external device? I have but one copy, on this external device, of my /home due to my making a mess and I don't want to harm it.

What does the "fopen: No such file or directory" mean? Has some data been harmed? If there is harm can it be undone before I proceed?

Can the same device be unlocked, with the passphrase, during a LiveUSB session?

Once unlocked, can LiveUSB-Clonezilla be used to create a duplicate of the encrypted data?

Is there a safe way to remove the encryption from external drive device. Again, it is a backup of my /home.

---


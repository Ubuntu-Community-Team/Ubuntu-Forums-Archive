---
title: "Raid + Crypto + LVM Install Howto ?"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by gopher2x on 2008-06-18
I have 2 SATA 300 gb HD's and want to install Ubuntu.
I was thinking 2 raid devices. 
1 for /boot as raid 1 format ext3
1 for the rest of / as RAID 0 as cryto space formatted for LVM space...
Will this be possible? 
What partation do i mark as bootable?
can the system handle all this crap at boot?
Is there a HOW TO somewhere? I could not find one....
Thanks...

---

### Post by Rocket2DMn on 2008-06-18
You mean like [https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto](https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto)
It says using the alternate install cd generally can give you what you need, but there is information there for your reference, too.
help.ubuntu.com has a lot of useful pages, I suggest using google for narrowing your search: "site:help.ubuntu.com <query>"
If you make your query something like "lvm" or "encrypted" or "RAID"

---

### Post by gopher2x on 2008-06-18
Thats a nice howto but no RAID...
Will keep searching though... thanks..

---

### Post by Rocket2DMn on 2008-06-18
There is also [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) (among other pages)
The alternate CD which you will need for the other stuff is also used for RAID installations.
I think if you get the RAID/LVM part setup first, doing the Encrypted part will be much easier rather than trying to do it all at once.
Good luck.

---

### Post by gopher2x on 2008-06-18
If i do the encryption first I would only have to type in the passphrase 1 time. If i encrypt each mounted filesytem wouldent i have to enter a passphrase for each?

Alternate CD downloaded and burning now...

---

### Post by Rocket2DMn on 2008-06-18
If you are using RAID0, then it acts as one file system.  You have an unencrypted /boot partition which should recognize the RAID (since it has to mount the filesystem), and you said everything else would be encrypted under / - that is only one encrypted partition of ~600GB.
I've never done this myself, so I can't say for sure.
Basically what should happen is you can setup the partitions BEFORE you actually start the install process.  Once you have the RAID0 setup, you can do your install and have the file system encrypted.  The fact that it is RAID should not be important for this.

I'll check up on you in the morning, I'm going to bed right now, so good luck!

---

### Post by gopher2x on 2008-06-18
I think i want to use /boot as raid1 and the rest as raid0...
Thanks for the support... Its done burning so im gonna pop it in now and post the results... thanks...

---


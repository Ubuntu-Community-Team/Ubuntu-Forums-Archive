---
title: "&quot;Starting Init crypto disks...&quot; failure to boot"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by Midgetprawn on 2010-02-17
Hello all
Having installed 9,10 onto a laptop my cherubic daughter swicthed off the power (no battery) and upon restarting i am faced with  "Starting Init crypto disks...  OK) and there it stops!! I had hoped that I could go to recovery mode and fix it but  am faced with the same stalling point.
I see others are unresolved in this.
Any suggestions beyond  reinstall?

---

### Post by dabl on 2010-02-17
It might be fixable.  Things to investigate, from a Live CD session:

```
fdisk -lu
```  (see the disk partitions and their filesystem types, and any errors about them)

```
sudo blkid
``` (see the partitions with their UUID numbers)

Alt-F2 "dolphin" and then browse to the /etc/fstab file on the hard drive system, open it with gedit (see the filesystem table and make sure the UUIDs match the ones you saw in the blkid output)

Also, it would not hurt to run fsck on each relevant Linux partition.  Finally, try a Ctrl-D at the point where booting stops -- you might get lucky.

---

### Post by ben2talk on 2010-05-02
What is going on here? I see several threads with people who find messages saying that their newly ecrypted Home directory is now inaccessible, and yet it does not seem to reach the front line news.

What's the story with this? /usr/bin/ecryptfs-mount-private returns '/usr/bin/ecryptfs-mount-private'

Despite saving the passcodes when encrypting, it seems my Home directory and contents (including 1.2 GB of podcast files and a ton of music video's) are now completely out of my reach - scrambled and inaccessible.

Surely such a security feature should be renamed 'shredder' as it effectively deleted my entire Home directory!!!

My conky.rc (hours and hours of work) and many other things I wanted to keep and use again on installing 10.04!!!

Maybe it's high time to think about Mint, or jump into Fedora which I hear is entirely more professional.

---


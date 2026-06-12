---
title: "GParted shows swap as unknown file system in Xubuntu 11.10"
date: 2012-03-08
forum: Installation &amp; Upgrades
---

### Post by ultimatecosmo on 2012-03-08
I installed Xubuntu 11.10 yesterday and noticed that the swap partition is being identified as unknown file system. My question is: is this proposital? Since I saw Ubiquity doing something with swap to improve security, don't remember the message that appeared, think it is... but I'm not sure.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=213923&stc=1&d=1331232831[/IMG]

Strangely, when I type free -m get this:

free -m
             total       used       free     shared    buffers     cached
Mem:          3907       2623       1284          0        126       1559
-/+ buffers/cache:        936       2970
**Swap:         3999          0       3999**


My fstab:
# swap was on /dev/sda2 during installation
#UUID=8c0fa077-35fb-4ee6-b54d-43e217197639 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

**I encrypted the home folder**, this have something related?
Thank you.

P.S.: Also, how to remove the Bluetooth tray icon? I already deactivated it.

---

### Post by MAFoElffen on 2012-03-08
My past experiences w/ that, is that I just selected the partition and formatted it with type as "swap".  I figured that anything in there was transient temporary files, so was not important.

Worked for me...

---

### Post by MAFoElffen on 2012-03-08
<<Duplicate Post>>

---

### Post by ultimatecosmo on 2012-03-08
> **MAFoElffen said:**
> My past experiences w/ that, is that I just selected the partition and formatted it with type as "swap".  I figured that anything in there was transient temporary files, so was not important.

Worked for me...

I read that encrypting the home partition would also be automatically encrypt swap.But this "unknown file system" is giving me doubts about it. :(

Ah! Here: [https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)

"Users installing from Ubuntu 9.10 and selecting the Encrypted Home option will automatically have encrypted swap space."

---

### Post by Rulius on 2012-12-27
Exactly the same thing happened to me after a clean install of 12.04, where I chose to encrypt my home folder on installation.  

Both Gparted and disk utility show swap partition as unknown. Also, "free -m" gave me 0 for swap increasing my concern that something is wrong.  

I deleted and recreated the swap partition from live cd and gparted initially showed swap correctly , but the error reappeared on next boot.  :frown:

I started editing fstab using the uuid indicated in "sudo blkid", only to realise that it changed on every boot.   ):P

After reading some other threads and this one I reached the following conclusions and someone more knowledgeable please confirm if I'm right or wrong.  

1) If you opt for an encrypted home folder your swap partition will also be encrypted (for releases after 9.10)  

2) The entry for swap in fstab should be: 
/dev/mapper/cryptswap1 none swap sw 0 0 
and the uuid..... entry for swap should be commented (having # in front of it) , or absent.   
Important: fstab was like that before I started messing with it.

3) Since the swap partition is encrypted, it is normal for Gparted and disk utility to show it as unknown. (Please confirm)   

Finally, after editing fstab per conclusion 2) and using "sudo swapon -a" I could see my swap on "free -m" and everything - apart from the unknown characterization of swap by Gparted and disk utility - seems to be fine. :guitar:

---

### Post by oldfred on 2012-12-28
We have seen the question before and everyone with encrypted swap has the same issue of gparted not showing it, because it is encrypted.

We have seen a lot of BootInfo reports or bootinfoscript reports where that is standard with this setting when /home is encrypted:
/dev/mapper/cryptswap1 none swap sw 0 0

---


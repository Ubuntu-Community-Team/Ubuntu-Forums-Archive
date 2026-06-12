---
title: "Encryption Fails on Large Disk? 12.04 Alt Instaler, 2T pair of disks- RAID fine"
date: 2013-08-05
forum: Installation &amp; Upgrades
---

### Post by DiagonalArg on 2013-08-05
Hi. I'm trying to do an install on a pair of 2T disks, which are to be raided together and encrypted.

The (large) root partition is being ignored when I try to activate it as an raided/encrypted partition.  Notice the odd issue in step (2). Is this relevant?

(Please help me with the alternate installer, as I'm not ready to learn RAID/LUKS command line yet.)

(1) Each disk has 3 primary partitions, which are set to be used for RAID
500MB (will be for /boot)
20GB (for swap)
2T (for root)

(2) I now "Configure Software RAID" and get:

MD0   499.1 MB
MD1   20.0 GB
MD2   2.0TB         ext4

MD0/1 have the size, but nothing else listed after them in the partition layout
***MD2, oddly, has "ext4" after it, even though I have not set it to be used yet.***

(3) I now select each RAID device in turn:

MD0 I use as ext4 and mount at /boot.  This produces:
MD0   499.1MB   f   ext4   /boot

MD1 I use a "physical  volume for encryption", Encryption Key I set to "Random Key"
MD1   20.0GB     K  crypto   not active

MD2 I use a "physical  volume for encryption", Encryption Key remains at "Passphrase"
MD2   2.0TB       K   crypto   not active

(4) Now I "Configure Encrypted Volumes"

It asks me if I want to write changes to disk ("Yes") and then offers:

Encryption Configuratoin Actions:
Activate Existing Encrypted Volumes
Create Encrypted Volumes
Fihish

***When I choose the first ("Activate") it asks me for a passphrase for MD1.
***But MD1 is supposed to have a _random_ key?

***If I choose it anyway, it completely ignores the 2T disk, not allowing  me to activate it.

Anyone have an idea of what's up?

---

### Post by newbie-user on 2013-08-06
You have to choose "Create Encrypted Volumes" instead of "Activate Existing Encrypted Volumes" because you don't have any existing encrypted volumes on a fresh install. Then you can choose which partitions to encrypt.

---

### Post by DiagonalArg on 2013-08-06
> **newbie-user said:**
> You have to choose "Create Encrypted Volumes" instead of "Activate Existing Encrypted Volumes" because you don't have any existing encrypted volumes on a fresh install. Then you can choose which partitions to encrypt.

I see what you mean, but I did try this.  I set devices MD1 & MD2 as "physical volumes for encryption", and then I "Configure Encrypted Volumes".  When I chose "Create Encrypted Volumes" (instead of "Activate Existing..."), then it didn't do anything other than what I had already done (set the volumes to "crypto").

Have I missed something?

---

### Post by newbie-user on 2013-08-07
Okay, so after setting the partitions to crypto, doesn't something like this show up, where you can format the encrypted volumes?
[ATTACH=CONFIG]245145[/ATTACH]

then after choosing the partition types:
[ATTACH=CONFIG]245146[/ATTACH]

---

### Post by DiagonalArg on 2013-08-07
I think I see the issue.  It's installing (finally), though I'm not sure if it's going to finish yet.

The deal is you have to do things in this order:

(1) partition the disks into pairs of identical partitions.
(Do _not_ raid together the disks and then partition them.  See here:
[https://lists.gnu.org/archive/html/bug-grub/2012-07/msg00009.html](https://lists.gnu.org/archive/html/bug-grub/2012-07/msg00009.html))

(2) Go into each partition in turn, and set each to be used for raid.

(3) Go to "Configure Software RAID" in the upper menu and create the 
RAID devices.

(4) Now go to "Configure Encrypted Volumes" (in that upper menu) and 
create the encrypted volumes.  Do _not_ do what you did with RAID, 
setting each partition to be used for  encryption.

(5) Go to the encrypted volumes and set swap and / to be mounted there.
Go to the (unencrypted) RAID array, and set /boot to be mounted there.

The key is step (4). When I set each one to be used for encryption, in 
analogy with what I did with RAID, and then tried to configure them, it
failed.

---

### Post by DiagonalArg on 2013-08-07
Grub install is working ... 
Rebooting ...
Oh, well, I'm getting that old "No Video Mode Activated" error.
Last time I had this, I did Ctl-Alt-F1, Ctl-Alt-F7 and got the 
disk decryption screen.  This time, I get the Ubuntu splash
screen, & ...

Now in BusyBox (which I don't know how to use).

Try to reboot & see if anything's different...
Nope, same.

---

### Post by DiagonalArg on 2013-08-07
Ok, this is a new problem, so I'm going to hop over to a new thread, here:
[http://ubuntuforums.org/showthread.php?t=2165948&p=12748481#post12748481](http://ubuntuforums.org/showthread.php?t=2165948&p=12748481#post12748481)

Thanks for all your help!!  :)

---


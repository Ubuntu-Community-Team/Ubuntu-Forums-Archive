---
title: "What is &quot;alternate cd&quot;?"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by zhaotianwu on 2010-11-10
Hi there, I've heard a lot about "alternate cd", what is it? Some of specific features seems only come with the "alternate cd", e.g. full disk encryption.

I'm currently using ubuntu-10.10-desktop-i386.iso, does it count as "alternate cd"? Thanks.

---

### Post by uRock on 2010-11-10
The "[alternate install CD]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate")" is used for advanced installs and it can be used for starting the upgrade from the last release before it.

The Desktop CD is considered the LiveCD, as it has the needed content to boot and run the OS from the CD itself without the use of the HDD.

---

### Post by zhaotianwu on 2010-11-10
> **uRock said:**
> The "[alternate install CD]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate")" is used for advanced installs and it can be used for starting the upgrade from the last release before it.

The Desktop CD is considered the LiveCD, as it has the needed content to boot and run the OS from the CD itself without the use of the HDD.

Thanks. Is LUKS full system partition encryption feature only available under alternate install CD? I noticed the regular installation also features a step asking you if you would like to "encrypt home folder", is it the same as the LUKS full system partition encryption feature implemented with alternate install CD? Many thanks.

---

### Post by UnrealMiniMe on 2010-11-10
> **zhaotianwu said:**
> Thanks. Is LUKS full system partition encryption feature only available under alternate install CD? I noticed the regular installation also features a step asking you if you would like to "encrypt home folder", is it the same as the LUKS full system partition encryption feature implemented with alternate install CD? Many thanks.

Don't take my word as gospel, but while you're waiting for a more informed response:
As far as I know, LUKS/dmcrypt can only be set up from the alternate install CD or through command line magic from the server CD.  (You can use it to create an encrypted partition from the command line at any time, but AFAIK encrypting your whole system can only be done in the aforementioned ways.)  It's used to encrypt entire partitions on a block-by-block basis.  Using this method allows you to encrypt your whole drive except for a small partition containing the /boot directory.  It runs in kernel-space, so it is very fast:  Writing/reading to/from the encrypted drive reportedly only carries a 3% performance penalty compared to using no encryption at all.

In contrast, Ubuntu uses ecryptfs to create an encrypted home folder on the same partition as the OS.  This uses a technology known as "filesystem encryption," because it works on the level of files and folders.  This has an advantage in terms of flexibility, and unlike LUKs/dmcrypt, it allows you to explicitly access and back up (copy/send/etc.) the raw encrypted versions of your files/directories if you want.  It has a larger performance hit though, because it runs in user-space.  (There's a benchmark of different methods floating around the net if you're interested, but I can't remember where.)

---

### Post by perspectoff on 2010-11-10
The alternate CD uses the time-honored installation methods, which are all command-line compatible.

The newer LiveCDs are "simplified" for new users and "automated" and tend to drift from the original Debian implementations. 

The text-based installers (even though using a GUI-like interface) of the alternate CDs can run on all machines, take less memory, and offer more transparent options.

They are familiar to anyone using Ubuntu/Debian for a long-time, whereas the newer LiveCDs no longer are.

I like both (the LiveCD and the Alternate CD), quite honestly. They do things a bit differently, though, and it can be confusing switching back and forth.

---

### Post by zhaotianwu on 2010-11-10
> **UnrealMiniMe said:**
> Don't take my word as gospel, but while you're waiting for a more informed response:
As far as I know, LUKS/dmcrypt can only be set up from the alternate install CD or through command line magic from the server CD.  (You can use it to create an encrypted partition from the command line at any time, but AFAIK encrypting your whole system can only be done in the aforementioned ways.)  It's used to encrypt entire partitions on a block-by-block basis.  Using this method allows you to encrypt your whole drive except for a small partition containing the /boot directory.  It runs in kernel-space, so it is very fast:  Writing/reading to/from the encrypted drive reportedly only carries a 3% performance penalty compared to using no encryption at all.

In contrast, Ubuntu uses ecryptfs to create an encrypted home folder on the same partition as the OS.  This uses a technology known as "filesystem encryption," because it works on the level of files and folders.  This has an advantage in terms of flexibility, and unlike LUKs/dmcrypt, it allows you to explicitly access and back up (copy/send/etc.) the raw encrypted versions of your files/directories if you want.  It has a larger performance hit though, because it runs in user-space.  (There's a benchmark of different methods floating around the net if you're interested, but I can't remember where.)


Thank you. I'm going to go with the alternate CD now, and LUKS system encryption is one of the major reason that attracted me from Windows XP. Can you provide any link or tutorial guides that can help a first-time user like me to install Ubuntu using alternate CD? Especially how to implement LUKS encryption for the whole system partition and /home. Thank you very much!

By the way, does it mean that my ubuntu-10.04-netbook-i386.iso that I've just downloaded is not going to be useful any more?

---

### Post by UnrealMiniMe on 2010-11-13
> **zhaotianwu said:**
> Thank you. I'm going to go with the alternate CD now, and LUKS system encryption is one of the major reason that attracted me from Windows XP. Can you provide any link or tutorial guides that can help a first-time user like me to install Ubuntu using alternate CD? Especially how to implement LUKS encryption for the whole system partition and /home. Thank you very much!

By the way, does it mean that my ubuntu-10.04-netbook-i386.iso that I've just downloaded is not going to be useful any more?

Sorry for the delayed response, but:

If you want to use the Alternate CD to encrypt your OS and swap partition with LUKS/dmcrypt, you can use [this walkthrough here]("https://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/").  It's a bit short on details, and there's probably a better one out there, but it's how I learned to do it just a few days ago.  The default settings are to use the aes:cbc-essiv:sha256 mode with a 256-bit key and sha1 hash spec.  I'm not sure exactly what the two different hashes are used for, but I do know that sha1 is considered less secure than sha256.  **I really wish I knew how to bump the hash spec up to sha256 too, but I don't...maybe someone else can give some pointers here?**

Note that you can ignore all of the "snapshots" talk if you want.  You DO need to set up an unencrypted boot partition, but layering LVM on top of the encrypted volume is not mandatory.  It's a good idea to do so though, because it's the only way to set up multiple partitions on the same encrypted volume (e.g. a root partition, a swap partition, and maybe a home partition, or however else you like to do things).

Also, if you ever want to create other encrypted volumes, you have two options:
[LIST][*]The really easy way is to go to System->Administration->Disk utility and use it for partition management.  When you create a new partition, the dialog has a built-in option for encryption.  This uses the same settings as the OS encryption, which I indicated above.  As far as I know though, it does NOT write random data on the drive beforehand, so your encrypted data will be easily distinguishable from free space that hasn't had encrypted data written to it yet.  Also, the simplicity comes at the cost of configurability, e.g. picking your own encryption settngs.  If you want to do either of those things, you'll have to do things the less easy way.
[*]The less easy way is to use [this walkthrough here]("http://www.packtp*******/article/securely-encrypt-removable-media-with-ubuntu").  It's not too bad though.  The basic idea is this:  First, you create an unencrypted formatted partition where you want your encrypted partition to be.  Then, you fill it with random data.  Then, you use cryptsetup to create a LUKS/dmcrypt volume in its place.  Then, you open that volume with your password and set up a partition on the inside.[/LIST]
Note that the latter walkthrough uses fdisk to create the initial unencrypted formatted partition.  This makes things more complicated than they need to be, and you can easily use GParted or the Disk Utility to create this partition instead.

In fact, I recommend it:  I'm not sure exactly what happened or why, but something went wrong on my first try.  The walkthrough uses fdisk to create a formatted partition without a filesystem.  A minor problem with this was that as long as I had that partition on my drive, GParted kept crashing.  The bigger problem was that after following the walkthrough to a 'T' (using fdisk, etc.), I synced hundreds of gigabytes of data to my new encrypted external drive, disconnected the drive, reconnected, and was unable to mount.  I'm not sure if things were noticeably screwed up before I even synced the data yet or not, but in any case, they were once I disconnected and reconnected the drive.  My partition table and disk geometry was all screwed up, such that the encrypted partition was bigger than my hard drive.  Disk Utility showed a tiny sliver of space past my encrypted partition, which was simultaneously interpreted as both negative space and millions of terabytes of free space (I wish it was actually the latter  ;)).  I was able to open the encrypted volume, but I couldn't mount the partition inside, and after exhausting my options trying to correct the error, I just gave up and redid the whole thing from scratch.  I don't know for sure what the problem was, but I get the feeling it had to do with fdisk getting the disk geometry wrong.

Moral of the story:  If you want to create an encrypted external drive, you can follow the walkthrough I gave for that, but ignore the initial fdisk step.  Just create an ext3/ext4/whatever partition in GParted or Disk Utility instead.  It's easier, and it just might save you a huge headache.

---


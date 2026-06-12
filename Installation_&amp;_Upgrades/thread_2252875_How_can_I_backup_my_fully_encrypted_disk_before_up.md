---
title: "How can I backup my fully encrypted disk before upgrading to Trusty from Precise?"
date: 2014-11-15
forum: Installation &amp; Upgrades
---

### Post by damonjablons on 2014-11-15
My computer is currently running **Precise**, and using full disk encryption. I'm nervous that if there are any complications when upgrading to **Trusty**, I won't be able to revert due to my disk being encrypted.

Is there a good way to create a full disk backup from an encrypted disk? Are there special instructions as to how to restore an encrypted full disk backup?

I'm also willing to un-encrypt my disk if that will make the process easier, but I'm not sure how to do that either.

(I'd also [asked this on askubuntu.com]("http://askubuntu.com/q/543687/518") a couple of weeks ago, but never received a response.)

---

### Post by Mark Phelps on 2014-11-15
You need to use an app that does not read the filesystem, but instead, simply backs up the drive sectors.

As far as I know, Clonezilla will do this -- use the saveparts option to save a compressed version of the partition.

---

### Post by sudodus on 2014-11-15
First of all, ***whatever method you choose for your backup, you should not trust it until you have checked that it really works***. This is particularly important with an encrypted system. And to do that with a full backup you need at least one more drive of at least the same size, and you should check that the system is restored and works, when you remove the original system drive and replace it with the new drive.

You can clone the system to a drive of at least the same size with ***dd*** and ***ddrescue*** and probably with ***Clonezilla***. I don't know if Clonezilla works with full disk encryption, but if it works, it is the best (fastest and safest). Those tools can also be used to create compressed images (a file or a directory with files). You should restore the system from the image to a drive of at least the same size in order to check that you have a restorable backup.

-o-

Another possibility is the run ***rsync*** or some GUI backup tool and backup your personal files and the personal setup to another drive, for example an external drive or a network drive. The personal setup is typically the content in the home directory's hidden directories and files. When logged in you will 'see' these things in clear text (decrypted), so they can be backed up in clear text by rsync when logged in with your regular user id.

In this case your backup will be directories and files in clear text, so that you can inspect the backup with standard tools (for example a file browser) and check that all important data are really backed up. After a disk crash you will have to re-install the operating system, but you should be able to do it with a separate home partition (with the backed up data).

---


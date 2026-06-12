---
title: "configuring partition shared between Ubuntu and XP"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Whatawonderfulday on 2007-04-20
Dear Ubuntufolk:

I am migrating to Ubuntu from Fedora Core 4.  I have a dual boot system with Windows XP Pro and Ubuntu 6.10, soon to be 7.04.  One partition, originally defined under XP as FAT32, is intended to be shared with Ubuntu, i.e. to be defined as accessible R/W from both operating systems.  This is a common technique.

Under FC4, I configured fstab with 'rw,userid=1234' instead of 'defaults' for this partition (call it /FAT) and things worked out.  I had a root login account (possible under FC4) and the user account where the user id was 1234.  I could access the partition from either operating system and write to it from anywhere on both operating systems (with umount and mount after the fstab changes of course).  I had no problem putting a link for files in this partition on the desktop for the two Linux login accounts.

However, under Ubuntu things are not working out so well.  First of all, since there is in Ubuntu not a root login account, as far as I can see, I defined two login accounts one with the characteristic 'desktop', the other with the characteristic 'restricted'.  This may or may not be wise, I don't really know Ubuntu well enough to know.

However, when I configured fstab for /FAT as I had done under FC4, I found that I got 'operation error' messages anytime I wanted to put a link on a Linux desktop to a /FAT file.

Question 1:  How can I configure /FAT so that I can put links on the Linux desktops?

Question 2:  How can I configure /FAT so that I can access it from both Ubuntu login accounts?  I tried to use 'userid=100' but it didn't work--it locked the /FAT partition into exclusive control by root, so that I couldn't access it at all except as a superuser.

Question 3:  What is the point of 'desktop' and 'restricted' login accounts in Ubuntu?

Thanks very much.

Whatawonderfulday

---

### Post by rich.bradshaw on 2007-04-20
The fat partition should just be automounted - you shouldn't have to do anything manually.

Look in /media there should be your drives.

It should just be on your desktop as well. If not then sudo apt-get install gconf-editor, then open gconf-editor go to apps/nautilus/desktop and tick drives show on desktop.

In Ubuntu just use sudo to do something as the root user. There is no root account.

So to update the apt index,

sudo apt-get update

will run this as if you were root. You shouldn't need to edit fstab to do anything this simple in Ubuntu.

---

### Post by Whatawonderfulday on 2007-04-20
To Rich.Bradshaw:

Yes, the FAT partition was automounted.  However, under FC4 to make the fstab changes 'take' I had to umount the FAT partiton and then mount it again.  The change to fstab worked under FC4 and was originally recommended to me by an Ubuntu user who had done the same thing in his own Ubuntu configuration for the same sort of FAT shared partition.  It is he who told me to umount and mount /FAT after changing fstab.

Clarification:  In addition to /, /boot, /home and /swap I manually defined at Ubuntu installation time, using the manual partitioning option, the /FAT partition to Ubuntu, but without a format (to keep the shared data).  Hence from the beginning the partition has been treated as a Ubuntu partition.  The problem is in being able to write to it in a routine way from a non-root account.

After the initial installation, alll the NTFS partitions from Windows were on the desktop, but none of the Ubuntu partitions, including the /FAT partition (since it had been defined to Ubuntu).  The Ubuntu partitions, including /FAT, were available through nautilus or through 'places'.

I am unable to do any internet work with Ubuntu until I install Feisty Fawn because I use a pcmcia modem (discussed on another thread).  Hence I will have to wait to install Feisty to do any updates.

The change to fstab does work: using the originally suggested settings of the Ubuntu user I can write to the /FAT partition files from the user account that I gave ownership too.  The problem is in:

a)  being able to put a link to a /FAT data set on the desktop using nautilus (I right-click on the data set in nautilus and then click on LINK, but I get the operation forbidden error); and

b) allowing more than 1 user account to have read-write privileges for the /FAT partition.

I am still puzzled.

Thanks.

Whatawonderfulday

---


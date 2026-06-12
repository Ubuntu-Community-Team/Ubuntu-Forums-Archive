---
title: "boot ini error"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by janimal on 2011-03-10
Hi all,
  My 68 year old father runs ubuntu on his x61 laptop (mostly for e-mail and some WP with OO, he usually saves any data to a usb stick)and has never had any problems before. However his battery has now died and until I go over to France next month with a new one he has to run it plugged in all the time. Unfortunately the cat managed to pull the power cord while he was using it and on boot up he was getting the boot ini error. 

Over skype (on his wife's win-box) I instructed him to put in the live cd so we could check the HD filesystem.  Unfortunately when trying to run fsck it said it couldn't run because the filesystem was mounted or in use. 

When trying to do a file system check from the disk utility that said the disk was bad.  

As he has no data on the drive I tried to get him to reformat so we could re-install. But both format and delete partition both fail saying the disk is in use. 

Trying to install from the Live CD the installation just hangs after clicking forward on the first page of the installer - ie just before the question about partitions.

Can anyone suggest a way to format the system partition from the live CD? I don't understand why it says the filesystem is mounted or in-use?

thanks in advance,
Janimal

PS. He is using Ubuntu 10.10 on a del x61 2gb ram

---

### Post by oldfred on 2011-03-10
Boot.ini is a windows boot error. Was he dual booting?

I had suggested to several other users to run fsck on a partition and they had the file in use issue. It was not related to swapoff issue, which keeps all partitions in the extended mounted since the extended is mounted if any partition is mounted. LiveCDs often mount swap.   The work around was to download and boot with Slitaz. For whatever reason, that did not say file was in use and they could run fsck.

From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

If you have windows issues then you may need to run chkdsk from a windows repair CD.

---

### Post by janimal on 2011-03-10
Hi thanks for your reply,

  I guess I have got the actual error wrong as it is a single boot only into ubuntu 

  I think the error was...

"no init found. try passing init=bootary"

 Unfortunately I'm not much more experienced than my father with ubuntu or linux in general. On first reading I don't really understand your reply. But I have got flu, it might become clearer if I google some of the terms you used ;)

---


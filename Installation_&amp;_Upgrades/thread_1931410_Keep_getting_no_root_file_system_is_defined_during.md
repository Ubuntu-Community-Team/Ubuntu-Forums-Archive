---
title: "Keep getting no root file system is defined during installation."
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by mapexmbirch on 2012-02-25
Hi I have installed ubuntu on my netbook and that was very easy.

Now I want dual boot with windows 7 64bit on my desktop. I have a SSD that plugs into a PCI slot on the motherboard I can't install ubuntu on that because it needs drivers which I don't think will work with Linux. But I have a secondary HDD that I have created a 18GB partition on and it should be able to install on that but I get 'no root file system is defined' I have selected the partition that I want and then click install and get that message.

The partition is currently formatted for NTFS and it has a 2GB partition 'unallocated' behind it because this stops the HDD from crashing windows for some reason.

I can format the whole HDD because I have a back up but this is a last resort.

Thanks :)

---

### Post by darkod on 2012-02-25
It can't install on ntfs. Boot windows and delete that partition. Leave the space as unallocated.

Then you can either use one of the auto methods and install into that unallocated space, or you can use the manual partitioning which is recommended for greater control.

In the case you are creating partitions manually make sure you create one ext4 partition with mount point / (root). That's why you are getting that message, you are trying to continue without root partition specified. It will not create the ntfs into / automatically, you need to delete it and create ext4 logical partition in that place, with mount point /.

The partitions you create can be primary too, just don't forget than you can have max 4 primary partitions on the hdd, or 3 primary and 1 extended which can have many logical partitions inside.

---

### Post by mapexmbirch on 2012-02-28
Thanks that worked

---

### Post by saidii89 on 2012-05-15
a lot of users faced such problem and the solution to it is pretty simple
 
make sure that the partition file system [you wish to install linux, ubunto or backrack on it] is ext4, ext3 or ext2 [not fat32 or ntfs]
 
then mount "/" on it, how? easy: 
1- on the installation process press [change] on the partition you wish to use
 
2- make sure [do not use this partition] scroll is not chosen, scroll to ext4, ext3 or ext2
 
3- and on "mount" field write "/"
 
4- when clicking ok then next a message will appear saying something like [swap area was not defined, do you wish to continue or choose a swap area? because bla bla bla..], click "ok" and continue or click "go back" and choose another partition and click change, on the file system scroll choose [swap] and click ok and next
 
this will solve both "no root file system is defined" and the "swap area" message, if you still get the swap area message then on step 4 mount "/swap" to the partition
 
**AND THIS SOLVES IT!**
 
every time anyone need solutions don't hesitate to search for help
 
ask me if you need something and I can help I will do it, I don't log to forums a lot, I found this thread while searching on google and I copied this answer to all the threads with the same problem, so If you need contact here it goes ->

 [http://www.twitter.com/saidii89](http://www.twitter.com/saidii89)
 [http://www.facebook.com/saidii89](http://www.facebook.com/saidii89)
 [http://www.formsrping.me/saidii89](http://www.formsrping.me/saidii89)
 [http://www.saidi-theory.blogspot.com]("http://www.saidi-theory.blogspot.com/")
 
brought to you by Sa'eed Awad
[Saidi Theory Solutions] by Sa'eed Awad

---


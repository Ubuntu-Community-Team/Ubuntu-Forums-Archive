---
title: "Vista Installer Deleted Ubuntu Partition"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by s3MA00RRNY on 2010-07-31
I'm having a really strange problem. I recently resized my home partition so I could install Windows at the end of the drive. Then I created an NTFS partition in that space, and marked it as bootable. After that I went into the Vista installer and tried to use that partition. I guess Vista doesn't like logical partitions, because it didn't work.

So I got the stupid idea of trying to delete that partition and recreate it from the Vista installer. Now my system partition disappeared. :(

This is what my layout looked like before:


[LIST]
[*]Boot
[*]Extended
[LIST]
[*]Ubuntu
[*]Swap
[*]Linux From Scratch
[*]Home
[/LIST]
 
[/LIST]
And this is what it was supposed to look like:

[LIST]
[*]Boot
[*]Extended
[LIST]
[*]Ubuntu
[*]Swap
[*]Linux From Scratch
[*]Home
[*]NTFS
[/LIST]
 
[/LIST]
And this is what Vista did:

[LIST]
[*]Boot
[*]Extended
[LIST]
[*]Empty
[*]Swap
[*]Linux From Scratch
[*]Home
[*]Empty
[/LIST]
 
[/LIST]
I still have my home, so I can install if I *have  *to, but I really don't want to. Testdisk successfully finds the partition, so we'll see how that works. I'm just wondering why Vista did this, and how I can prevent it from happening again.

---

### Post by sydbat on 2010-07-31
> **pcdude2143 said:**
> I'm having a really strange problem. I recently resized my home partition so I could install Windows at the end of the drive. Then I created an NTFS partition in that space, and marked it as bootable. After that I went into the Vista installer and tried to use that partition. I guess Vista doesn't like logical partitions, because it didn't work.

So I got the stupid idea of trying to delete that partition and recreate it from the Vista installer. Now my system partition disappeared. :(

This is what my layout looked like before:


[LIST]
[*]Boot
[*]Extended
[LIST]
[*]Ubuntu
[*]Swap
[*]Linux From Scratch
[*]Home
[/LIST]
 
[/LIST]
And this is what it was supposed to look like:

[LIST]
[*]Boot
[*]Extended
[LIST]
[*]Ubuntu
[*]Swap
[*]Linux From Scratch
[*]Home
[*]NTFS
[/LIST]
 
[/LIST]
And this is what Vista did:

[LIST]
[*]Boot
[*]Extended
[LIST]
[*]Empty
[*]Swap
[*]Linux From Scratch
[*]Home
[*]Empty
[/LIST]
 
[/LIST]
I still have my home, so I can install if I *have  *to, but I really don't want to. Testdisk successfully finds the partition, so we'll see how that works. **I'm just wondering why Vista did this**, and how I can prevent it from happening again.I think your signature answers that question...

Windows likes to be first. I suspect Vista figured the first available partition space rightfully belonged to it. I also believe that Windows needs to be put onto a Primary partition (at least it used to).

---

### Post by s3MA00RRNY on 2010-07-31
Thanks for your answer. I figured it was something like that. I'll try resizing my extended partition and installing Vista again now that I'm back in business. I just hope it doesn't wreck anything else. Even though I have a backup it's a pain to restore.

---

### Post by oldfred on 2010-07-31
Windows does not have to be first, but it just about has to be installed in a primary partition. The only way to install to an extended is to have a windows install in a primary so it can boot thru that primary partition.

To get each MS to have its own boot loader make a primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by JK3mp on 2010-07-31
Windows 7 works a WHOLE lot better with other partitions/OS installations. I was able to easily install it on an already partitioned drive. Vista was a pain. Gotta love MS.

---


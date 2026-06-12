---
title: "installation problems."
date: 2006-03-07
forum: Installation &amp; Upgrades
---

### Post by Felix21685 on 2006-03-07
hey guys,

just burned the ISO onto a CD and rebooted my machine.

I have windows XP on my first partition and a 5GB empty partition 
which are both on my WD Raptor (SATA)

I get the following error when I try to install UBUNTU

"the boostrap program exited with an error (return value 1).
check /target/var/log/bootstrap.log

on my D drive which is the target.. there is no bootstrap.log

thanks for the help in advance,

-Felix

---

### Post by Felix21685 on 2006-03-07
you guys think it might be a bad cd?

---

### Post by aysiu on 2006-03-07
Could be.

Read more here:
[http://ubuntuforums.org/showthread.php?t=76316](http://ubuntuforums.org/showthread.php?t=76316)

---

### Post by Felix21685 on 2006-03-07
what do they mean by breezy on that thread?
sorry im a newb

---

### Post by Felix21685 on 2006-03-08
I think I figured out why it didn’t work for me
First of all I didn’t assign a swap space.
And I forced it to do FAT32..i hear this is both ok with linux and I could read files from windows. Once I let it do EXT3 or whatever its called it worked ok on another machine. so ill try on this one in a little bit.

---

### Post by Sutekh on 2006-03-08
> **Felix21685]what do they mean by breezy on that thread?[/QUOTE]'Breezy' refers to the nickname of the current Ubuntu release said:**
> I think I figured out why it didn&#8217;t work for me
First of all I didn&#8217;t assign a swap space.
And I forced it to do FAT32..i hear this is both ok with linux and I could read files from windows. Yes this is correct, but you shouldn't use it for essential Linux partitions (like where programs will be installed).  Its okay to have a FAT32 partition for shared data.  I believe this is because FAT32 doesn't support Linux (POSIX) permissions.

[QUOTE=Felix21685]Once I let it do EXT3 or whatever its called it worked ok on another machine. so ill try on this one in a little bit.[/QUOTE]
Yep ext3 is the filesystem you should use for Ubuntu.

---

### Post by Felix21685 on 2006-03-08
sweet thanks for the quick replies ..
seems like a very informative forum

---

### Post by DivaRachel on 2006-03-21
[QUOTE=Felix21685]
I get the following error when I try to install UBUNTU

"the boostrap program exited with an error (return value 1).
check /target/var/log/bootstrap.log[/QUOTE]
I got the same error when installing last week. Installing from the CD which was shipped from ubuntu. Version 5.10.

Installing Ubuntu on Pentium 1 PC with 8GIG hard drive and 2GIG secondary HD. 256 RAM (I think?). I have been able to install Win98/2k/XP on this machine, altho XP and 2K running slowly. Which is why I thought Ubuntu would be a good alternative. PC is to be used by children (kids games and barbie.com). That's it.

Not sure how to partition properly. Used the 'partition helper guide' that comes with the install. Didn't touch the 2GIG HD, which is windows-FAT32 formatted, and houses old 'My Document' directory. Would like to keep as-is. (of I could unplug this drive from the motherboard entirely, if you think that's going to help).

The partition guide created 2 parititions in the 8 gig drive. If I remember correctly, its a /boot partition and another one. Assuming the 'paritition guide' is not to be trusted, how should I re-partition my drive?

Appreciative of any info. THANKS!

---

### Post by tuxinvader on 2006-03-21
[QUOTE=DivaRachel]I got the same error when installing last week. Installing from the CD which was shipped from ubuntu. Version 5.10.
Installing Ubuntu on Pentium 1 PC with 8GIG hard drive and 2GIG secondary HD. 

<snip>

Not sure how to partition properly. Used the 'partition helper guide' that comes with the install. Didn't touch the 2GIG HD, which is windows-FAT32 formatted, and houses old 'My Document' directory. Would like to keep as-is. (of I could unplug this drive from the motherboard entirely, if you think that's going to help).

<snip>

Appreciative of any info. THANKS![/QUOTE]

Hi,

Shouldn't need to unplug the 2gig drive, just don't touch it in the partitioner ;)

On the 8gig, you probably want the first partition to be setup as /boot with 100mb and the bootable flag set, the second for swap with 512mb. After this you can either stick the rest of it on root (/) or split it between root and /home. Personally I use the ext2 filesystem for boot and reiserfs for my root and home partitions becuase it's faster than ext3. 

If you decide to split root and home it will be easier for you to preserve your home directory should you ever decide to try another distro.

I hope that's clear?

---

### Post by DivaRachel on 2006-03-21
[QUOTE=tuxinvader]Hi,

Shouldn't need to unplug the 2gig drive, just don't touch it in the partitioner ;)

On the 8gig, you probably want the first partition to be setup as /boot with 100mb and the bootable flag set, the second for swap with 512mb. After this you can either stick the rest of it on root (/) or split it between root and /home. Personally I use the ext2 filesystem for boot and reiserfs for my root and home partitions becuase it's faster than ext3. 

If you decide to split root and home it will be easier for you to preserve your home directory should you ever decide to try another distro.

I hope that's clear?[/QUOTE]
Hi, 
Its not 100% clear, but I gather I will need 3 partitions on my 8 gig HD:
1. /boot. 100mb
2. /swap space: 512mb
3. /root : the rest of the spage available.

When re-partitioning, try to specified filesystems. :-k (I don't remember that being an option on my first try, but i will look for it.)  

I will try it out this weekend. Thanks.

---


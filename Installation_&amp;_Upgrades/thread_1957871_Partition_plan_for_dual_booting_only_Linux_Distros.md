---
title: "Partition plan for dual booting only Linux Distros."
date: 2012-04-13
forum: Installation &amp; Upgrades
---

### Post by buntush on 2012-04-13
Can someone quickly review the partition plan below for dual booting Kubuntu and OracleLinux? Any suggestions highly appreciated.

Many thanks for your time and attention.

/dev/sda (225GB)
+-/dev/sda1      /boot     (500MB, ext2)  Kubuntu11.10
+-/dev/sda2      data      (100GB, ext4)  Shared (non OS files)
+-/dev/sda3      swap      (3GB, ext3)    Shared
[COLOR=Blue]+-/dev/sda4      extended  (120GB, ext4)
   +-/dev/sda5   /tmp      (2GB, ext4)    Kubuntu11.10 
   +-/dev/sda6   /home     (15GB, ext4)   Kubuntu11.10  
   +-/dev/sda7   /         (20GB, ext4)   Kubuntu 11.10
   +-/dev/sda8   /boot     (500MB, ext4)  OEL6.2
   +-/dev/sda9   /tmp      (2GB, ext4)    OEL6.2
   +-/dev/sda10  /home     (10GB, ext4)   OEL6.2
   +-/dev/sda11  /         (15GB, ext4)   OEL6.2
   +-/dev/sda12  /oracle   (20GB, ext4)   Oracle11gR2 + datafiles + tools
   Free Space = 15GB[/COLOR]

---

### Post by cortman on 2012-04-13
I don't know why it wouldn't work, although I'm a little baffled as to why so many partitions. Boot and /tmp can both be part of the root partition. But that's personal choice.
What exactly is it you are wondering?

---

### Post by oldfred on 2012-04-13
I agree with cortman. It should work, but I do not think for Kubuntu you need extra system partitions.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

Separate /home is ok but if you put most data into the data partition there is less need for a separate /home. 

Not sure what OracleLinux uses, but sharing data can be an issue unless you make sure UID & GID are the same. Ubuntu makes first user 1000, but some use 500.

Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

[http://ubuntuforums.org/showthread.php?t=1806443](http://ubuntuforums.org/showthread.php?t=1806443)
Post #p by SeijiSensei
> I do try and enforce a common set of /etc/passwd and /etc/group files across distros so that user and group names map correctly. I've generally adopted Debian/Ubuntu's numbering which starts users at UID=1000 for RHEL/CentOS to maintain consistency. Just create master copies of /etc/passwd, /etc/group, and /etc/shadow and copy them to all the distros. If you run servers, you may need to futz with with the various unprivileged users like "www-data" in Ubuntu which is the equivalent of "httpd" in RHEL-flavored distros.


---

### Post by buntush on 2012-04-13
Thanks Cortman. I think you're correct on unnecessary partitions and having /tmp, /boot as separate partitions.

Here is a plan suggested by my another friend which looks good to me:

1 primary partition for Kubuntu (20 GB)
1 primary partition for OL 6.2 (20 GB)
1 primary partition for swap Kubuntu/OL 6.2 ( 5 GB )
1 extended partition (ext3) for Oracle db files and FRA (30 GB) 
1 extended partition for a shared disk (100 GB) DATA (non OS)
50GB free

The only thing is I already have 100GB "data" partition (non OS files) as a primary partition that is 75% filled up. So I am planning to create SWAP inside extended partition instead of as a primary so I will have 3 primary + 1 extended. Or may be during installation of first OS (Kubuntu) I will boot into LiveCD mode and try to move "data" partition into extended and delete the primary one later. Not sure if that can be done, else will go as mentioned above (SWAP inside extended).

I just want to make sure I am on a right path before proceeding hence asking for opinions from the individuals that played a lot with these things :)

Thanks again for your attention.

---

### Post by buntush on 2012-04-13
Thanks much oldfred. Your comments and the information in links you sent make sense and I am coming to a conclusion not to have unnecessary partitions.

I planned to follow that path only because I read somewhere about these recommendations but I think on home system it may not be relevant.

Can you please check my previous reply about a new plan that I have now and advise if you feel something is wrong?

---

### Post by darkod on 2012-04-13
I wouldn't recommend you trying to move partition with 75GB from primary to logical (inside extended).

Swap has no problem being a logical partition, in fact none of the ubuntu partitions care about that.

So, try to achieve your setup with as little partitions moving as possible. Every partition move or resize has a certain amount of risk for your data.

---

### Post by oldfred on 2012-04-13
New plan looks good. I also agree with Darko on swap as logical. Normally the default install of Ubuntu makes swap a logical partition.

I am not familar with Oracle Linux. 
Does its install or database have any specific requirements? Some other systems than Ubuntu, also have to have primary partitions or specific formating, sizes or configurations.

---

### Post by buntush on 2012-04-13
That's very valuable advice Darko. I was not aware of possibility of data loss due to move/resize of partition. I will keep that in mind.

I will now go with installation and come back later here to mark the thread as solved.

Thank you very much.

---

### Post by DWade on 2012-04-13
Or you could change the hard drive to GPT [GPT stands for GUID Partition Table (GPT)] and have as many primary partitions as you want.

---

### Post by cortman on 2012-04-13
I don't know if I'd mess with GPT at this point. Your new partition plan looks great buntush.

---

### Post by oldfred on 2012-04-13
I also like gpt especially for Linux only installs. And Arch recommends it for Linux only SSDs. 

But I do not know if Oracle works with it or not. And I have not tried with Kubuntu. So unless Oracle also suggests gpt I would not try that now.

I did have minor issues with gpt on 10.04, but none on 10.10 or 12.04 as long as I created a bios_grub. If drive was over 1TB then it may make more sense & gpt would be required if drive was over 2.2GB.

---


---
title: "My Partitioning scheme for performance!"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by yooozy on 2011-09-12
I'm reinstalling ubuntu 11.04 on my old machine, to get better performance and stability!

After a long research, I come up with this partitioning plan for a 160 GiB HD  :
**what do you think?**

/boot             - 100 MiB/ext2/readonly
/ (root)           - 1 GiB
/swap            - 1 GiB/swap
/tmp              - 1 GiB/ext4
/usr               - 8 GiB/ext4
/var               - 8 GiB/ext4
/usr/local        - 2 GiB ext4
/home             - rest/ext4 
/home/public    - 4 GiB ntfs (to share across platform)    


computer specs:

Processor: Intel(R) Celeron(R) CPU 2.13GHz
Memory        :  1GiB
Hard disk: 160 GiB


Note here that I'm installing ubuntu from scatch without duel boot

---

### Post by Blasphemist on 2011-09-12
I have no way to point to specific truth about this but unless this is a server I doubt very much that you'll notice any performance improvement with all of these partitions versus one / partition and a swap. 

Are you or did you have bad performance? I expect running a light weight distro based on ubuntu has more chance of improving performance and still keepin it in the family so to speak. Bodhi is my favorite light weight ubuntu based distro.

Should you ever want to try other distros and have this already in place, this will complicate things for you.

---

### Post by haqking on 2011-09-12
> **yooozy said:**
> I'm reinstalling ubuntu 11.04 on my old machine, to get better performance and stability!

After a long research, I come up with this partitioning plan for a 160 GiB HD  :
**what do you think?**

/boot             - 100 MiB/ext2/readonly
/ (root)           - 1 GiB
/swap            - 1 GiB/swap
/tmp              - 1 GiB/ext4
/usr               - 8 GiB/ext4
/var               - 8 GiB/ext4
/usr/local        - 2 GiB ext4
/home             - rest/ext4 
/home/public    - 4 GiB ntfs (to share across platform)    


computer specs:

Processor: Intel(R) Celeron(R) CPU 2.13GHz
Memory        :  1GiB
Hard disk: 160 GiB


Note here that I'm installing ubuntu from scatch without duel boot

for a home machine then nothing much more than a whole / or a / and a /home should do.

If you must go down this route then as an example (open to conjecture)

/boot (if you use a lot of kernel or with kernel updates this can get full so say 100-150 maybe

/  1-2 gb

/swap

/home (size based on data, as large as you need

/tmp (min of 500

/usr (depends on what you will install

/var (min of 500...i put my backups here and rsync them to an external so size is upto you

all can be ext4 though i would make /boot ext2 as it dont change much and /usr2 as it too doesnt really need journalling but upto you.

there is also argument for a /usr/local and a /opt

but like i say i doubt you will see much performance issues with just a / and a /home with a home system

---

### Post by yooozy on 2011-09-12
[@[COLOR=Black]**_Blasphemist:_**[/COLOR]]("http://ubuntuforums.org/member.php?u=1165520")

I've already tried xubuntu, it's a lot faster than ubuntu but I'm convinced to stick to ubuntu due to various reasons ( mainly different tasks and too many programs)
[COLOR=Blue]@[/COLOR][B]haqking: 
[/B]I already use the scheme you suggested, I think it's not best choice if planning to reinstall without loosing personal data and configuration, am I wrong?!

---

### Post by haqking on 2011-09-12
> **yooozy said:**
> [@[COLOR=Black]**_Blasphemist:_**[/COLOR]]("http://ubuntuforums.org/member.php?u=1165520")

I've already tried xubuntu, it's a lot faster than ubuntu but I'm convinced to stick to ubuntu due to various reasons ( mainly different tasks and too many programs)
[COLOR=Blue]@[/COLOR][B]haqking: 
[/B]I already use the scheme you suggested, I think it's not best choice if planning to reinstall without loosing personal data and configuration, am I wrong?!


The paritioning doesnt relate to losing personal data and configuration as much as whether you back things up or not.

If you installed everything to /

you can still have your system up and running easily after failure if you have the necessary backups of 

/home 
/etc 
/usr/local 
/var

I mean having /home mounted in a seperate partition can be useful for a quick reinstall but you still need to have backups regardless

---

### Post by yooozy on 2011-09-12
what do you mean?! I have to backup even if I have  separated partitions?!
as for installing everything in / , I agree it will do the job but it's a lot different from many perspectives IMO

BTW how to backup and restore everything at once?


thank you:)

---

### Post by haqking on 2011-09-13
> **yooozy said:**
> what do you mean?! I have to backup even if I have  separated partitions?!
as for installing everything in / , I agree it will do the job but it's a lot different from many perspectives IMO

BTW how to backup and restore everything at once?


thank you:)


Of course you have to backup.  So you have seperate partitions, and your hard drive fails ? then what ?

Always have backups of personal and configuration data.

I am not telling you to install everything into root /, i mean if you did as long as your backups of certain directories are done then a restore is relatively simple.

as for how to backup, there are many tools.  from command line .tar to simple backup (sbackup) in repos, or using dd, clonezilla, remastersys etc.

I personally have a cron job running for a backup to my /var which daily syncs to a external hard drive, the method depends on your needs and data.

I am also not saying dont use the seperate partitions (i have many) im saying they are not necessarily required and not necessarily needed on a home system, and the performance difference will be negligible

---

### Post by Herman on 2011-09-13
If you have one or two large capacity hard disks, you might be able to eck a little bit more performance from a multiple partition scheme by using 'short stroking'. The idea of 'short stroking would be to try to arrange for whichever partitions you think will demand the most hard drive reads and writes to the outside perimeter of the hard disk(s). For example,                          [Unconventional partition setup]("http://ubuntuforums.org/showthread.php?t=1687792&highlight=Short+Stroking"). It probably won't be much help just for normal sized hard disks though, (<500 GB).
If you have enough hard disks to create a RAID array though, that would be a lot better than 'short stroking'. 
You still need to make backups no matter how many partitions you make, but some kinds of RAID (mirroring RAID, which give you 'redundancy', would help except of course if the machine gets struck by lightning or something like that. It's pretty hard to get away without the need to keep any backups at all. (Assuming you value your data).  :)

Personally for general purpose PC I prefer one single partition with maybe a swap area if you want to hibernate, but I like swap files instead of a swap partition, I prefer to shut down than hibernate. 

It's up to you though, it's your computer. Just remember when you come back here wanting help because one partition or another is filled up and you need to resize all your partitions and go through a lot of un-necessary work and hassles that we told you so. :)

---

### Post by YesWeCan on 2011-09-13
> **Herman said:**
> Personally for general purpose PC I prefer one single partition with maybe a swap area if you want to hibernate, but I like swap files instead of a swap partition, I prefer to shut down than hibernate.
Ah someone who uses a swap file. Good. I'm thinking of doing this myself - I'm not sure why Ubuntu desktop installer doesn't default to this (because it is simpler for the novice). I'm not sure whether you are saying a swap partition is needed if you want to hibernate...is Ubuntu different from Windows which can hibernate and uses a swap file?

---

### Post by BeowulfNode on 2011-09-13
I personally believe that simplicity vs optimising for performance at the cost of complexity, simplicity wins the time race. if you want max hdd performance use raid10 and/or ssd.

I like 1 drive or raid
per OS
per box or virtual machine

then additional HDDs for data

if you want to change OSes in a box regularly use trayless hdd rack/caddies to change OS hdds.

I don't know about you but I seem to have gathered a lot of HDDs over the years, might as well use them

---

### Post by dino99 on 2011-09-13
what you need, nothing else:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Herman on 2011-09-13
> Ah someone who uses a swap file. Good. I'm thinking of doing this myself  - I'm not sure why Ubuntu desktop installer doesn't default to this  (because it is simpler for the novice). I'm not sure whether you are  saying a swap partition is needed if you want to hibernate...is Ubuntu  different from Windows which can hibernate and uses a swap file?@ Yes We Can
:) Yes, we can use a swap files and hibernate, I have used the following excellent how-to many, many times, and have had good results from it,                           [HOWTO: Use swapfile instead of partition and hibernate]("http://ubuntuforums.org/showthread.php?t=1042946&highlight=make+swap+file+hibernate")- by iva2k.

More recently though, I found out that it's possible to create a *dynamic* swap area and that seems like a great idea to me when a person wants to conserve disk space usage when installing in a USB flash memory stick or small computer like my EeePC 4G. - A dynamic swap file shrinks when not needed and more is created as swap is required. Since I set swappiness to 10 in flash installations and have more than enough RAM that shouldn't be too often so it's a great way to conserve disk space. 
I'm not sure if it would help extend the life of the flash memory for an installation (USB or SSD) or not but it seems like it could conceivably help to randomize disk erases and writes a little too, but I'm only guessing about that.
It's simple to install '[Dynamic Swap Space Manager]("http://pqxx.org/development/swapspace/")' from our Ubuntu Software Center or Synaptic or 'sudo apt-get install swapspace'.
```
sudo apt-get install swapspace
```There's nothing the user needs to worry about configuring or anything, just install and enjoy.   :)
However, I did notice that the option to hibernate is missing.

---

### Post by Herman on 2011-09-13
One of the reasons in favor of multiple partition schemes to try to make an operating system faster seems to come from the Arch Linux people, where for a while they advocated the use of rieserfs for some partitions because it used to be up to 15x faster than ext3 for small disk writes.  
I use to like reiserfs for that reason too, it really did make a noticeable difference, especially in flash memory, it was measurable, and even cut installation times.
As soon as I tried out ext4 and wasn't able to pick a noticeable or measurable performance difference I decided to stick with just ext4. 

Even though I'm arguing in favor of a single partition scheme, I don't mean to say that multiple partitioning is never any good. A point in favor of GNU/Linux operating systems' ability to use many partitions is its ability to be able to install across more than one disk. Foe example I have my EeePC 4GB SSD installed with /  and I have /boot and /home in an 8GB camera card. 
So a person could for example install in a number of small disks like several SUB flash memory sticks on a USB hub or something. I have not yet read about anybody doing that but it seems like kind of a cool idea. (he-he) Maybe not so economic though, as hard disks are not too expensive now. :)

With hard disks, installing across more than one hard disk would probably produce a small speed boost because it would spread reads and write work out over more independently working sets of read and write heads.
I though Bucic might be on to something with the idea of short stroking in the thread I linked to earlier, and was a little dissappionted to read at the end that the results didn't seem to justify the effort.
Maybe with larger capacity hard disks though, it would have worked better, or with a slightly different physical location for some of the partitions?, (I'm not sure).

I have a pile of hard disks sitting around still in sealed in their wrappers waiting for me to try a six disk RAID 0 installation to see if it's faster than my OZC Vertex SSD, or maybe I'll chicken out and make a RAID 5 again and just have one disk for redundancy or something like that. RAID 0 for maximum speed seems like it would be fun. :)

---

### Post by yooozy on 2011-09-14
> **haqking said:**
> 

as for how to backup, there are many tools.  from command line .tar to simple backup (sbackup) in repos, or using dd, clonezilla, remastersys etc.

I've just tried deja dup, it's amazing!!!
> **haqking said:**
> 

I am also not saying dont use the seperate partitions (i have many) im saying they are not necessarily required and not necessarily needed on a home system, and the **performance difference will be negligible** 

ok ok agreed on this one! but wait a minute here what about stability?! I mean if you wanna keep settings and everything after re-installation and upgrades.... I see a lot of lost-after-upgrade threads these days!   

> **Herman said:**
> 

  ....but some kinds of RAID (mirroring RAID, which give you 'redundancy', would help except of course if the machine gets struck by lightning or something like that. 

> **BeowulfNode said:**
> I personally believe that simplicity vs  optimising for performance at the cost of complexity, simplicity wins  the time race. [B]if you want max hdd performance use raid10 and/or ssd.
[/B]

wow this is a cool idea! say for example I got a powerful machine with 1Tb HDD. replacing it with 4x250 GiB would be better! yeah in multiple levels in fact

I'm looking forward to try that since I got a lot of old HDD's

what if I use each drive for one component for example:

HDD01 /boot, /root, /swap
 HDD02 /home
HDD03 /usr/local, /var

What do you think?

---

### Post by haqking on 2011-09-14
> **yooozy said:**
> 
 

ok ok agreed on this one! but wait a minute here what about **stability**?! I mean if you wanna keep settings and everything after re-installation and upgrades.... I see a lot of lost-after-upgrade threads these days!   

?


Stability and performance are different things.  again like i said i didnt say not to, im saying that having seperate partitions for certain directories will not necessarily increase performance (if on same drive for example)

as for restoring settings then yes it can help if in different partitions but not much different to having backup, you need a backup regardless (hard disk failures).  If you have **/home** on a seperate parition but on same drive and the dirve fails the seperate partition didnt help you.  if it is on different drive and that fails you still need a back up of it to restore it.

---

### Post by YesWeCan on 2011-09-14
[http://www.youtube.com/watch?v=96dWOEa4Djs](http://www.youtube.com/watch?v=96dWOEa4Djs) :p

---

### Post by haqking on 2011-09-14
> **YesWeCan said:**
> [http://www.youtube.com/watch?v=96dWOEa4Djs](http://www.youtube.com/watch?v=96dWOEa4Djs) :p


Dunno what i would prefer, the 24 256GB RAID system or just the money it would take to buy them and spend it frivivously instead ;-)

---

### Post by YesWeCan on 2011-09-14
> **haqking said:**
> Dunno what i would prefer, the 24 256GB RAID system or just the money it would take to buy them and spend it frivivously instead ;-)

I could only afford a 4 HDD RAID 10's worth of pleasure. :(
Good news is that it is a constant source of pleasure none the less. :)

---

### Post by haqking on 2011-09-14
> **YesWeCan said:**
> I could only afford a 4 HDD RAID 10's worth of pleasure. :(
Good news is that it is a constant source of pleasure none the less. :)


Shame the video wasnt using Linux, be interested to see a benchmark comparison on that between the 2

---

### Post by YesWeCan on 2011-09-14
2000MB/s LOL.

Hey, no one has mentioned partitioning of RAM. How about 32GB and a few ramdisks?

I just created a 2GB ramdisk...
[COLOR="DarkSlateBlue"]mkdir /tmp/ramdisk[/COLOR]
[COLOR="DarkSlateBlue"]mount -t tmpfs -o size=2G tmpfs /tmp/ramdisk[/COLOR]
and filled it with zeros
[COLOR="DarkSlateBlue"]dd if=/dev/zero of=/tmp/ramdisk/bigfile bs=10M[/COLOR]
resulting in...
[COLOR="green"]dd: writing `/tmp/ramdisk/bigfile': No space left on device
205+0 records in
204+0 records out
2143285248 bytes (2.1 GB) copied, 0.880746 s,[/color] [COLOR="Red"]2.4 GB/s[/COLOR] 8-[ 8-)

---


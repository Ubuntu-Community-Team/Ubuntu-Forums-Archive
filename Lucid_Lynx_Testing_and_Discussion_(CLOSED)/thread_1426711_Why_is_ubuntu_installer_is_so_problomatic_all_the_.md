---
title: "Why is ubuntu installer is so problomatic all the time?"
date: 2010-03-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-03-10
every time i download a new daily version there are other problems with the installer first of all none of the recent versions i downloaded latetly detect i already have an operating system on the computer and i have two os i have windows seven on sdb and server 2008 on sda. 
 
but the installer said no os is detected also today installer has gave me an error when i chose create partitions automaticly and when i pressed continue any way it immediatly jumped to the page where you put name an password so i stoped the installer because i didn't knew where it would be install and i can choose the option to use the biggest free space because if it doesn't detect the server 2008 on sda who know what he would do to he's partition. 
 
and also the old problem i had with installing grub 2 that after is forcing me to manually install grub 2 on bote sda and sdb via live cd is still not solved.
 
any way i'm hopping that a final proper installer would be released soon because it's a big problem to download new version and only then detect that the installer is not so good and then you don't install anything like i did today or you need to download alternate cd which can also be problomatic at times.
 
thanks in advance.

---

### Post by 23meg on 2010-03-10
Is this a genuine question? Do you really want to learn *the reason* why the installer has been problematic in your experience?

[QUOTE=aviramof]any way i'm hopping that a final proper installer would be released soon[/QUOTE]

Unless you filed good bug reports on the issues you encountered, there's no reason for you to hope for assume that. [https://wiki.ubuntu.com/DebuggingUbiquity](https://wiki.ubuntu.com/DebuggingUbiquity) may help.

---

### Post by aviramof on 2010-03-10
yes i'm tierd of this that every time i download a new version i'm not sure i would be able to install it at all as it did today or the fact that i need to install grub 2 manually all the and if there is something i can do about it like report my computer setting to the developers group who's in charge about the installer and grub 2 or anything eles that would be great i want to do what i can to get this problem solved once and for all because i don't think that my computer hardware and etc is that uniq that the installer should have so much problems all the time.
 
any way i would try tommorw to install the betafreeze version via live cd not just the install option and hopefully i would be able to report problems directly during the installtion process.

---

### Post by ankspo71 on 2010-03-10
Hi,
```
ubuntu-bug grub2
```
```
ubuntu-bug ubiquity
```
Be sure to let them know about your drive setup too, like ata, sata, (or both), raid?, etc.

For partitioning issues, it might be better to boot into a live session, run gparted to do all of your partition work, then use the ubuntu installer to install ubuntu. This won't fix the ubuntu installer problems you mentioned, but it should help you get ubuntu installed with less partitioning hassle.

Also, there is a link to "update this installer" once the the installer (ubiquity) starts. This might or might not help, but it's there.

Is this only a Lucid problem, or has this also happened with past versions?
Good luck.

---

### Post by VMC on 2010-03-10
> **23meg said:**
> Is this a genuine question? Do you really want to learn *the reason* why the installer has been problematic in your experience?



Unless you filed good bug reports on the issues you encountered, there's no reason for you to hope for assume that. [https://wiki.ubuntu.com/DebuggingUbiquity](https://wiki.ubuntu.com/DebuggingUbiquity) may help.

I wish they would update that wiki page. Once someone comes across Feisty or Hardy names, they may assume it doesn't apply to current testing. The "install.py" still applies. A good read otherwise.

I realized ,after todays *ubi-partman* error that there actually is a log for it.

---

### Post by aviramof on 2010-03-11
i don't think i have this problem when i installed ubuntu 8.10 and perhaps not 9.04 or 9.10 but i'm not sure any way will see once today version would be released and update the installer want really work if i'm using the same day version there is nothing to update or at least there shouldn't be.

---

### Post by ranch hand on 2010-03-11
> **aviramof said:**
> i don't think i have this problem when i installed ubuntu 8.10 and perhaps not 9.04 or 9.10 but i'm not sure any way will see once today version would be released and update the installer want really work if i'm using the same day version there is nothing to update or at least there shouldn't be.
I certainly hope that you are talking about 8.10-testing, 9.04-testing and 9.10-testing.  I doubt that though as I know there were problems with 9.10-testing, I was there.

You can't compare a testing OS to a stable OS.  It is unfair to each and not a valid comparison in the first place.

I really do hope you are filing bugs and not just complaining that an alpha is acting like an alpha.

---

### Post by aviramof on 2010-03-11
i do fill bugs but i can't always do that not via the installer anyway because my connection is pppoe and i can't connect via normal installer only via live cd option.

---

### Post by ankspo71 on 2010-03-11
Hi,
Just to clarify what I was saying... 
If a user has trouble using ubiquity, the person has the option to update ubiquity without having to download another iso or burn another cd, which is good if the person decides to try the install again a few days later. 

Also, I asked if the OP had problems with previous versions only to find out if the problem has been ongoing to find out if the problem is Lucid specific or not. Sometimes they're not.

I just don't want to see anyone here have a more difficult time over something I said or asked. Back to testing what I was in the middle of testing...:D

---

### Post by aviramof on 2010-03-11
download a new iso is not so difficult and i have an RW dvd which cost very little so it's a problem to burn a new cd the difficult part in updating the installer is that you never know weather the new installer is better or worse then the previous one.

---

### Post by VMC on 2010-03-11
> **ankspo71 said:**
> Hi,
Just to clarify what I was saying... 
If a user has trouble using ubiquity, the person has the option to update ubiquity without having to download another iso or burn another cd, which is good if the person decides to try the install again a few days later. 

Problem is there is no update for ubiquity. I'm waiting for 2.1.34 or 2.1.35. They have it fixed but, when I tried to download the deb file its missing critical dependencies.

ubiquity currently is 2.1.33, and ubi-partman fails.

---

### Post by ronacc on 2010-03-11
I long ago gave up on ubi-partman it fails more than it works for me , I use a stand alone gparted cd to do my partitioning and formating before I even boot the live cd. been doing that since dapper or edgy , I give ubiquity a shot at it a couple of times during each dev cycle but always end up back with gparted .

---

### Post by KrazyPenguin on 2010-03-11
> **aviramof said:**
> every time i download a new daily version there are other problems with the installer first of all none of the recent versions i downloaded latetly detect i already have an operating system on the computer and i have two os i have windows seven on sdb and server 2008 on sda. 
 
but the installer said no os is detected also today installer has gave me an error when i chose create partitions automaticly and when i pressed continue any way it immediatly jumped to the page where you put name an password so i stoped the installer because i didn't knew where it would be install and i can choose the option to use the biggest free space because if it doesn't detect the server 2008 on sda who know what he would do to he's partition. 
 
and also the old problem i had with installing grub 2 that after is forcing me to manually install grub 2 on bote sda and sdb via live cd is still not solved.
 
any way i'm hopping that a final proper installer would be released soon because it's a big problem to download new version and only then detect that the installer is not so good and then you don't install anything like i did today or you need to download alternate cd which can also be problomatic at times.
 
thanks in advance.

The daily version is a snapshot, it has bugs, it is not completed.
Alpha releases are snapshots which usually have a working installation and are free of major showstoppers.
If you want to install a working version of ubuntu, try 9.10 or 8.04 LTS.
Hope that answers your question.

---

### Post by VMC on 2010-03-11
> **ronacc said:**
> I long ago gave up on ubi-partman it fails more than it works for me , I use a stand alone gparted cd to do my partitioning and formating before I even boot the live cd. been doing that since dapper or edgy , I give ubiquity a shot at it a couple of times during each dev cycle but always end up back with gparted .

The problem is even if your already parted, once you enter manual method, it fails.

 But I see ubiquity 2.1.35 is now available, so I will launch daily-live and upgrade ubiquity. See if it now works.
Edit: It does!

---

### Post by aviramof on 2010-03-11
> **KrazyPenguin said:**
> The daily version is a snapshot, it has bugs, it is not completed.
Alpha releases are snapshots which usually have a working installation and are free of major showstoppers.
If you want to install a working version of ubuntu, try 9.10 or 8.04 LTS.
Hope that answers your question.
 
i don't want 8.04 8.10 9.04 or 9.10 tried 8.10 it's good but too old for me 9.04 9.10 didn't want to work with my internet connection using pppoeconf command why i don't know but there not consider to be the best versions that is why i downloaded 10.04 in the first place.
 
as for ubiquity 2.1.35 how can i get it via the installer?how can i know what version there is in the installer?do you think today beta1freeze version would have this version?
 
thanks in advance.

---

### Post by kansasnoob on 2010-03-11
I just happened to notice this:

> i can't always do that not **via the installer** anyway because my connection is pppoe and i can't connect via normal installer only **via live cd option**

So are you talking about ubiquity or debian-installer? The live cd uses ubiquity but the alternate cd uses debian-installer unless I'm mistaken.

But in answer to your question, it's an alpha :)

This is why I multi-boot:

> Generating grub.cfg ...
Found background image: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.32-16-generic
Found initrd image: /boot/initrd.img-2.6.32-16-generic
Found linux image: /boot/vmlinuz-2.6.32-15-generic
Found initrd image: /boot/initrd.img-2.6.32-15-generic
Found Microsoft Windows XP Home Edition on /dev/sda1
Found Ubuntu 9.10 (9.10) on /dev/sda12
Found Debian GNU/Linux (squeeze/sid) on /dev/sda18
Found Ubuntu 9.04 (9.04) on /dev/sda5
Found Linux Mint 7 Gloria - Main Edition (7) on /dev/sda7
Found Ubuntu 8.04.4 LTS (8.04) on /dev/sda9
Found Microsoft Windows XP Home Edition on /dev/sdb1
Found Fedora release 12 (Constantine) on /dev/sdb2


Part of that is for grub2 testing, part for Ubuntuzilla testing, but Jaunty is what I use as my stable OS,

Why grub2 is wanting to "force install" to any mbr I don't know. I hadn't encountered that with the Live CD, unless I'm replacing Lucid (which has been controlling boot for a long time) I always choose to not install the new bootloader anywhere. Or in the case of Fedora I couldn't find that option so I installed it's grub to it's own root partition.

If you're using the alternate CD I'm not sure because I haven't used one yet in Lucid, maybe I should just to see how it goes. But this is an alpha and as it says at the top of this forum page:

> Ubuntu Lucid Lynx is in development, use only for testing purposes!!!

If I get frustrated with testing I just boot into my stable OS and forget about it for a while - sometimes days.

---

### Post by kansasnoob on 2010-03-11
> **VMC said:**
> The problem is even if your already parted, once you enter manual method, it fails.

 But I see ubiquity 2.1.35 is now available, so I will launch daily-live and upgrade ubiquity. See if it now works.

The daily live still says March 10. Yesterday I zsynced mine and it came out 718.1 MB even though the [page]("http://cdimage.ubuntu.com/daily-live/current/") says it's 685MB. I thought maybe zsync messed up (never has before) so I downloaded a whole new one and it was the same.

No new one today. I had wanted to do some testing because of [this parted bug]("http://ubuntuforums.org/showpost.php?p=8947039&postcount=7").

---

### Post by VMC on 2010-03-11
> **kansasnoob said:**
> The daily live still says March 10. Yesterday I zsynced mine and it came out 718.1 MB even though the [page]("http://cdimage.ubuntu.com/daily-live/current/") says it's 685MB. I thought maybe zsync messed up (never has before) so I downloaded a whole new one and it was the same.

No new one today. I had wanted to do some testing because of [this parted bug]("http://ubuntuforums.org/showpost.php?p=8947039&postcount=7").

Once you boot March10 daily-live, then click on update this installer, and it will upgrade to Ubiquity version 2.1.35.
And the *ubi-parted* bug is no more. :)

---

### Post by aviramof on 2010-03-11
i'm talking about ubiquity and i really don't understand why is it causing me so much problems all the time that i need to maually install grub 2 all the time i have two HD's
one ide one sata 1 the sata is in bios on channel 3 but he's the first on the boot sequnce and yet ubuntu recognize it as sdb the ide is on channel 1 i can't change it as far as i know so any way even if it's a good installer i still need to mount the sda 1 or what ever to install grub 2 then i need to install it again on sdb using this commands i got here in this forum:
 
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
 
sudo grub-install /dev/sda
 
sudo grub-install /dev/sdb
 
exit
 
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
 
a good ubiquity would do it on he's own but at the moment it doesn't even recognize i have windows seven on sdb and windows server 2008 on an ntfs partition in sda.

---

### Post by kansasnoob on 2010-03-11
Give me a little time. I'm going to put together some general instructions along with links to screenshots. 

Basically it will be what I do when I get a computer dumped in my lap that I know nothing about. It may take me a couple of hours :)

---

### Post by kansasnoob on 2010-03-11
Regarding the multi-drive situation it depends in part on the BIOS. Some BIOS settings allow you to choose whether IDE comes before SATA or vice versa. Others do not, but sometimes a BIOS update may change that. **[COLOR="Red"]But I never flash a BIOS unless it's absolutely necessary![/COLOR]** Quite often flashing the BIOS can cause more problems than it solves. 

My present motherboard's BIOS does not. If a SATA hard drive is plugged in it's always sda whether it's a boot drive with an OS or not, but this varies greatly from one motherboard manufacturer to another. Not only that but my mobo's SATA ports are not numbered so I can only tell which is SATA1 and which is SATA2 by digging up the manual.

Of course IDE is usually now only one port, mine does have 2, but they're clearly marked. Again this can vary, but **[COLOR="Red"]I try to fiddle with cables as little as possible![/COLOR]** Even with the greatest care, including anti-static precautions, there is always some danger of actual breakage plugging and unplugging components.

So generally, after checking for dust bunnies. I'll boot a computer with a Live CD just to see what I have. If I'm in doubt about specs I'll ususally use an old Knoppix Live CD that I have laying around, but I much prefer using an Ubuntu Live CD. 

In fact sometimes I'll use the Knoppix CD just to be sure Ubuntu should be compatible and then I boot the Ubuntu Live CD. One of the reasons for that is how Knoppix recognizes drives. [COLOR="Red"]My old Knoppix and Debian still tend to recognize IDE drives as hda whereas Ubuntu recognizes all as sda![/COLOR]

Anyway if I can boot an Ubuntu Live CD and run the Live Desktop that's when I start to figure out what I have and how it's recognized by Ubuntu. If I'm going to install Ubuntu I don't care how any other OS recognizes the discs or partitions! The same would be true of any OS!

I generally begin with the command:

```
sudo fdisk -l
```

Example:

```
lance@lance-desktop:~$ sudo fdisk -l
[sudo] password for lance: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0xdbc9dbc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1970    15823993+   7  HPFS/NTFS
/dev/sda2            2903       19457   132978037+   5  Extended
/dev/sda3            1971        2902     7486290   83  Linux
/dev/sda5            2903        3672     6184993+  83  Linux
/dev/sda6            3673        4188     4144738+  83  Linux
/dev/sda7            4189        4958     6184993+  83  Linux
/dev/sda8            4959        5481     4200966   83  Linux
/dev/sda9            5482        6257     6233188+  83  Linux
/dev/sda10           6258        6775     4160803+  83  Linux
/dev/sda11           6776        7292     4152771   83  Linux
/dev/sda12           7293        8065     6209091   83  Linux
/dev/sda13           8066        8582     4152771   83  Linux
/dev/sda14          19305       19457     1228941   82  Linux swap / Solaris
/dev/sda15          19019       19304     2297263+  83  Linux
/dev/sda16          16349       19018    21446743+  83  Linux
/dev/sda17          14973       16348    11052688+  83  Linux
/dev/sda18           8583        9362     6265318+  83  Linux
/dev/sda19           9363        9878     4144738+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0x63056305

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1913    15366141    7  HPFS/NTFS
/dev/sdb2            1914        2678     6144862+  83  Linux
/dev/sdb3            2679        9729    56637157+   5  Extended
/dev/sdb5            2679        3199     4184901   83  Linux
/dev/sdb6            9575        9729     1245006   82  Linux swap / Solaris
/dev/sdb7            9305        9574     2168743+  83  Linux
/dev/sdb8            7332        9304    15848091   83  Linux
/dev/sdb9            5993        7331    10755486   83  Linux
/dev/sdb10           4552        5992    11574801   83  Linux

Partition table entries are not in disk order

```

Well crap two drives and lots of partitions! What's what? Well with a mess like that I'd next use the [Boot Info Script]("http://bootinfoscript.sourceforge.net/"). I'm not going to post mine because it would only confuse you.

But it's broken down in sections and you should be able to derive enough info to see what operating systems are installed and all of there "designations", what OS's bootloader is installed to what drives mbr, etc. The first section will always be something like this:

> => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #3 for /boot/grub.

Then you'll see a list of all partitions, eg:

> sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM


Of course those partitions that do not have an OS installed will look like this:

> sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   


In order to tell what's there I would just have to use Nautilus to browse the contents. But something else that's very helpful is to use Gparted just to see what you have:

[ATTACH]149798[/ATTACH]

While that's a screenshot of my sda you can see in the upper right hand corner I can toggle to sda or sdb. Of course we're not talikng partitioning just yet, we just want to know what we have :)

So hopefully that gives you an idea of how to figure out exactly how Ubuntu recognizes your existing discs and partitions, next comes preparing to install! I like this general procedure:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Now, not everything there applies. I especially dislike that it shows using a separate /boot partition. **[COLOR="Red"]A separate /boot partition is seldom needed[/COLOR]** and quite often causes problems! But I like to have all of my partitioning (or repartitioning) figured out before I install!

Of course if I'm going to install to pre-existing partitions that's no problem. Once I've identified them I can just mark it down on a piece of paper, eg: you can see in that prior screenshot that I've labeled my partitions, so sda3 is Lucid Root (/) and sda11 is Lucid Home (/home), so if I were going to reinstall to those partitions I'd choose "Specify Partitions Manually" as it shows here:

[http://members.iinet.net.au/%7Eherman546/p22/027.png](http://members.iinet.net.au/%7Eherman546/p22/027.png)

In the next screen you'll be able to see each partition:

[http://members.iinet.net.au/%7Eherman546/p22/029.png](http://members.iinet.net.au/%7Eherman546/p22/029.png)

That's why it's important to know ahead of time just how the Ubuntu installer recognizes your partitions/discs. **[COLOR="Red"]I always create my partitions before installing![/COLOR]**

Once you're done applying changes and/or designating which partitions you want to install to you'll click forward and see this:

[http://members.iinet.net.au/%7Eherman546/p22/033.png](http://members.iinet.net.au/%7Eherman546/p22/033.png)

And maybe this:

[http://members.iinet.net.au/%7Eherman546/p22/034.png](http://members.iinet.net.au/%7Eherman546/p22/034.png)

Then you'll finally get this:

[http://members.iinet.net.au/%7Eherman546/p22/035.png](http://members.iinet.net.au/%7Eherman546/p22/035.png)

**[COLOR="Red"]That is your last chance to Quit if you think you might have messed up![/COLOR]** But if you look in the lower right hand corner there is an advanced button. **[COLOR="Red"]That's where you can make grub changes![/COLOR]**

[http://members.iinet.net.au/%7Eherman546/p22/036.png](http://members.iinet.net.au/%7Eherman546/p22/036.png)

So I could choose to not install the bootloader anywhere or to sda or sdb, or I could even choose to install it to a partition if I want to set up some strange chainloading setup :D

I hope this is helpful and I hope I didn't make any huge mistakes :D

---

### Post by ronacc on 2010-03-11
> **VMC said:**
> The problem is even if your already parted, once you enter manual method, it fails.

 But I see ubiquity 2.1.35 is now available, so I will launch daily-live and upgrade ubiquity. See if it now works.
Edit: It does!

that is the specific problem at this time but there have been others at different times , formating drives it was told not to format , formating the wrong drive (not the same thing), not reporting the drives in bios order ,drive designations not agreeing with grub designations ,using a uuid to setroot in grub that does not agree with the uuid of the devise grub sets as root (HDX,Y is not uuid .............) refusing to install grub to anywhere but what it THINKS is the first drive on the box , and yes I have bugged these things or added my me too if someone else reported it first .

---

### Post by kansasnoob on 2010-03-11
> **ronacc said:**
> that is the specific problem at this time but there have been others at different times , formating drives it was told not to format , formating the wrong drive (not the same thing), not reporting the drives in bios order ,drive designations not agreeing with grub designations ,using a uuid to setroot in grub that does not agree with the uuid of the devise grub sets as root (HDX,Y is not uuid .............) refusing to install grub to anywhere but what it THINKS is the first drive on the box , and yes I have bugged these things or added my me too if someone else reported it first .

No doubt there have been bugs in Alpha, I've initiated a couple of Ubiquity and parted reports.

What's important is knowing when something fails before it causes you to restore a backup ;)

If I spent some time I'm sure I can find one where I had to use a different Live CD to complete what I wanted.

That's what testing is for. If someone is not up to the challenge then they shouldn't do it!

---

### Post by VMC on 2010-03-11
> **ronacc said:**
> that is the specific problem at this time but there have been others at different times , formating drives it was told not to format , formating the wrong drive (not the same thing), not reporting the drives in bios order ,drive designations not agreeing with grub designations ,using a uuid to setroot in grub that does not agree with the uuid of the devise grub sets as root (HDX,Y is not uuid .............) refusing to install grub to anywhere but what it THINKS is the first drive on the box , and yes I have bugged these things or added my me too if someone else reported it first .

Oh, I see. You have a valid point. Ubiquity shouldn't have anything to do with this alpha or any other for that matter. There have been numerous ubiquity errors in the past.

I know from the look of this Ubiquity that work has been done on it, so something got messed up for sure.

The debian-installer, on the other hand, rarely has any issues. Probably not much updating on that stable program.

---

### Post by ronacc on 2010-03-11
@ VMC     I am not saying that at all , in fact what I said indicates that it needs through testing to insure as far as possible that disasters don't happen in the release . but at the same time serious effort should be put into stabilizing something as important as the installer program (all parts of it) . I am sorry if it offends but I believe an installer that works as it should is more important than one that is glitzy.

@ kansasnoob  I have been "upto the challenge"  so far , sometimes with help from other testers here in the forum .

---

### Post by aviramof on 2010-03-12
here is the bug report i did along with boot info i did using vmc boot info script:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/533643](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/533643)

---

### Post by VMC on 2010-03-12
> **ronacc said:**
> @ VMC     I am not saying that at all , in fact what I said indicates that it needs through testing... 

ronacc, a misunderstanding. I stated you made a valid point, period. **Then** I added my take on the rest of Ubiquity's problems. I should have clarified that more.

---

### Post by ronacc on 2010-03-12
@ VMC  sorry, I misread you answer .

---


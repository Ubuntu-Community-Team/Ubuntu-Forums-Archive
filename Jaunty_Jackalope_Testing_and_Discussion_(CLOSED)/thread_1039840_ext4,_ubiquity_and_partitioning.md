---
title: "ext4, ubiquity and partitioning"
date: 2009-01-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2009-01-14
Hi all, 
 It seems people have issues with ext4, ubiquity and partitioning. All the bugs however seem to be all over the place. Could we have all the bugs and issues in one specific thread so we could know what to look out for .  I propose we use this thread specifically for the same and ask the developers to also come look at the thread so we can have ext4 happening cool by release time. 

Btw parted got a new update. 

> 

parted (1.8.8.git.2008.03.24-11.1ubuntu3) jaunty; urgency=low

  * unpartitioned-disks.dpatch (update): Just return immediately from
    ped_disk_commit if running on an unpartitioned disk, to avoid failures
    in case we end up in _kernel_reread_part_table (encountered during a
    Wubi installation of Ubuntu).

 -- Colin Watson <cjwatson@ubuntu.com>  Thu, 15 Jan 2009 00:47:01 +0000



---

### Post by autocrosser on 2009-01-14
The problem I had was with a created EXT4 system & the patched grub--Colin is working on it...Seems that there is a "difference" between a partition that was formatted as EXT4 & one that was converted from EXT3 to EXT4. I forwarded the bug report to Colin & I have "fixed" the problem by backing up my /boot--deleting it & then reinstalling it..not elegant, but it worked in my case. The bug report is at:

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/316872](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/316872)

Colin seems a bit overworked right now, so let's all pull together & help as much as possible......I for one want to see the bugs killed & EXT4 be the default real soon ;)

---

### Post by ShirishAg75 on 2009-01-15
I have the same idea, at the very least critical bugs regarding ext4 should be fixed before alpha4 as far as possible.

---

### Post by waspbr on 2009-01-15
I am having some issues, first of all, is it possible to have an ext4 root partition with an ext4 /home partition?  I have done the fresh install with while keeping the /home intact a million times already. 

I am using the daily build of today (15/01) and both livecd and alternate cd give me the same error

failed to create a file system

the ext3 file system creation in partition #4 (my home) of SCSI3 (0,0,0) sda failed. 

what gives?

---

### Post by Slug71 on 2009-01-15
> **waspbr said:**
> I am having some issues, first of all, is it possible to have an ext4 root partition with an ext4 /home partition?  I have done the fresh install with while keeping the /home intact a million times already. 

I am using the daily build of today (15/01) and both livecd and alternate cd give me the same error

failed to create a file system

the ext3 file system creation in partition #4 (my home) of SCSI3 (0,0,0) sda failed. 

what gives?

Yes it is possible to have /(root) and /home as Ext4. Thats how my system currently is.
There seem to be problems with the installer for the last few days. I'd wait for Alpha 3.

---

### Post by Gina on 2009-01-15
As I've posted elsewhere, I have an ext4 system with separate / and /home partitions formatted to ext4, on my very old AMD K6-2 machine.  I haven't yet done extensive testing but it works.  Now I'm hoping Alpha 3 will install on my AMD64 and I can test ext4 on that.

---

### Post by Starks on 2009-01-15
I have the latest daily live iso and ubiquity is not letting me partition my drive as such:

20 GB /root ext4 + 130 GB /home ext4 + 5 GB swap

Also, can somebody explain to me why Gparted 0.4.2 svn still not included in Jaunty?

---

### Post by Starks on 2009-01-15
> **Slug71 said:**
> **Yes it is possible to have /(root) and /home as Ext4. Thats how my system currently is.**
There seem to be problems with the installer for the last few days. I'd wait for Alpha 3.

how did you set that up?

---

### Post by Slug71 on 2009-01-15
Another new thread about this. Cans the mods please merge them.

---

### Post by Slug71 on 2009-01-15
> **Starks said:**
> how did you set that up?

I had the Daily Build from the 9th i think(the first day Ext4 was included) for AMD64. The installer and whole setup menu was text based though.

---

### Post by Starks on 2009-01-15
> **Slug71 said:**
> I had the Daily Build from the 9th i think(the first day Ext4 was included) for AMD64. The installer and whole setup menu was text based though.

1. was ext4 included for i686 on that day?

2. can an alternate cd iso be made usb bootable?

---

### Post by ruik on 2009-01-15
2. Yes

---

### Post by Slug71 on 2009-01-15
> **Starks said:**
> 1. was ext4 included for i686 on that day?

2. can an alternate cd iso be made usb bootable?

 1. Yeh i think so. It was the first day that Ext4 hit the installer when i downloaded the Daily Build. Was all text based though.

---

### Post by waspbr on 2009-01-15
My bad, what I meant to ask was if it was possible to have a ext4 root partition together with a ext3 /home. So far I have not managed to get that to work...

---

### Post by Slug71 on 2009-01-15
> **waspbr said:**
> My bad, what I meant to ask was if it was possible to have a ext4 root partition together with a ext3 /home. So far I have not managed to get that to work...

Yeh that should be no problem at all.

---

### Post by DeeZiD on 2009-01-15
The [http://cdimage.ubuntu.com/kubuntu/daily-live/20090115.1/](http://cdimage.ubuntu.com/kubuntu/daily-live/20090115.1/) amd64 image works fine!
```
/dev/sda5 on / type ext4 (rw,relatime,errors=remount-ro)

```

I've installed my first EXT4 and KDE4.2 system. :)

---

### Post by Rocket2DMn on 2009-01-15
Threads merged.  I'll be doing ext4 on Jaunty as soon as I get alpha 3 :)

---

### Post by Starks on 2009-01-15
rocket, good luck.

you won't be able to do it with swap or /home partitions included.

the installers, text or graphical, won't work properly if you want to have other partitions on the disk along with an ext4 one.

---

### Post by Slug71 on 2009-01-15
I'm actually starting to think maybe Ubiquity should just be replaced by maybe Anaconda.

---

### Post by caryb on 2009-01-15
I have the Kubuntu daily installer 15/1/09 amd64 (I hosed my machine trying to convert my FS last night)It allows me to created a ext4 / partition but when you select apply it it crashes back to the timezome maps:confused: I tried to select ext3 as well but it does the same.


Cary

Am too impatient to be without a machine waiting for Alpha 3 It could be days or weeks away.

---

### Post by Rocket2DMn on 2009-01-15
> **Starks said:**
> rocket, good luck.

you won't be able to do it with swap or /home partitions included.

the installers, text or graphical, won't work properly if you want to have other partitions on the disk along with an ext4 one.

Thanks for the heads up, I'll just be installing on a laptop that I use solely for testing development released.  I'm excited to see how ext4 performs on this older machine.  I have another laptop that I keep as stable, but there isn't much on it except for stuff I need when I travel.  My desktop is the only machine that truly has to be stable, and it's the only one with multiple partitions, I wasn't intending to use ext4 on it anytime soon.

---

### Post by caryb on 2009-01-15
Does anyone know the command to create the ext4 partition from cli using fsck?


TIA Cary

---

### Post by autocrosser on 2009-01-15
Cary---best info is at:  [http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)

Be careful & backup everything first......

Start at: Converting an ext3 filesystem to ext4

---

### Post by waspbr on 2009-01-16
hmmm, no cake tho. 

I tried again installing jaunty daily of 15/01,as a ext4 root partition along side with my existing ext3 /home. Note that also have hardy and intrepid installed onto other partitions using the same /home.

I still get the same error message as before and a grub error 22 at reboot.

I will try again when alpha 3 is released

---

### Post by Gina on 2009-01-16
> **Rocket2DMn said:**
> Thanks for the heads up, I'll just be installing on a laptop that I use solely for testing development released.  I'm excited to see how ext4 performs on this older machine.  I have another laptop that I keep as stable, but there isn't much on it except for stuff I need when I travel.  My desktop is the only machine that truly has to be stable, and it's the only one with multiple partitions, I wasn't intending to use ext4 on it anytime soon.I have Jaunty with two separate ext4 partitions for / and /home successfully working on my 10 yr old AMD K6-2 machine.

---

### Post by kaervos1024 on 2009-01-16
I was having the same trouble, I hosed my system using an AMD64 Alternate Install daily spin from 01/15. I just got the AMD64 Desktop Install daily for 01/16, made root and usr partitions EXT4, home partition ReiserFS along with a swap partition. The graphical installer handled all this fine (unlike the Alpha2 one, which was totally borked), created and formatted the partitions fine... install has just completed. Rebooting now... ... GLORY! No GRUB errors, booted perfectly, and MIGHTY fast!

If you were having issues before, try the 01/16 daily spin.

Going to go enjoy 9.04 w/ EXT4 now. Cheers!

---

### Post by Starks on 2009-01-16
ext4 will not be practical until you can mess around with it in gparted.

---

### Post by Gina on 2009-01-16
Yes, we certainly need it supported in gparted.

---

### Post by caryb on 2009-01-16
Well I rebuilt my laptop, it was a bugger to get ext4 going, I had to boot to live cd & run fsck to create the partition then install & tell the partitioner program not to format otherwise it crashes! It might be a placebo effect but it does seem to boot a lot faster.


Cary

---

### Post by goompas on 2009-01-17
Caryb have you installed system with ext4?
Because i have same problem, when i make partiotions ext4 and swap and have windows partiotion installr back from formating step to 5 step(partitioning program)

---

### Post by jerrylamos on 2009-01-17
Is ext4 ready for prime time? Check out

[http://ubuntuforums.org/showthread.php?t=1040199](http://ubuntuforums.org/showthread.php?t=1040199)

for multiple cases of irretrievable data loss....

Jerry

---

### Post by plun on 2009-01-17
No, Jaunty is a Alpha release and must be tested.

EXT4 is up to every user, also backups...

---

### Post by Gina on 2009-01-17
I'm only installing with ext4 on machines used for nothing but testing aand net browsing - no data of any importance - so if it wipes the whole hard drive I don't worry, just reinstall from scratch - no problem.  I have ext4 on my AMD K6-2 and now on the AMD64 which I'm currentlky trying to get working properly after installing Alpha 3 with ext4 partitions.  I also have Jaunty on my laptop but I stay one step behind on that as there would be more to restore if I lost everything..

---

### Post by psychok9 on 2009-02-04
I can't understand HOW can you use Ext4 on root partition of Ubuntu Jaunty.
I've tried (after XFS nightmare filesystem) and i got the same result: can't boot! And I've downloaded last daily Jaunty alpha3 :(
I can't modify any grub mount because i got a generic error 15 without any edit boot options... 	:cry:

---

### Post by Slug71 on 2009-02-04
> **psychok9 said:**
> I can't understand HOW can you use Ext4 on root partition of Ubuntu Jaunty.
I've tried (after XFS nightmare filesystem) and i got the same result: can't boot! And I've downloaded last daily Jaunty alpha3 :(
I can't modify any grub mount because i got a generic error 15 without any edit boot options... 	:cry:

Alpha-4 should be out in less than 24hrs. 
Download and try that.

---

### Post by psychok9 on 2009-02-04
> **Slug71 said:**
> Alpha-4 should be out in less than 24hrs. 
Download and try that.

Thanks ;)

---

### Post by psychok9 on 2009-02-05
Great: alpha4 now seem to be work correctly with Ext4 root and boot partition ;)
For info: I need to download the following cd, or I can download only updates?
I've seen the same patch on the updater (alpha3 vs alpha4), but with alpha4 I can work on ext4 :D

---

### Post by Slug71 on 2009-02-05
> **psychok9 said:**
> Great: alpha4 now seem to be work correctly with Ext4 root and boot partition ;)
For info: I need to download the following cd, or I can download only updates?
I've seen the same patch on the updater (alpha3 vs alpha4), but with alpha4 I can work on ext4 :D

You dont need a separate boot partition.

---

### Post by psychok9 on 2009-02-05
> **Slug71 said:**
> You dont need a separate boot partition.

Yeah, I've installed fine on a single partition (root & boot on the same partition).
Often I don't speak a good english sorry ;)

---

### Post by Slug71 on 2009-02-05
> **psychok9 said:**
> Yeah, I've installed fine on a single partition (root & boot on the same partition).
Often I don't speak a good english sorry ;)

Got ya.

As for your earlier question - If you keep up with the updates you DON'T need to download the next Alpha or any other following release.

---


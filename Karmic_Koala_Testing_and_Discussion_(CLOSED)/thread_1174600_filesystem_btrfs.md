---
title: "filesystem btrfs"
date: 2009-05-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by pulpo69 on 2009-05-31
will btrfs an option in karmic?

---

### Post by ghindo on 2009-05-31
At least on some level, yes.

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=btrfs](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=btrfs)

---

### Post by whoop on 2009-05-31
You can already use it in Jaunty (even in Intrepid although you might require a newer kernel, forgot which kernel Intrepid is using)..
It's not stable enough for production atm... I wouldn't try to use it on / either :p Even more so if your /boot isn't on it's own partition. Don't think grub knows btrfs.

---

### Post by nanog on 2009-05-31
Its slow. Achingly, heart-rendingly slow. My informal benchmark of raid1 showed it to be ~30% of the speed of ext4+mdadm on a remote nfs share. It cannot do raid5 or raid6 (or raid 1+0) and  there is no plan to start working on this BASIC functionality. 

(*screams unmentionable things about the single sentence in the GPLv2 that prevents inclusion of zfs*)

---

### Post by hexsel on 2009-05-31
That actually matches a benchmark by Phoronix.  Unless you really want the features of BTRFS, EXT4 is the way to go (as far as performance goes).

[Comparative BTRFS]("http://www.phoronix.com/scan.php?page=article&item=btrfs_benchmarks&num=1")


> **nanog said:**
> Its slow. Achingly, heart-rendingly slow. My informal benchmark of raid1 showed it to be ~30% of the speed of ext4+mdadm on a remote nfs share. It cannot do raid5 or raid6 (or raid 1+0) and  there is no plan to start working on this BASIC functionality. 

(*screams unmentionable things about the single sentence in the GPLv2 that prevents inclusion of zfs*)

---

### Post by gnomeuser on 2009-05-31
My Fedora 11 box has just been reinstalled on btrfs, the reports of it's utter slowness are overrated. For a normal desktop it feels no different than ext4.

Performance is also being profiled and optimized, the important thing so far has been getting a reasonable feature set and stability of the dataformat. The performance is increasing with every release now, Chris Mason is actively working on improvements along with optimizing fsync behaviour.

It's very stable so far and performs quite reasonable. The biggest problem is that the advanced features aren't really exposed to the any thing like backup services or package managers (for rollback e.g.)

The Server team for Ubuntu has expressed interest in getting btrfs testable for Ubuntu users, so I assume there might be work to enable that for Karmic unless there are more pressing tasks.

---

### Post by ghindo on 2009-05-31
> **nanog said:**
> (*screams unmentionable things about the single sentence in the GPLv2 that prevents inclusion of zfs*)With Oracle having bought Sun, I'm still a bit hopeful that they will re-license ZFS...

---

### Post by whoop on 2009-05-31
> **ghindo said:**
> With Oracle having bought Sun, I'm still a bit hopeful that they will re-license ZFS...

Last I heard you had to pay for garbage collection :-&

---

### Post by gnomeuser on 2009-05-31
> **ghindo said:**
> With Oracle having bought Sun, I'm still a bit hopeful that they will re-license ZFS...

That alone will not make it available in Linux, remember that the code has to live up to the standards of the kernel. This includes not duplicating a boatload of features like the device mapper which ZFS does currently (by design).

Btrfs will be in shape and deployed with the same features as ZFS (and more) way before ZFS even if relicensed today will be in shape for inclusion in the kernel even label as experimental.

ZFS should probably be added if we ever get the code and most importantly a suitable license of the patents Sun hold on it. If for anything but to make it easy for people to use their existing infrastructure and transition to a Btrfs future.

---

### Post by hexsel on 2009-06-01
> **whoop said:**
> Last I heard you had to pay for garbage collection :-&

Although I'm not a big fan of Oracle, that's not true.  IF you want to use the EXPERIMENTAL GC they just shipped with the latest release IN PRODUCTION, you are required to have a contract with them.

That does not affect anyone developing or testing with it.  Also shouldn't affect any production systems, since it would be irresponsible to put an experimental GC there in the first place.

---

### Post by hexsel on 2009-06-01
Actually, you must not have read the Phoronix article, btrfs was even slower than EXT3 in some situations.  You didn't "feel" the difference, which is not exactly very scientific.

Like EXT4 had serious issues with some applications (regardless of whose fault it was), btrfs might have its own issues.

Thus:
[LIST]
[*]it's slower
[*]no useful features are exposed
[*]it's risky
[/LIST]

You should use it only if you're likely to provide useful bug reports and like to live dangerously!



> **gnomeuser said:**
> My Fedora 11 box has just been reinstalled on btrfs, the reports of it's utter slowness are overrated. For a normal desktop it feels no different than ext4.

Performance is also being profiled and optimized, the important thing so far has been getting a reasonable feature set and stability of the dataformat. The performance is increasing with every release now, Chris Mason is actively working on improvements along with optimizing fsync behaviour.

It's very stable so far and performs quite reasonable. The biggest problem is that the advanced features aren't really exposed to the any thing like backup services or package managers (for rollback e.g.)


---

### Post by whoop on 2009-06-01
> **hexsel said:**
> Although I'm not a big fan of Oracle, that's not true.  IF you want to use the EXPERIMENTAL GC they just shipped with the latest release IN PRODUCTION, you are required to have a contract with them.

That does not affect anyone developing or testing with it.  Also shouldn't affect any production systems, since it would be irresponsible to put an experimental GC there in the first place.

Actually I wasn't being (totally) serious. I know:
[http://java.sun.com/javase/6/webnotes/6u14.html](http://java.sun.com/javase/6/webnotes/6u14.html)

> 
Although G1 is available for use in this release, note that production use of G1 is only permitted where a Java support contract has been purchased...


I was just pointing out that the Oracle Sun takeover isn't necessaryly a good thing for zfs...
I'll stop trying to be funny ;)

---

### Post by loomsen on 2009-06-01
> **gnomeuser said:**
> My Fedora 11 box has just been reinstalled on btrfs, the reports of it's utter slowness are overrated. For a normal desktop it feels no different than ext4.

Performance is also being profiled and optimized, the important thing so far has been getting a reasonable feature set and stability of the dataformat. The performance is increasing with every release now, Chris Mason is actively working on improvements along with optimizing fsync behaviour.

It's very stable so far and performs quite reasonable. The biggest problem is that the advanced features aren't really exposed to the any thing like backup services or package managers (for rollback e.g.)


#2 
except that I didn't reinstall but install onto another partition.

Am I the only one who finds it useful that you can mount separate disks all on the same mountpoint?

---

### Post by dtessier on 2009-06-01
> **gnomeuser said:**
> That alone will not make it available in Linux, remember that the code has to live up to the standards of the kernel. This includes not duplicating a boatload of features like the device mapper which ZFS does currently (by design).

I was just reading up on BTRFS today, and found the following in their wiki.

[http://btrfs.wiki.kernel.org/index.php/Multiple_Device_Support](http://btrfs.wiki.kernel.org/index.php/Multiple_Device_Support)

[http://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices](http://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices)

Sounds like they're heading down the same path as ZFS. These sentences from the first link are particularly interesting:

> If Btrfs were to rely on device mapper or MD for mirroring, it would not be able to resolve checksum failures by checking the mirrored copy. The lower layers don't know the checksum or granularity of the filesystem blocks, and so they are not able to verify the data they return.

If Btrfs were to rely on device mapper for aggregating all of the physical devices into a single big address space, it would not have sufficient information to allocate mirrored copies on different devices. Keeping this information in sync between Btrfs and the device mapper would be difficult and error prone.

---

### Post by gnomeuser on 2009-06-02
> **dtessier said:**
> I was just reading up on BTRFS today, and found the following in their wiki.

[http://btrfs.wiki.kernel.org/index.php/Multiple_Device_Support](http://btrfs.wiki.kernel.org/index.php/Multiple_Device_Support)

[http://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices](http://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices)

Sounds like they're heading down the same path as ZFS. These sentences from the first link are particularly interesting:

Kinda.. 

They are working together to find the best road ahead, there are lots of situations that need handling for these next generation file systems and other functionality (union mounts e.g. will require plentiful vfs work to be done right - alternatively there is a fuse way and other means such as aufs). 

In some ways btrfs might merge with or replace parts of both layers, it is not wholesale going to throw out all that code in favor of it's own brand new code though. 

[This FUDCon talk might shed some light](http://alt.fedoraproject.org/pub/alt/videos/2009/FUDConF11/fudcon-f11-rm345-session1.ogg) - Val is a former ZFS developer who helped design parts of both filesystems. The audio in this Ogg Theora video is unfortunately a bit poor.

---

### Post by ssam on 2009-06-02
> **nanog said:**
> (*screams unmentionable things about the single sentence in the GPLv2 that prevents inclusion of zfs*)

the GPL did not stop Linux getting FAT, HFS and NTFS. someone just needs to sit down and write a GPL or BSD ZFS module. it should be an easier task as you would not have to reverse engineer it (get someone to write a spec based on sun's source code).

---

### Post by gnomeuser on 2009-06-02
> **ssam said:**
> the GPL did not stop Linux getting FAT, HFS and NTFS. someone just needs to sit down and write a GPL or BSD ZFS module. it should be an easier task as you would not have to reverse engineer it (get someone to write a spec based on sun's source code).

Won't work, that module would be in violation of the patents Sun holds on ZFS, we need a license for those to even attempt such a reimplementation.

---

### Post by tgpraveen on 2009-06-02
> **ssam said:**
> the GPL did not stop Linux getting FAT, HFS and NTFS. someone just needs to sit down and write a GPL or BSD ZFS module. it should be an easier task as you would not have to reverse engineer it (get someone to write a spec based on sun's source code).

NTFS is not in the kernel it is FUSE ie user space

though its inclusion by default in ubuntu in main is a grey area,

---

### Post by ssam on 2009-06-02
> **gnomeuser said:**
> Won't work, that module would be in violation of the patents Sun holds on ZFS, we need a license for those to even attempt such a reimplementation.

there are patents on FAT too, thats never stopped it being in the kernel.

if the patents on ZFS are valid, then they may cover BTRFS too. The lawsuit with NetApp covers methods rather than specific ZFS implementation, so it could cover other filesystems with built in RAID.

[QUOTE=tgpraveen]
NTFS is not in the kernel it is FUSE ie user space

though its inclusion by default in ubuntu in main is a grey area
[/QUOTE]
NTFS-3G is not build out of code from microsoft, and is licensed under the GPL (and also available under a proprietary licence).

---

### Post by Eclipse. on 2009-06-02
> **ssam said:**
> **there are patents on FAT too, thats never stopped it being in the kernel.**

if the patents on ZFS are valid, then they may cover BTRFS too. The lawsuit with NetApp covers methods rather than specific ZFS implementation, so it could cover other filesystems with built in RAID.


NTFS-3G is not build out of code from microsoft, and is licensed under the GPL (and also available under a proprietary licence).

*Cough* Tom-Tom incident *Cough*

---

### Post by Luke has no name on 2009-06-26
I would think a few filesystem hackers already have ZFS working on Linux, regardless of legality. 

1) As long as they keep it quiet, who's going to stop them?

2) If ZFS ever did get relicensed, they'd be on the ball deploying it.

---

### Post by ssam on 2009-06-26
> **Luke has no name said:**
> I would think a few filesystem hackers already have ZFS working on Linux, regardless of legality. 

1) As long as they keep it quiet, who's going to stop them?


as long as they don't distribute it they aren't breaking the GPL or CDDL (as far as i can tell with CDDL, but pretty sure for GPL).

---

### Post by loomsen on 2009-07-03
> **Luke has no name said:**
> I would think a few filesystem hackers 

I'd seriously doubt that due to ZFSs obvious 
> concept of a single, linear chain of snapshots
disadvantages compared to btrfs for instance.

However, imo btrfs succeeds zfs already cause of writeable snapshots (thus a timeline/timescrollbar - similar to the one centos plans to implement - can be realized with btrfs, not with zfs tho...) 

Anyway, I'm considering to move on and give Tux3 a try (after my first complete btrfs-crash after 3,5weeks of non-stop usage... compared: ext4 running for 4 days now, 3 freezes and 5 acpi power-offs because my thermal sensors reached their limits...) 

Additional Tux3 reading:
[http://tux3.org/index.html](http://tux3.org/index.html)

---

### Post by RmsMit on 2009-07-19
> **whoop said:**
> You can already use it in Jaunty (even in Intrepid although you might require a newer kernel, forgot which kernel Intrepid is using)..
It's not stable enough for production atm... I wouldn't try to use it on / either :p Even more so if your /boot isn't on it's own partition. Don't think grub knows btrfs.

Karmic is going to have Grub2 which I belive will support btrfs as a boot point.:D

---

### Post by nanog on 2009-07-19
i am fairly certain that ext4 is not the cause of your freezes and acpi problems.

---

### Post by whoop on 2009-07-20
> **RmsMit said:**
> Karmic is going to have Grub2 which I belive will support btrfs as a boot point.:D

I don't think grub2 supports btrfs yet; but if it doesn't, it will. Grub will probably never support btrfs...

---

### Post by flavouride on 2009-07-20
> **nanog said:**
> i am fairly certain that ext4 is not the cause of your freezes and acpi problems.

Unfortunately my (ex-)Jaunty used to run flawlessly until I tune2fs & fsck my boot + root + home partition to ext4 from ext3 (using jaunty live cd) and odd crashes just started occurring; I doubt kernel 2.6.28's maturity in supporting ext4

This apparent fact only echoed when my system has become rock solid again after I update-manager -d to karmic a month ago

---

### Post by Triptol on 2009-08-01
LWN has a nice artice about btrfs, might shed some lights on the discussion  here: [http://lwn.net/Articles/342892/](http://lwn.net/Articles/342892/)

---

### Post by wayne_cat on 2009-08-01
> **Triptol said:**
> LWN has a nice artice about btrfs, might shed some lights on the discussion  here: [http://lwn.net/Articles/342892/](http://lwn.net/Articles/342892/)

ok .. even Linus screwed his system with btrfs ...

[http://www.mail-archive.com/linux-btrfs@vger.kernel.org/msg02501.html](http://www.mail-archive.com/linux-btrfs@vger.kernel.org/msg02501.html)

... so I don't have to be ashamed :biggrin:

---

### Post by gnomeuser on 2009-08-01
> **wayne_cat said:**
> ok .. even Linus screwed his system with btrfs ...

[http://www.mail-archive.com/linux-btrfs@vger.kernel.org/msg02501.html](http://www.mail-archive.com/linux-btrfs@vger.kernel.org/msg02501.html)

... so I don't have to be ashamed :biggrin:

Auto migration of dataformats are kind of a problem for people like Linus who need to bisect older kernels.. boot it once and your data is no longer readable beyond a certain changeset.

Nothing you should really run into, unless you intentionally boot older kernels. Even then it shouldn't hose your data just fail to mount if I understand correctly.

Regardless average users might want to hold off till experimental support is in the distro you use. Not that this means it's safe but it gives some degree of support and assurance that the userspace tools will be provided in sync with kernel updates and that you will get a steady flow of fixes.

---

### Post by wayne_cat on 2009-08-01
> **gnomeuser said:**
> Auto migration of dataformats are kind of a problem for people like Linus who need to bisect older kernels.. boot it once and your data is no longer readable beyond a certain changeset.

Nothing you should really run into, unless you intentionally boot older kernels. Even then it shouldn't hose your data just fail to mount if I understand correctly.

Regardless average users might want to hold off till experimental support is in the distro you use. Not that this means it's safe but it gives some degree of support and assurance that the userspace tools will be provided in sync with kernel updates and that you will get a steady flow of fixes.

you are right ... you don't lose any data ... but if you boot an older kernel it looks like
a totaly damaged filesystem.  

I agree to Ted Tso ... "keep more backwards compatibility code for longer" 

[http://www.mail-archive.com/linux-btrfs@vger.kernel.org/msg02501.html](http://www.mail-archive.com/linux-btrfs@vger.kernel.org/msg02501.html)

I still like btrfs ... fast as lightning

---

### Post by nanog on 2009-08-02
Actually in my speed tests brtfs is slightly slower than ext3. Since you still have to use mdadm to run a useful raid array I keep asking myself whats the ****ing point? IMO, its a file system designed for a developer/hobbyist.

I am getting more and more impressed with Nexenta (Ubuntu on Solaris) and am considering moving several file servers to zfs.

---

### Post by gnomeuser on 2009-08-02
> **nanog said:**
> Actually in my speed tests brtfs is slightly slower than ext3. Since you still have to use mdadm to run a useful raid array I keep asking myself whats the ****ing point? IMO, its a file system designed for a developer/hobbyist.

I am getting more and more impressed with Nexenta (Ubuntu on Solaris) and am considering moving several file servers to zfs.

Not everything is about speed, aside that it's no way near finished with integration with the system nor optimization.

---

### Post by Regenweald on 2009-08-02
> **gnomeuser said:**
> Not everything is about speed, aside that it's no way near finished with integration with the system nor optimization.

Not for the life of me do i get why persons continue to compare a fs in heavy development to a completed one then act like it's news that the 'stable for years' ones give better performance. compare btrfs to tux3 and tell me something of substance. 

am i alone in this ? :)

---

### Post by loomsen on 2009-08-03
> **regenweald said:**
> not for the life of me do i get why persons continue to compare a fs in heavy development to a completed one then act like it's news that the 'stable for years' ones give better performance. Compare btrfs to tux3 and tell me something of substance. 

Am i alone in this ? :)

#2

---

### Post by nanog on 2009-08-03
While whinging about the speed of a fs under development is premature I only brought it up in response to someone who stated that it was fast. 

Its not.

ZFS works now. I really encourage anyone who wants to play with snapshots, seemless lvm, and raid-z (a bloody revelation) to try Nexenta. It will be many years before brtfs comes close to feature parity with zfs.

---

### Post by purct on 2009-09-19
I don't understand why nobody is working on the port of advfs to linux.  All the Tru64 code and the HP-UX code is available for porting and having used ZFS on solaris and advfs on tru64 - I have to say that advfs seemed to have the edge... 

If btrfs is not going to be available for sometime and ZFS is a no go, Why no port of AdvFS?

---

### Post by gnomeuser on 2009-09-19
> **purct said:**
> I don't understand why nobody is working on the port of advfs to linux.  All the Tru64 code and the HP-UX code is available for porting and having used ZFS on solaris and advfs on tru64 - I have to say that advfs seemed to have the edge... 

If btrfs is not going to be available for sometime and ZFS is a no go, Why no port of AdvFS?

btrfs will be ready very soon, it runs very nicely today and progress is very quick. You are overestimating the time it will take to finish it to a point where distros could ship it. Maybe not as the default fs but as a technology preview (infact Fedora does this already). 

You are also grossly underestimating the time such a advfs port would take, let alone the time it would take to prove it stable. Aside that there might be problems with license compatibility and patents in doing this.

---

### Post by purct on 2009-10-02
> **gnomeuser said:**
> btrfs will be ready very soon, it runs very nicely today and progress is very quick. You are overestimating the time it will take to finish it to a point where distros could ship it. Maybe not as the default fs but as a technology preview (infact Fedora does this already). 

You are also grossly underestimating the time such a advfs port would take, let alone the time it would take to prove it stable. Aside that there might be problems with license compatibility and patents in doing this.

OK, maybe I am underestimating the time it would take to port and prove stable,  but what do you mean with regards to license compatibility and patents in doing it?  The code has been licensed under the GPLv2 to be compatible with the Linux kernel or am I missing something?

---

### Post by gnomeuser on 2009-10-02
> **purct said:**
> OK, maybe I am underestimating the time it would take to port and prove stable,  but what do you mean with regards to license compatibility and patents in doing it?  The code has been licensed under the GPLv2 to be compatible with the Linux kernel or am I missing something?

I mean I have not examined the exact licensing of every aspect of the code, I was unsure if there were license incompatibilities, this is often the case when large companies open their proprietary code. Likewise with patent issues, they might open the code but refuse to license the patents. I honestly didn't feel like doing so since it feels pointless based on the below:

At any rate the pure technical challenge of converting the code to  the Linux kernel will very likely take longer than the time it will take to finish BtrFS which is already looking very solid. You are suggesting taking nearly finished code and chucking it in favor of porting code which we have not reviewed, which probably only very few people know and which has no buy in from distributions.. it is put simply a stupid plan. 

It's basically suggesting starting over but with the added burden of keeping the new port compatible and without a great number of skilled people actively paid to work full time on the project. This may not seem like a big deal to you but one of the reasons BtrFS has been able to move so quickly is that it has been able to improve and adapt due to not carrying around legacy design from an older or existing implementation.

So no, I do not believe I will be spending a second longer considering this plan.

---

### Post by purct on 2009-10-02
> **gnomeuser said:**
>  Likewise with patent issues, they might open the code but refuse to license the patents.

OK, I wasn't aware that patent issues may still exist in code that has been released under GPL2
> **gnomeuser said:**
> 
You are suggesting taking nearly finished code and chucking it in favor of porting code which we have not reviewed.

NO, I am in no way suggesting BtrFS should be chucked in favor of porting AdvFS.

I have seen a number of posts from people asking for kernel based ZFS because nothing exists in Linux to compete with it (but cant be done because of Licensing issues..)  So All I was saying is that if BtrFS was sometime away and ZFS couldn't be ported....advfs shouldn't be ruled out :lolflag:

> **gnomeuser said:**
> 
 it is put simply a stupid plan. 

I really don't see how that could be a stupid plan...:confused: 

I don't think unreasonable for me as a user to make a suggestion - even if I am ill-informed :P  I am sorry if the suggestion offended you...I certainly didn't intend it to.

> **gnomeuser said:**
> 
This may not seem like a big deal to you but one of the reasons BtrFS has been able to move so quickly is that it has been able to improve and adapt due to not carrying around legacy design from an older or existing implementation.

No, I am in no way knocking development efforts, and yes it is a Big Deal! I have only read good things about what BtrFS is going to deliver....

However, I from what I have read while BtrFS is available now it is very much Alpha and it would be a number of years before its for mainstream use...you are the first person I have come across who says its sooner than you think!

I was asking why it wasn't feasable for advfs to be ported to directly compete with Suns ZFS, given that AdvFS is a proven enterprise level filesystem and is available for porting. 

BUT given what you have said,  I do understand why its better to wait for BtrFS Now! :)

---

### Post by Regenweald on 2009-10-06
A nice article on BTrFS. Some good info for those interested:
[http://www.h-online.com/open/The-Btrfs-file-system--/features/113738/0](http://www.h-online.com/open/The-Btrfs-file-system--/features/113738/0)

---

### Post by Gourgi on 2009-10-07
> **Regenweald said:**
> A nice article on BTrFS. Some good info for those interested:
[http://www.h-online.com/open/The-Btrfs-file-system--/features/113738/0](http://www.h-online.com/open/The-Btrfs-file-system--/features/113738/0)
interesting indeed.
there are not much btrfs articles out there so thanks for sharing it!

---


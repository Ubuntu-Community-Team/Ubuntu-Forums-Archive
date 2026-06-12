---
title: "Ext4 data loss stopped?"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by olskar on 2009-04-03
According to the bugreport about this ( [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781?comments=all) ) a fix has been released, can anyone confirm that here? :)

---

### Post by Kow on 2009-04-03
Yes. ext4 seems to be working exactly as intended.

---

### Post by plun on 2009-04-03
Nope... you have several fixes within 2.6.29.1 which is not merged to the Ubuntu 2.6.28 kernel.

---

### Post by Kosimo on 2009-04-03
> **plun said:**
> Nope... you have several fixes within 2.6.29.1 which is not merged to the Ubuntu 2.6.28 kernel.

one more reason to get 2.6.29.1 :KS

---

### Post by MadsRH on 2009-04-03
> **plun said:**
> Nope... you have several fixes within 2.6.29.1 which is not merged to the Ubuntu 2.6.28 kernel.

Any idea if it will make it in before KernelFreeze April 9th?

---

### Post by FuturePilot on 2009-04-03
> **olskar said:**
> According to the bugreport about this ( [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781?comments=all) ) a fix has been released, can anyone confirm that here? :)
Yes it was fixed

> **plun said:**
> Nope... you have several fixes within 2.6.29.1 which is not merged to the Ubuntu 2.6.28 kernel.

Please read 
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/56]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/56")

and
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/154]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/154")

Those were backported from another kernel. It *is* fixed.

---

### Post by plun on 2009-04-03
> **FuturePilot said:**
> Yes it was fixed


Nope...   Linus went crazy :-\" and new one was done 

> commit 395d73413c5656c6d7706ae91dcb441f9b7e3074
Merge: c226fd6... 06705bf...
Author: Linus Torvalds <torvalds@linux-foundation.org>
Date:   Wed Apr 1 10:57:49 2009 -0700

    Merge branch 'for_linus' of git://git.kernel.org/pub/scm/linux/kernel/git/tytso/ext4
    
    * 'for_linus' of git://git.kernel.org/pub/scm/linux/kernel/git/tytso/ext4: (33 commits)
      ext4: Regularize mount options
      ext4: fix locking typo in mballoc which could cause soft lockup hangs
      ext4: fix typo which causes a memory leak on error path
      jbd2: Update locking coments
      ext4: Rename pa_linear to pa_type
      ext4: add checks of block references for non-extent inodes
      ext4: Check for an valid i_mode when reading the inode from disk
      ext4: Use WRITE_SYNC for commits which are caused by fsync()
      ext4: Add auto_da_alloc mount option
      ext4: Use struct flex_groups to calculate get_orlov_stats()
      ext4: Use atomic_t's in struct flex_groups
      ext4: remove /proc tuning knobs
      ext4: Add sysfs support
      ext4: Track lifetime disk writes
      ext4: Fix discard of inode prealloc space with delayed allocation.
      ext4: Automatically allocate delay allocated blocks on rename
      ext4: Automatically allocate delay allocated blocks on close
      ext4: add EXT4_IOC_ALLOC_DA_BLKS ioctl
      ext4: Simplify delalloc code by removing mpage_da_writepages()
      ext4: Save stack space by removing fake buffer heads
      ...



---

### Post by phenest on 2009-04-03
Are we still looking for 2.6.29 kernel for the fix, or a later version? And will it make it to Jaunty in the near future? I'd rather not use ext4 until this is sorted out.

---

### Post by phenest on 2009-04-03
Perhaps some one aught to put a sticky up to clarify the position of ext4.

---

### Post by plun on 2009-04-03
> **phenest said:**
> Are we still looking for 2.6.29 kernel for the fix, or a later version? And will it make it to Jaunty in the near future? I'd rather not use ext4 until this is sorted out.

Nope... we just needs all patches for EXT4.

EXT4 is great and this is the final of needed small fixes.

---

### Post by olskar on 2009-04-03
> **plun said:**
> Nope... we just needs all patches for EXT4.

EXT4 is great and this is the final of needed small fixes.

Should the bug once again be marked as In progress instead of Fix released then?

---

### Post by plun on 2009-04-03
> **olskar said:**
> Should the bug once again be marked as In progress instead of Fix released then?

"The bug" has been in progress all the time.

as I wrote Linus asked (went crazy) about Ext4 and some behavior, Ted fixed it.

;)

---

### Post by olskar on 2009-04-03
> **plun said:**
> "The bug" has been in progress all the time.

as I wrote Linus asked (went crazy) about Ext4 and some behavior, Ted fixed it.

;)

Yes, I was mostly reffering to the bugreport in Launchpad that is marked as fixed; [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781)

Perhaps you should add some info you got over there :)

Personally, I feel like I'm not able to keep up with this Ext4 business so I'm happy some people seems to be :)

---

### Post by plun on 2009-04-03
> **olskar said:**
> 
Perhaps you should add some info you got over there :)


I am rather sure that the kernel team knows about this....;)

When Linus wakes up its urgent...

---

### Post by nicedanmonkey on 2009-04-03
I'm using ext4 right now. To take advantage of these fixes will I have to redo my filesystem or will I get the changes automatically with a kernel update?

---

### Post by MacUntu on 2009-04-03
> **plun said:**
> When Linus wakes up

he usually forgets his good manners. I didn't know if I should laugh or shake my head when I was reading the "discussion". :shock:

---

### Post by olskar on 2009-04-07
Has the new patches been applied to the Jauntykernel now?

---

### Post by habtool on 2009-04-07
From one of Theodore Ts'o reply on launchpad:
until we get 2.6.29, if one is still worried with data loss, you can use nodelalloc attribute with ones ext4 fstab line, something like:


UUID=e3b96b25-6633-4744-9bd9-4c6428acfcbc / ext4 relatime,errors=remount-ro,nodelalloc 0 1

(UUID will be unique, so dont use this one above!)

If this is incorrect, fell free to advise, but this is how I understood it.

Theodore is not keen for us to use nodelalloc, as it will slow things down and cause more fragmentation, but many programs needed to be changed as to how they fsync, as they are using the 5 second fsync's std in ext3. Ext4 writes every say 60 seconds, so a crash in that time can cause zero bit files on newly created files.

Habtool

---

### Post by carlgm on 2009-04-07
> **MacUntu said:**
> he usually forgets his good manners. I didn't know if I should laugh or shake my head when I was reading the "discussion". :shock:

Where could I read this? I haven't seen anything on the usual places I check.

I Think I might have found it: [http://thread.gmane.org/gmane.linux.kernel/811167/focus=811228](http://thread.gmane.org/gmane.linux.kernel/811167/focus=811228) ?

---

### Post by FrancoNero on 2009-04-07
what I really wanna know is, whether I can safely install jaunty with ext4 once the RC is out. can that question be answered?

---

### Post by habtool on 2009-04-07
I am sure you can, but as long as programs are relying on the 5 sec ext3 fsync function and not writing to disk themselves, you may need to add the ,nodelalloc, to your ext4 options in fstab.

I am running without ,nodelalloc, to see if it looses data for me.

If X locks, i will just ctl alt F1 to a tty and sudo sync.

Hope this helps

---

### Post by meho_r on 2009-04-07
But what when the lock is so bad that even Ctrl+Alt+F1 doesn't help, and it does happen from time to time? I'm still undecided if I would personally use ext4 in Jaunty. Koala, maybe.

---

### Post by crjackson on 2009-04-07
I too would like to enjoy the reported speed of ext4, but stability is paramount for me, so I'll stay at ext3 until everything smooths out.

---

### Post by kurros on 2009-04-07
I'm confident in the dataloss issues mentioned being fixed in Ubuntu's sauce. But I still get soft lockups from rapid IO (compiling large source trees, emptying trash, etc)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824)

If it's not resolved by Jaunty release then i'll probably re-install with ext3. Not looking forward to the first mandatory fsck after that though.

---

### Post by habtool on 2009-04-08
The main issue, as mentioned by Theodore Ts'o, is that many programs are relying on ext3's write every 5 seconds, so the programs dont explicitly write to disk themselves.

EXT4 has a design feature, like ZFS BTRFS and all modern FS's, using delayed allocation as a technique to improve speed and improve de-fragmentation, this is NOT a BUG in EXT4 and the lead developer, mentioned above, will not be removing delayed allocation. (or making it 5 seconds like ext3)
We need the program developers to modify their code to explicitly fsync as often as they require. This will take time, as user will need to pester program developers who's programs are loosing data to update their code.

Their is however a temporary work around that anyone can use now, being ,nodelalloc, this will need to be added to mount options in FSTAB.

Waiting till Jaunty +1 is NOT going to change the EXT4 delayed allocation system. He has changed the way it saves existing files, but appears adamant that he is POSIX compliant and its now up to the individual program coders to update their code to work with a modern FS like EXT4.

Short answer is simply use ,nodelalloc, in FSTAB if you are worried.

Regards
Habtool

There are some changes coming to 2.6.29 +
[http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892](http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892)

---

### Post by habtool on 2009-04-08
Info on adding nodelalloc and testing if it worked:

at a terminal type: mount

before
/dev/sdb2 on / type ext4 (rw,relatime,errors=remount-ro)

after
/dev/sdb2 on / type ext4 (rw,relatime,errors=remount-ro,nodelalloc)

(To enable no delayed allocation...)
nodelalloc added in FSTAB
# / was on /dev/sdb2 during installation
UUID=e3b96b25-6633-4744-9bd9-4c6428acfcbc /               ext4    relatime,errors=remount-ro,nodelalloc	 0       1

---

### Post by FrancoNero on 2009-04-09
> **habtool said:**
> The main issue, as mentioned by Theodore Ts'o, is that many programs are relying on ext3's write every 5 seconds, so the programs dont explicitly write to disk themselves.

EXT4 has a design feature, like ZFS BTRFS and all modern FS's, using delayed allocation as a technique to improve speed and improve de-fragmentation, this is NOT a BUG in EXT4 and the lead developer, mentioned above, will not be removing delayed allocation. (or making it 5 seconds like ext3)
We need the program developers to modify their code to explicitly fsync as often as they require. This will take time, as user will need to pester program developers who's programs are loosing data to update their code.

Their is however a temporary work around that anyone can use now, being ,nodelalloc, this will need to be added to mount options in FSTAB.

Waiting till Jaunty +1 is NOT going to change the EXT4 delayed allocation system. He has changed the way it saves existing files, but appears adamant that he is POSIX compliant and its now up to the individual program coders to update their code to work with a modern FS like EXT4.

Short answer is simply use ,nodelalloc, in FSTAB if you are worried.

Regards
Habtool

There are some changes coming to 2.6.29 +
[http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892](http://www.h-online.com/open/Ext4-data-loss-explanations-and-workarounds--/news/112892)

thanks. with my limited knowledge of what you're talking about I can understand this, but what about the rest of the "human beings" ubuntu professes to aim at? would most of the programs used by the distro have code updated for this posix compliant method?

---

### Post by megamania on 2009-04-09
> **FrancoNero said:**
> what about the rest of the "human beings" ubuntu professes to aim at? would most of the programs used by the distro have code updated for this posix compliant method?
Aims and reality are two different things, unfortunately.

Linux is not for everybody. I've been using Linux (and only linux) for five years now, and I think I can say it is *not* for everybody by nature: since anybody can contribute, there will never be a single beaten track as it is for Microsoft or Apple.

That's the beauty of Linux - but also its major problem, depending on how you see it.

---

### Post by habtool on 2009-04-09
> **FrancoNero said:**
> thanks. with my limited knowledge of what you're talking about I can understand this, but what about the rest of the "human beings" ubuntu professes to aim at? would most of the programs used by the distro have code updated for this posix compliant method?

@FrancoNero

Ubuntu Jaunty 9.04 is defaulting to EXT3 so the humans have nothing to worry about and can install 9.04 with ext3 and be non the wiser to the teething 'problems' of ext 4 and programs that need to be tweaked to suite ext4 / POSIX complaint.

I am sure the Ubuntu devs will make a informed decision about ext4 in the 9.10 cycle, should there still be issues with lost data, all they would need to do is add the ,nodelalloc option as standard and all will be well. Ubuntu +1 / 9.10 is still a long way off, so panicking is way premature.
Ubuntu is NOT fedora, so the devs certainly are not trying to be at the cutting edge for the sake of being there, esp not at the expenses of the Humans ;)
(that said we do need the fedora's of the Linux world as they are pioneering the next generations of Linux)

Please bear in mind that this discussion is happening for alpha/beta testers that enjoy messing around and don't mind crashes and data loss, as we have backups etc.
We are here to help bug fix and find these sort of problems, so the humans don't get any nasty surprises.

Ubuntu Forums > The Ubuntu Forum Community  > Other Community Discussions  > Development & Programming  > Jaunty Jackalope Testing and Discussion  > 

I am personally looking forward to BTRFS and its snapshots :)

---

### Post by FrancoNero on 2009-04-12
good reply, thanks.

I'm waiting for the Release Candidate now and some more recent comments/reviews, and then i'm gonna wipe that 32bit Vista off my new Thinkpad :D it came with 4gig RAM so I'm looking forward to actually using those :)

---

### Post by ZarathustraDK on 2009-04-16
So, any weigh-ins on how much slower it is when using nodealloc in fstab? Is it ext3-speed or inbetween ext3 and ext4-w/o-nodealloc?

If it's faster than ext3 then one might as well give it a try.

---

### Post by tonyric on 2009-04-17
Time to break out the 250GB HDD for my thinkpad to try it out. I had to go back to 8.10 with KDE 4.2 to be happy AND not lose data. This weekend is the time to see if it blows up my laptop again.

---

### Post by slashdotfx on 2009-04-18
I'm using ext4 at the moment,
can I downgrade to ext3?

any how to?

thx

---

### Post by FuturePilot on 2009-04-18
> **slashdotfx said:**
> I'm using ext4 at the moment,
can I downgrade to ext3?

any how to?

thx

Nothing short of a reformat. Converting file systems is a one way street.

---

### Post by MacUntu on 2009-04-18
Well, there IS a way to downgrade. You need to remount the partition with the noextents mount option, copy all files to a temp dir and rewrite the original files with their copies. Then you can clear the INCOMPAT_EXTENTS flag with tune2fs and remount the partition as ext3. Not so easy but working without doing a reformat. :P

---

### Post by Bios Element on 2009-04-18
> **slashdotfx said:**
> I'm using ext4 at the moment,
can I downgrade to ext3?

any how to?

thx

Why would you want to do that? I've been using it for near a month and it's working faster then ever.

---

### Post by growled on 2009-04-18
It's working fine here as well.

---

### Post by tonyric on 2009-04-19
> **tonyric said:**
> Time to break out the 250GB HDD for my thinkpad to try it out. I had to go back to 8.10 with KDE 4.2 to be happy AND not lose data. This weekend is the time to see if it blows up my laptop again.

Problem remains. Hard drive that has operated for 1.5 years and still had an old intrepid install on it was formatted with ext4. Things were great until it was fully patched and 200GB copied to the disk. Then 8 hours later, after sitting overnight idle, I went to run synaptic and boom, wouldn't work any longer since /var was "read only" which is funny since /var is on the / partition (only 1 filesystem on the machine). Rebooted and hundreds of crossed inodes and multiply claimed blocks. 

Pulled the 250 out of the laptop and put the 500 with Intrepid back in.

I had the same problem previously with XFS and EXT3 using Jaunty on the 500GB drive, so I know it isn't the drive.

Tony

---

### Post by nanog on 2009-04-19
I've had several nfs arrays running ext4 for many months with no problems. The speed difference is AMAZING (~40 mb/s vs 20-30 for ext3). I'd use btrfs but when I last tested it it was painfully slow.

---


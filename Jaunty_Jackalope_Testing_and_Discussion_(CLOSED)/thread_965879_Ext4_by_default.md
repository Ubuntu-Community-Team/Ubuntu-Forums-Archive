---
title: "Ext4 by default"
date: 2008-10-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by int on 2008-10-31
Please add ext4fs and choose for installation...
Reasons:
1. Speedup file removing
2. Better and faster allocator
3. Bigger max file size
4. Precision timestamps
5. Bigger max number of folder inclusion
6. Faster indexation
7. Faster checking
8. Re-allocation for better video recording, torrent downloading etc.

[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)
------------------------------------------------------------------------------------------------------------

**== To test is needed ==**
* Kernel 2.6.28 [COLOR="SeaGreen"]**DONE**[/COLOR]
* ubuntu-installer that support ext4 [COLOR="SeaGreen"]**DONE**[/COLOR]
* e2fsprogs version 1.41.0 or higher is required [COLOR="SeaGreen"]**DONE**[/COLOR]

**== To enable to /boot/ on the same partition. ==**
One of the next
a) grub support ext4 [COLOR="SeaGreen"]**DONE**[/COLOR]
b) grub2 as default bootloader [COLOR="Orange"]**NOT AS DEFAULT**[/COLOR]


**== Tools  ==**
* The next release of GParted (0.4.2). [COLOR="SeaGreen"]**RELEASED**[/COLOR]

---

### Post by kahping on 2008-10-31
I'd definitely want to take ext4 for a spin, but as default it would really be bad if there's problems. Better let it be optional so people have to choose to take that risk.

It normally takes years of usage to be sure there's no surprises, right?

---

### Post by sdowney717 on 2008-10-31
[http://fedoraproject.org/wiki/Features/Ext4](http://fedoraproject.org/wiki/Features/Ext4)

---

### Post by gnomeuser on 2008-10-31
> **sdowney717 said:**
> [http://fedoraproject.org/wiki/Features/Ext4](http://fedoraproject.org/wiki/Features/Ext4)

Indeed, I have been running on Ext4 since early in the F9 development cycle. I have never seen a problem with using it on my machines, and now that it has left behind the development status upstream it signifies a good time to adopt.

If Fedora 10 had not been in a development and feature freeze, the maintainer of the feature has expressed a desire to have pushed for the switch to be flipped and default to ext4. I suspect this will happen first thing after F11 development opens. As such it would probably be a good time for Ubuntu to adopt as well, share the experiences yet not the pain (since ext4 is an evolution of the stable ext3 code and has been tested heavily in Fedora for a year every major bug should have been shaken out of it making it low risk).

I would strongly favor adopting ext4, it has been very good to me and many other people. Also I have not heard any horror stories of ext4 eating babies from any of the testers which is also a very encouraging sign.

---

### Post by Timon&amp;Pumba on 2008-11-01
There should also be ext4 support in Grub, so that we can boot from an ext4 filesystem.
But I get it is not too hard to develop that in 6 months, or is it?

---

### Post by gnomeuser on 2008-11-01
> **Timon&Pumba said:**
> There should also be ext4 support in Grub, so that we can boot from an ext4 filesystem.
But I get it is not too hard to develop that in 6 months, or is it?

I believe openSUSE had a Google Summer of Code student who worked on this, I don't know how far along that project has come though. But if we can't make this work before Jaunty, the simple solution would be to create /boot on a small separate ext3 partition (which is also a good idea since that allows us to mount it only on demand, lowering the risk of accidently kernel image corruption).

[http://code.google.com/soc/2008/suse/appinfo.html?csaid=91DC4C762E7EE6D7](http://code.google.com/soc/2008/suse/appinfo.html?csaid=91DC4C762E7EE6D7)

Grub2 apparently supports EXt4 with extends, so that is one solution right there though not without issues.
[http://www.mail-archive.com/bug-grub@gnu.org/msg11692.html](http://www.mail-archive.com/bug-grub@gnu.org/msg11692.html)

---

### Post by apoth on 2008-11-01
By default would be preferable, but not if there's more than the absolute tiniest risk of data loss.

---

### Post by Quikee on 2008-11-01
Now that it has been out of development it should be available at least as an option. There is no need to rush and enable it by default just yet - anyone that wants it can migrate from ext3 easily.

---

### Post by plun on 2008-11-01
> **Timon&Pumba said:**
> There should also be ext4 support in Grub, so that we can boot from an ext4 filesystem.
But I get it is not too hard to develop that in 6 months, or is it?

Well...

Ext4 is hardened with kernel 2.6.28 and with RC2 some bugs are fixed

[http://lkml.org/lkml/2008/10/26/159](http://lkml.org/lkml/2008/10/26/159)

This one is also important:

[http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)

>   **For people who are running Ubuntu**

For people who are running Ubuntu, it is *highly* recommended that you download a set of modified util-linux packages and install them. Packages for Ubuntu Hardy are available here. These packages revert a change made by Ubuntu to use the volid library instead of the blkid library. The volid library has a number of shortcomings, including that they don't work on freshly created filesystems or swap devices until after you reboot (since it is tied to udev probing) and the volid library doesn't understand ext4dev filesystems. The blkid library is much better, and Debian uses the blkid library for util-linux. **Unfortunately, Ubuntu chose to make this reason for some unknown reason**. For other versions of Ubuntu, the patch that was applied can be found here. 


So this must be clarified and also that testing starts as soon as possible.
[B]
We cannot let others do the "hard work".  !!![/B]

I don't believe its possible with default EXT4, but maybe...:confused:

(This also means that users which understands backups can test....)

---

### Post by PatrickVogeli on 2008-11-01
I'd rather choose xfs or jfs, both of which seem to perform better than ext2/3 and have been longer around than ext4

---

### Post by gnomeuser on 2008-11-01
> **Quikee said:**
> Now that it has been out of development it should be available at least as an option. There is no need to rush and enable it by default just yet - anyone that wants it can migrate from ext3 easily.

Actually the migration is not as easy as it would seem. Merely changing ext3 to ext4 in fstab is not enough to gain the full ext4 feature set. You would currently need to reformat (or do a fresh install) to gain the optimal settings. A converter is not yet available (but should amply be possible to create).

One could do such a migration in a second stage upgrade such as Fedora's Anaconda/preupgrade, mainly this would be a good idea because messing with the partition resizing and moving all the data on a running system would be.. unsafe at best.

---

### Post by Changturkey on 2008-11-01
Maybe for 9.10 or whenever Grub2 is out?

---

### Post by gnomeuser on 2008-11-01
> **Changturkey said:**
> Maybe for 9.10 or whenever Grub2 is out?

AS Matthew Garrett puts it, grub2 is going to be the ultimate bootloader for GNU Hurd. It has been in development so long it's unfunny. It's still not complete and likely won't fit every scenario we need for a while. Worse still upstream have all but abandoned grub1 which everyone uses so we pretty much using unmaintained code which won't support ext4 unless someone produces the patch and maintains it themselves.

3 paths logically then present themselves:

1) Add support for ext4 (and btrfs which will also be needed soon) to grub1
2) Put a massive amount of work into helping finish grub2
3) Find an alternative to grub such as extlinux 

Of these number 1 seems the most likely to be the outcome short term.

---

### Post by Eclipse. on 2008-11-01
There is no chance of it being default.

Ext4 still isnt bug free and we need to wait for grub2 (or patch grub1, the first option seems more likely).

Possibley see it available but definetly not defauult.

---

### Post by bash on 2008-11-01
Sure like to see ext4. But as I said in another thread, not if that ends up in a Pulse Audio like mess. There also Fedora picked it up first, everyone was enthralled because it sounded brilliant in theory, but what then ended up in Ubuntu should have definitly not been put in a LTS release. So all I'm saying is: If it's ready, great, then take it and put it in. If it's not though, then please don't rush it in, just so we have it (Offering it as an option then would be ok though).

---

### Post by insane_alien on 2008-11-01
ext4 should be an option in the next release, jaunty+1 can have it by default as it should be stable enough to take up the mantle of ext3 by then.

---

### Post by plun on 2008-11-01
Well... instead of discuss, how do I setup a ext4 partition ?


[http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)


I have 3 partitions and can easily test with one....:)

---

### Post by Quikee on 2008-11-01
> **gnomeuser said:**
> Actually the migration is not as easy as it would seem. Merely changing ext3 to ext4 in fstab is not enough to gain the full ext4 feature set. You would currently need to reformat (or do a fresh install) to gain the optimal settings. A converter is not yet available (but should amply be possible to create).

One could do such a migration in a second stage upgrade such as Fedora's Anaconda/preupgrade, mainly this would be a good idea because messing with the partition resizing and moving all the data on a running system would be.. unsafe at best.

I was not aware of this. As far as I read all needed to do is to enable at least on of the feature of ext4 (extends for example) via tune2fs and the migration will be performed automatically in the next mandatory fsck run.

---

### Post by Slug71 on 2008-11-01
I'm all for EXT4 as default for all the reasons the OP said. I think the only way EXT4 will have all the bugs ironed out is for more people to be using it and therefore should be included from Alpha 1. 

If it can speed up Ubuntu then thats definitely a plus too.

---

### Post by gnomeuser on 2008-11-01
> **Slug71 said:**
> I'm all for EXT4 as default for all the reasons the OP said. I think the only way EXT4 will have all the bugs ironed out is for more people to be using it and therefore should be included from Alpha 1. 

If it can speed up Ubuntu then thats definitely a plus too.

ext4 is already very bugfree, it builds on the ext3 code which has been vetted for years. It has also been tested by hundreds of volunteers over the past year in Fedora alone (just check the smolts.org stats for ext4dev and ext4 - the latter is low for a good reason, the name only just changed and smolt only updates once a month so it will take a while for even all F10 testers to get onboard). 

Aside that a few of the developers have moved production machines to ext4 and while it still doesn't have all the planned features the disk format is forward compatible. The only changes might be tweaks at mkfs time for optimal behaviour but it's not in flux at all. It's stable code.

As for speedups, I will be honest, I don't feel any with my current setup. fsck is faster which is nice but it's an evolution not a revolution (like btrfs is). It brings much needed features to the old and trusty ext3 code, it is faster in most benchmarks but as a user you are unlikely to experience it as a big upgrade. You should not press for ext4 for performance reasons, io is slow regardless of what filesystem you use, it will always be painful so it's better to look at the features we gain. Ext4 is significantly better at scaling to todays large disks, fsck is a big problem on ext3 something ext4 will bring much needed improvement to (multiple TB disks such as is found on kernel.org can take days to perform fsck, which is completely unacceptable downtime). As drives keep growing this problem is increasingly finding it's way to end user desktops, I am already seeing this on my machine and I only have slightly less than a terrabyte of storage in this machine (considering that 1.5 TB drives just started coming out with the promise of 2TB drives in Q109 - this will be a problem on every machine near you soon).

---

### Post by gnomeuser on 2008-11-01
> **Eclipse. said:**
> There is no chance of it being default.

Ext4 still isnt bug free and we need to wait for grub2 (or patch grub1, the first option seems more likely).

Possibley see it available but definetly not defauult.

Okay then please point me to said bugs, also please explain to me how we find them without testing (never mind the fact that we actually have been intensely testing ext4 for over a year on production machines without hitting major bugs).

You also should mention that the support lacking in grub is not booting into ext4 but having /boot on ext4. A problem we can get around either by having a separate /boot which is a perfectly fine compromise till such a time as a patch or grub2 is ready.

---

### Post by Slug71 on 2008-11-01
So i've decided i'm gonna be on board Jaunty with Alpha 1 since the final of Intrepid seems to have gone backwards for me.

If EXT4 isn't included with Alpha 1 of Jaunty, what will be the best way for me to mount it?


Why not include the Alpha or whatever stage Grub2 is at now with Alpha 1 so that EXT4 can be included? Perhaps this could help Grub2 move along a little faster with more people contributing??

---

### Post by SunnyRabbiera on 2008-11-01
I think ext4 should be made optional as many still use ext3 and we dont want people to break their systems.

---

### Post by gnomeuser on 2008-11-01
> **Slug71 said:**
> So i've decided i'm gonna be on board Jaunty with Alpha 1 since the final of Intrepid seems to have gone backwards for me.

If EXT4 isn't included with Alpha 1 of Jaunty, what will be the best way for me to mount it?


Why not include the Alpha or whatever stage Grub2 is at now with Alpha 1 so that EXT4 can be included? Perhaps this could help Grub2 move along a little faster with more people contributing??

I will say this now, no guarantees, a quick way that should work, but remember never.. ever.. under any circumstances change the partition you have /boot on to ext4, it will fail horribly. Double check before doing this that you have a separate partition for /boot.

If the module is compiled with your kernel (and I believe Ubuntu ships ext4 as a module). Then you can change ext3 into ext4 for existing partitions in /etc/fstab. This as I mentioned earlier will not get you all of the ext4 features but will allow you to fully rollback to ext3 in a purely harmless way. 

You can also enable extends, the biggest new feature, to do this I would recommend working on your partitions while not live, so boot a LiveCD and invoke tune2fs -O extends /dev/sdXY (where XY denotes device and partition). Once you have done this, there is no going back to ext3, this needs to be understood fully, you cannot go back to your cozy ext3 ways when extends has been enabled on your partition so be sure you want this. Then I would run fsck on the partition just to be safe.

For this guide to work, your e2fsprogs package must be at least version 1.41 or higher. This version has ext4 support and will be needed.

This still will not get you to a full ext4 experience, since at mkfs time for a new ext4 partition certain parameters are invoked to attain optimal values. THese are set differently on ext3 partitions and cannot to my knowledge easily be changed. To get here thus you will need to backup your data and recreate the partition from scratch, also as these values are being tweaked currently a ext4 partition created now might not be fully optimal for all future changes but it will work, the disk format is stable and there is no obvious adverse stability effects to this.

I will however repeat, do not.. ever.. change the partition containing /boot to ext4, if you do not know how to determine which partition that is, disregard this guide entirely and wait for migration tools to become available or at such a time as installs onto ext4 are supported, do a fresh install.

---

### Post by gnomeuser on 2008-11-01
> **SunnyRabbiera said:**
> I think ext4 should be made optional as many still use ext3 and we dont want people to break their systems.

Existing ext3 partitions could either be left as such or upgraded to ext4 without extends which is 100% compatible and as such should you ever decide to go back to ext3 that is possible simply by changing ext4 to ext3 in fstab. 

This method does not grant all the cool features of ext4 but it does provide a progression to ext4 without regressions and full reversibility. 

Eventually an upgrade might offer a migration to a full ext4 partition, when well tested tools for this have been released or systems like this could be left in the non-optimal state forever to be extra careful.

---

### Post by Metaleks on 2008-11-02
Gonna have to vote no on this one. ext4 recently came out of a "hot development" phase, and while nothing thats really significant will be added to it, it needs a lot more testing. Even having it as an option is too much, in my opinion. I don't think there is a single doubt in anyone's mind that ext4 is better than ext3, or that it will eventually take ext3's place in Ubuntu. But until then, it really needs more testing. This is a *file system* we're talking about. Throwing even the smallest caution to the wind will be detrimental in the long run.

---

### Post by plun on 2008-11-02
Yes and this is a **development forum** where software should be tested...  not endless discussions about rumours.

As soon as possible this testing must start  !!  

Maybe also Ubuntu can contribute to upstream...  ???(real upstream). 

Of course it probably will end in some broken file systems... thats testing and "**** happens".:)

---

### Post by RATM_Owns on 2008-11-02
I wouldn't have it as default in Jaunty but I think there should be a option in the partitioner.

---

### Post by Slug71 on 2008-11-02
> **plun said:**
> Yes and this is a **development forum** where software should be tested...  not endless discussions about rumours.

As soon as possible this testing must start  !!  

Maybe also Ubuntu can contribute to upstream...  ???(real upstream). 

Of course it probably will end in some broken file systems... thats testing and "**** happens".:)

+1
Grub2 and EXT4 along with Kernel 2.6.28 should be included with Alpha1 right from the start.

---

### Post by gnomeuser on 2008-11-02
> **Metaleks said:**
> Gonna have to vote no on this one. ext4 recently came out of a "hot development" phase, and while nothing thats really significant will be added to it, it needs a lot more testing. Even having it as an option is too much, in my opinion. I don't think there is a single doubt in anyone's mind that ext4 is better than ext3, or that it will eventually take ext3's place in Ubuntu. But until then, it really needs more testing. This is a *file system* we're talking about. Throwing even the smallest caution to the wind will be detrimental in the long run.

A years worth of testing without any kinds of dataloss bugs or other regressions. It even managed to improve the ext3 codebase whenever a problem was caused.

There will always be bugs, it's a lot of code but it's not as you would have us believe a hotbed of change which is entirely untested as well as completely new. The filesystem has been deemed stable by it's developers. Cautious people as it already is. 

You have a smooth incremental upgrade with the option of backing out fully to your existing ext3 partition for upgrades with NO RISK AT ALL as well as the option to jump full on to the ext4 path with all the new features enabled. 

Hundreds of people use ext4 today and have done so for a year. No serious bugs have been found during the time of this testing, regression test suites are run on this code often and the tool suite is now complete. I don't understand what more safety you expect will come out of not testing it nor encouraging it's adoption.. for a development cycle (where we do changes far more likely to cause dataloss than the transition from ext3 to ext4 would on a quite regular basis).

---

### Post by Gina on 2008-11-02
This would seem to be a good time to include it and get testing - right at the beginning of a new version cycle.

---

### Post by plun on 2008-11-02
> **Slug71 said:**
> +1
Grub2 and EXT4 along with Kernel 2.6.28 should be included with Alpha1 right from the start.

Well...  we will see what happens  :)

Ben Collins started "Kernel Next" and apparently it wasn't popular.

Maybe we must wait until someone hear "rumors" that someone from Debian says something is "safe" within a mailing list... :confused:

Or to find a howto/guide within "Tutorials and Tips"...:)

"Made in Ubuntu" :)

---

### Post by Slug71 on 2008-11-02
Not sure who we should take it up with, Launchpad or Brainstorm? 

I'll start whichever is most appropriate.

[[IMG]http://brainstorm.ubuntu.com/idea/15155/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/15155/)

Brainstormed it for now.

---

### Post by plun on 2008-11-02
> **Slug71 said:**
> Not sure who we should take it up with, Launchpad or Brainstorm? 



It will for sure be there, the challenge is more to do important functions early in a development cycle.

Not wait for Debian, work directly with upstream.  :)

We have several examples such as Firefox 3, OO-3, PulseAudio.

It will be broken PCs but thats better then a mess after release out of too short testing and lousy test procedures.

---

### Post by Slug71 on 2008-11-02
> **plun said:**
> It will for sure be there, the challenge is more to do important functions early in a development cycle.

Not wait for Debian, work directly with upstream.  :)

We have several examples such as Firefox 3, OO-3, PulseAudio.

It will be broken PCs but thats better then a mess after release out of too short testing and lousy test procedures.

Absolutely.:guitar:

---

### Post by Metaleks on 2008-11-02
> **plun said:**
> Yes and this is a **development forum** where software should be tested...  not endless discussions about rumours.
I agree, but who was discussing rumours? Is it really a rumour that ext4 needs more testing? I thought that it was fact. ext4 has been officially "stable" since October 11th. A mere few weeks have passed. All I'm saying is that lets not jump the gun and make it default for 9.04. I don't see the problem with waiting this out a little more.

---

### Post by Slug71 on 2008-11-02
> **Metaleks said:**
> I agree, but who was discussing rumours? Is it really a rumour that ext4 needs more testing? I thought that it was fact. ext4 has been officially "stable" since October 11th. A mere few weeks have passed. All I'm saying is that lets not jump the gun and make it default for 9.04. I don't see the problem with waiting this out a little more.

I believe he was just generalising with the rumours part as they are always flying around the forum.

That is exactly why now is a good time to bring in Ext4. Ext4 will be the future for the next few years now and if its deemed stable then why not bring it in so that it can be thoroughly tested and polished?

---

### Post by of_darkness on 2008-11-02
if it is on by default then the boot issue must be solved 1st.

Grub2, well i loked arund the wiki for grub2 and nothing about X86-64 suport, only a test on a 64bit platform but no real plans on suport for 64bit so im very sckeptical about it.

Mabe fixing suport in leagcy grub so long as it dosent make it bad in any way and i think it is somthing that neads extensive testing ,more then 6months normal testing. if it got alot of testers doing some intensive try to brake it testing then maybe..


So put it optional untill its tested and working solidly as it is souch a critical pize of software thats neads to be treated whit silk glowes in part.

---

### Post by Slug71 on 2008-11-02
> **of_darkness said:**
> if it is on by default then the boot issue must be solved 1st.

Grub2, well i loked arund the wiki for grub2 and nothing about X86-64 suport, only a test on a 64bit platform but no real plans on suport for 64bit so im very sckeptical about it.

Mabe fixing suport in leagcy grub so long as it dosent make it bad in any way and i think it is somthing that neads extensive testing ,more then 6months normal testing. if it got alot of testers doing some intensive try to brake it testing then maybe..


So put it optional untill its tested and working solidly as it is souch a critical pize of software thats neads to be treated whit silk glowes in part.

Grub2 must have 64bit support since they're both gonna be around for a while. But thats why i said Grub2 should also be added from Alpha 1 so that it can move along faster.

Ext4 has been tested for around a year now and has been deemed 'stable' as of Oct 11. Read Gnomeuser's posts about Ext4.

---

### Post by kernelhaxor on 2008-11-02
ext4 is alread out of development and testing is goin on .. I think it wud be pretty stable by next April .. personally, I would use it if available at least as an option

---

### Post by BwackNinja on 2008-11-02
Is there even all that much point in 64-bit support for grub2? Regardless if it is a 32-bit or 64-bit program, it should still be able to load operating systems, and having grub2 as the _one_ 32-bit app in a 64-bit install shouldn't make anyone cry. I have a 32-bit grub loading both 32-bit and 64-bit operating systems.

I can't wait until grub-legacy is out of the picture and grub2 becomes mainstream.

---

### Post by Slug71 on 2008-11-03
Has anyone tried the last Alpha version of Grub2 to come out back in Feb?

---

### Post by plun on 2008-11-03
> **Slug71 said:**
> Has anyone tried the last Alpha version of Grub2 to come out back in Feb?

Can you find a good howto and "trouble shooter" so start a new thread and we can test this piece of software... ;)

Ubuntus version is from May.
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=grub2](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=grub2)


I never tests anything without good documentation and I didn't find any good upstream.


I also compiling a kernel with Ext4 support, I need a Ubuntu Ext4 "howto"):P

---

### Post by Slug71 on 2008-11-03
Will see what i can find plun.:p

It seems Ubuntus version from May clears up the 64/32bit issues as there's versions for both.

---

### Post by plun on 2008-11-03
> **Slug71 said:**
> Will see what i can find plun.:p

Found it....;)

[http://grub.enbug.org/](http://grub.enbug.org/)

Manual
[http://grub.enbug.org/Manual](http://grub.enbug.org/Manual)


But.... Debian/Ubuntu specific :confused:

---

### Post by Eclipse. on 2008-11-03
All this talk of Grub2, I'm sorry to disapoint but its never going to happen.Its just not ready yet.The developers havent even got to the stage of begining to stabilizing it.PLus it has been delayed so many times its unrealistic to put a date on its release, if were are going to use it we will just need to stick with grub legacy and patch it.

---

### Post by Slug71 on 2008-11-03
Uhh, they're going to begin stabilising this month.

---

### Post by Eclipse. on 2008-11-03
> **Slug71 said:**
> Uhh, they're going to begin stabilising this month.


There was also supposed to be a beta 2 years ago.

---

### Post by Slug71 on 2008-11-03
Migrating to Ext4

[http://www.ibm.com/developerworks/library/l-ext4/index.html](http://www.ibm.com/developerworks/library/l-ext4/index.html)


Also found this

[http://lwn.net/Articles/302391/](http://lwn.net/Articles/302391/)

---

### Post by plun on 2008-11-03
> **Slug71 said:**
> Migrating to Ext4

[http://www.ibm.com/developerworks/library/l-ext4/index.html](http://www.ibm.com/developerworks/library/l-ext4/index.html)



I think this is better

[http://ext4.wiki.kernel.org/index.php/Main_Page](http://ext4.wiki.kernel.org/index.php/Main_Page)

And this one

[http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)


BUT... I am stucked within this writing:

>   For people who are running Ubuntu

For people who are running Ubuntu, it is *highly* recommended that you download a set of modified util-linux packages and install them. Packages for Ubuntu Hardy are available here. These packages revert a change made by Ubuntu to use the volid library instead of the blkid library. The volid library has a number of shortcomings, including that they don't work on freshly created filesystems or swap devices until after you reboot (since it is tied to udev probing) and the volid library doesn't understand ext4dev filesystems. The blkid library is much better, and Debian uses the blkid library for util-linux. Unfortunately, Ubuntu chose to make this reason for some unknown reason. For other versions of Ubuntu, the patch that was applied can be found here. 


I am compiling 2.6.28-RC3 for the moment and it takes 2 hours.

**ext4dev** is also renamed to just **ext4** within this kernel. 

;)

---

### Post by Slug71 on 2008-11-03
> **plun said:**
> I think this is better

[http://ext4.wiki.kernel.org/index.php/Main_Page](http://ext4.wiki.kernel.org/index.php/Main_Page)

And this one

[http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)


BUT... I am stucked within this writing:



Yes i like what you have found better




I am compiling 2.6.28-RC3 for the moment and it takes 2 hours.

**ext4dev** is also renamed to just **ext4** within this kernel. 

;)

It appears 2.6.28 does have support for Ext4

---

### Post by plun on 2008-11-03
> **Slug71 said:**
> It appears 2.6.28 does have support for Ext4

Yes... its an important function within 2.6.28.

But it must be enabled with the kernel config

About kernel compile:

tseliots thread: 
[http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)

Master kernel thread_
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)


Then kernelcheck when you knows how it works..
[http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/)

---

### Post by Slug71 on 2008-11-03
Thanks for that plun seems a lot easier that way and i dont have to break my install. I might just try compile a kernel(2.6.28.) with Wayland and Grub2

Nevermind, cant do Wayland yet.

---

### Post by hellion0 on 2008-11-03
> **Timon&Pumba said:**
> There should also be ext4 support in Grub, so that we can boot from an ext4 filesystem.
But I get it is not too hard to develop that in 6 months, or is it?It's something like this that makes me say it should certainly be an option, but not yet the default.

---

### Post by MacUntu on 2008-11-04
Make it an option. Ext4 left development state but still broad testing is needed to consider something as important as a filesystem stable enough to get default.

---

### Post by gnomeuser on 2008-11-04
> **MacUntu said:**
> Make it an option. Ext4 left development state but still broad testing is needed to consider something as important as a filesystem stable enough to get default.

How does +700 people running it for a year sound in terms of testing as well as artificial stress tests, without hitting major issues that is?

---

### Post by MacUntu on 2008-11-04
700+ doesn't sound overwhelming to me but I can't remember the beginnings of ext3 so that's just a gut feeling. On the other hand ext4 isn't something made from scratch...

9.04 dev cycle would be a good time to test ext4 "in the wild" but I'm not yet convinced it should be default.

It's also a matter of how far the software around ext4 is developed. Starts with GRUB, ends with all the tools eg. for accessing the partitions with other OS.

---

### Post by ShirishAg75 on 2008-11-04
I made a tracking bug [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/293465](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/293465) for 9.04 or 9.04+1 whenever things happen. Please subscribe to the same, and add any new info. as and when it comes along to the same.

---

### Post by plun on 2008-11-04
> **Slug71 said:**
> Thanks for that plun seems a lot easier that way and i dont have to break my install. I might just try compile a kernel(2.6.28.) with Wayland and Grub2

Nevermind, cant do Wayland yet.


Well... here we go  :lolflag:


```
plun@plun:~/$sudo umount /Min

plun@plun:~/$ sudo tune2fs -O extents -E test_fs **/dev/sda3**
tune2fs 1.41.3 (12-Oct-2008)
Setting test filesystem flag

plun@plun:~/$sudo blkid

/dev/sda1: UUID="CE44EAB544EAA007" TYPE="ntfs" 
/dev/sda2: UUID="01d4a969-5b4c-499a-8ef2-6fca71fe2ccd" TYPE="ext3" 
/dev/sda3: UUID="1bd53d0e-a190-4358-a24f-cdea59941581" TYPE=**"ext4dev"** 
/dev/sda4: UUID="ea60a35d-3a50-4b02-8eda-60da18ad08fd" TYPE="ext3" 


plun@plun:~/$ sudo mount -t ext4 /dev/sda3 /Min
```


Rather confusing filesystem...   ext4dev is also used, latest kernel should use ext4.  Latest e2fsprogs  ?

Seems to work.... after reboot ?  ):P


EDIT

Survived.... fsck goes in also for a "force check"

```
Nov  4 17:58:57 plun kernel: [   20.769547] lp0: using parport0 (interrupt-driven).
Nov  4 17:58:57 plun kernel: [  190.824242] EXT3 FS on sda2, internal journal
Nov  4 17:58:57 plun kernel: [  408.632314] EXT4-fs: barriers enabled
Nov  4 17:58:57 plun kernel: [  408.638889] kjournald2 starting.  Commit interval 5 seconds
Nov  4 17:58:57 plun kernel: [  408.639119] EXT4 FS on sda3, internal journal on sda3:8
Nov  4 17:58:57 plun kernel: [  408.639123] EXT4-fs: delayed allocation enabled
Nov  4 17:58:57 plun kernel: [  408.639322] EXT4-fs: mballoc enabled
Nov  4 17:58:57 plun kernel: [  408.639328] EXT4-fs: mounted filesystem with ordered data mode.
Nov  4 17:58:57 plun kernel: [  408.679801] kjournald starting.  Commit interval 5 seconds
Nov  4 17:58:57 plun kernel: [  408.680037] EXT3 FS on sda4, internal journal
Nov  4 17:58:57 plun kernel: [  408.680044] EXT3-fs: mounted filesystem with ordered data mode.
```


Note that I am also using latest e2fsprogs from GIT according to kernel.org wiki.


EDIT again.. after reboot its just ext4 with kernel 2.6.28

```
plun@plun:~$ sudo blkid
[sudo] password for plun: 
/dev/sda1: UUID="CE44EAB544EAA007" TYPE="ntfs" 
/dev/sda2: UUID="01d4a969-5b4c-499a-8ef2-6fca71fe2ccd" TYPE="ext3" 
**/dev/sda3: UUID="1bd53d0e-a190-4358-a24f-cdea59941581" TYPE="ext4"** 
/dev/sda4: UUID="ea60a35d-3a50-4b02-8eda-60da18ad08fd" TYPE="ext3" 

```

---

### Post by int on 2008-11-06
**EXT4**
Fedora 10 brings a fully ext4-compatible e2fsprogs. In addition Anaconda's partition screen has an ext4 filesystem option available if you launch the installer with the ext4 option.

Fedora 10 also brings delayed allocation for ext4. However, ext4 in Fedora 10 does not currently support filesystems larger than 16 terabytes.


Site: [Source]("http://fedoraproject.org/wiki/Releases/10/Beta/ReleaseNotes#EXT4")

---

### Post by gnomeuser on 2008-11-06
> **int said:**
> **EXT4**
Fedora 10 brings a fully ext4-compatible e2fsprogs. In addition Anaconda's partition screen has an ext4 filesystem option available if you launch the installer with the ext4 option.

Fedora 10 also brings delayed allocation for ext4. However, ext4 in Fedora 10 does not currently support filesystems larger than 16 terabytes.


Site: [Source]("http://fedoraproject.org/wiki/Releases/10/Beta/ReleaseNotes#EXT4")

e2fsprogs 1.41 is compatible, I believe that is what ships in Intrepid as well (or you have patches applied - I saw on the mailing list). also..go Fedora.. yay! (I had to)

---

### Post by Sophont on 2008-11-09
As an option - sure. Always nice to have options.

As default - I don't see how that makes sense. From what I gathered the changes on performances won't be felt by most typical users and the biggest advantages are for use cases that are not typical (very large files, huge filesystems, etc...).

So even when the risks are low enough there simply are no compelling features (for typical users) to make it worth *any* risk.

And that's without taking missing support from tools and grub into account.

Advanced users who really need it's new features and can make it work will also be able to install it.

---

### Post by Gina on 2008-11-09
> **sophont said:**
> as an option - sure. Always nice to have options.

As default - i don't see how that makes sense. From what i gathered the changes on performances won't be felt by most typical users and the biggest advantages are for use cases that are not typical (very large files, huge filesystems, etc...).

So even when the risks are low enough there simply are no compelling features (for typical users) to make it worth *any* risk.

And that's without taking missing support from tools and grub into account.

Advanced users who really need it's new features and can make it work will also be able to install it.+1

---

### Post by Progressive on 2008-11-18
Well, we are very early in development of a non-LTS release. I think ext4 would be a great idea considering the minimal risk. If anything does break, we can always switch anytime between alpha 2 and beta.

Also, it mentions improvements for torrents and deleting files. Both of those things should be considered highly useful for average users.

Let's not let fedora beat us

---

### Post by Slug71 on 2008-11-18
> **Progressive said:**
> Well, we are very early in development of a non-LTS release. I think ext4 would be a great idea considering the minimal risk. If anything does break, we can always switch anytime between alpha 2 and beta.

Also, it mentions improvements for torrents and deleting files. Both of those things should be considered highly useful for average users.

Let's not let fedora beat us

Yep exactly. EXT3 will always be there anyway for the people that do not want to use Ext4.

---

### Post by poebae on 2008-11-18
I'd be willing to be a guinea pig for an ext4 test. Given Ubuntu's massive userbase, this is a great chance for Ubuntu to contribute something back to the rest of the Linux community, by rigorously testing ext4 and reporting any bugs or holes.

I know that not every user shares my sentiment and they want their system to have the most stable, secure FS available, but it'd be great if ext4 was at least included as an option.

---

### Post by Slug71 on 2008-11-18
Well according to Linus its ready to go.

[http://www.linux-magazine.com/online/news/kernel_ext_4_filesystem_moves_beyond_developer_status](http://www.linux-magazine.com/online/news/kernel_ext_4_filesystem_moves_beyond_developer_status)



Another reason to give us 2.6.28 ASAP!

---

### Post by Progressive on 2008-11-18
If Linus said it then that is The Word. I mean, who else needs to approve? Stephen Colbert?

---

### Post by Slug71 on 2008-11-18
Yep,

And last i heard Ext4 is bootable with Grub Legacy. I either read it here somewhere or when i was searching Google for info. 
Not sure how true it is but apparently it was just a bug. Hopefully it is true.

---

### Post by Progressive on 2008-11-18
If you look in the expanded list of Jaunty blueprints, you will notice that Ext4 is already added as a proposed feature.

[https://blueprints.launchpad.net/ubuntu/jaunty/+specs?show=all](https://blueprints.launchpad.net/ubuntu/jaunty/+specs?show=all)

---

### Post by RAOF on 2008-11-19
It's worth noting that anyone can propose blueprints, and that blueprint doesn't seem to be associated with an active Ubuntu developer (as determined by MOTU, core-dev, or ubuntu-universe-contributors status).  He could certainly go to UDS and suggest to have a session discussing the merits, though.

I don't have a firm grasp of the benefits/risks of EXT4, but I'm not sure that it's the best idea to go from "it's now declared stable" to "let's make it default".  It'll already receive much wider testing by being available in Fedora 10 and (presumably) Jaunty.  Give it a release or two for this wide testing (with self-selecting clueful users) to catch some of the really obscure corner cases that are undoubtedly hiding away in there.  Then set it as the default the people who don't know or care what their filesystem is get.

---

### Post by gnomeuser on 2008-11-19
> **RAOF said:**
> It's worth noting that anyone can propose blueprints, and that blueprint doesn't seem to be associated with an active Ubuntu developer (as determined by MOTU, core-dev, or ubuntu-universe-contributors status).  He could certainly go to UDS and suggest to have a session discussing the merits, though.

I don't have a firm grasp of the benefits/risks of EXT4, but I'm not sure that it's the best idea to go from "it's now declared stable" to "let's make it default".  It'll already receive much wider testing by being available in Fedora 10 and (presumably) Jaunty.  Give it a release or two for this wide testing (with self-selecting clueful users) to catch some of the really obscure corner cases that are undoubtedly hiding away in there.  Then set it as the default the people who don't know or care what their filesystem is get.

To give you a rough idea. I have used ext4 on all my machines for a year and I have only ever been bitten by one bug. [This one](https://bugzilla.redhat.com/show_bug.cgi?id=468437), it was non destructive not to mention fixed really quickly.

---

### Post by SunnyRabbiera on 2008-11-19
I hope ext4 is at least an option but should not be forced

---

### Post by kestal on 2008-11-19
I think ext4 will be great :) by default, on my end.

---

### Post by jnw222 on 2008-11-19
not super stable for server, but interesting for the desktop users who want to use it.

needs to be added as an option, even if only available in an expert mode

---

### Post by Gina on 2008-11-20
I would by willing to test ext4 if/when it's available for testing in Ubuntu as an option.  I have several PCs and not unduly worried if a test one goes belly-up - I'll just reformat and reinstall.

Obviously it should be optional, as is ext3 etc.

---

### Post by michaeldadmum on 2008-11-23
I think it should be an option when the user space tools (mkfs.ext4, fsck.ext4, grub2, etc.) are ready. I am already running grub2 and I will upgrade my / filesystem to ext4 first, then my /home filesystem after linux 2.6.28 is out.

---

### Post by ShirishAg75 on 2008-11-23
> **michaeldadmum said:**
> I think it should be an option when the user space tools (mkfs.ext4, fsck.ext4, grub2, etc.) are ready. I am already running grub2 and I will upgrade my / filesystem to ext4 first, then my /home filesystem after linux 2.6.28 is out.

I hope for the same, although I do hope there is a downloadable alternate ISO which has everything so even that can be tested.

---

### Post by autocrosser on 2008-11-23
Very good idea---I too will start running EXT4 as soon as the tools are all available for it.....

> **ShirishAg75 said:**
> I hope for the same, although I do hope there is a downloadable alternate ISO which has everything so even that can be tested.

---

### Post by k64 on 2008-11-23
I Have Been Googling Ext4 And Found Benchmarks. They Said That There Is Hardly Any Risk Of Data Loss

---

### Post by plun on 2008-11-23
> **autocrosser said:**
> Very good idea---I too will start running EXT4 as soon as the tools are all available for it.....

Well... I am running one partition as Ext4...:)  e2fsprogs is OK.

but Ubuntu..... 

>   **For people who are running Ubuntu**

For people who are running Ubuntu, it is *highly* recommended that you download a set of modified util-linux packages and install them. Packages for Ubuntu Hardy are available here. These packages revert a change made by Ubuntu to use the volid library instead of the blkid library. The volid library has a number of shortcomings, including that they don't work on freshly created filesystems or swap devices until after you reboot (since it is tied to udev probing) and the volid library doesn't understand ext4dev filesystems. The blkid library is much better, and Debian uses the blkid library for util-linux. Unfortunately, **Ubuntu chose to make this reason for some unknown reason**. For other versions of Ubuntu, the patch that was applied can be found here.

[http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)

 


**Changelog for util-linux**  :confused::confused::confused:

> * New Debian version: remaining ubuntu changes:
    - use libvolume-id instead of libblkid
    - udev hooks

[http://changelogs.ubuntu.com/changelogs/pool/main/u/util-linux/util-linux_2.14-1ubuntu2/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/u/util-linux/util-linux_2.14-1ubuntu2/changelog)




Inverted logic....:confused:    I hope a developer sets up a blueprint soon.  :)

---

### Post by autocrosser on 2008-11-23
Thanks plun---good info!!

I might reformat my storage drive to take a look at it--depends how much time I have to devote to that in the next couple of days....may wait til next weekend--have a 4 day coming up:guitar:

---

### Post by Slug71 on 2008-11-23
Yes, thanks plun.

I might wait till K2.6.28 becomes available so i can do a fresh install on Ext4.

---

### Post by plun on 2008-11-23
> **autocrosser said:**
> Thanks plun---good info!!

I might reformat my storage drive to take a look at it--depends how much time I have to devote to that in the next couple of days....may wait til next weekend--have a 4 day coming up:guitar:

Well... I am just a freak and a real developer must clarify this. :)

I don't believe someone without knowledge writes that stuff
within a upstream wiki...

Looks strange...:confused: also if Debian uses another solution...

EDIT drag the URL with me...[http://ext4.wiki.kernel.org/index.php/Main_Page](http://ext4.wiki.kernel.org/index.php/Main_Page)

---

### Post by decard_pain on 2008-11-23
i took a look in launchpad and the devs seem to be well aware of this problem(although the bug report is marked undecided and is 7 months old)
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311)

basically it seems as there may or may not be a merge of filesystem detection libraries upstream.

theres not much info there really.

---

### Post by k64 on 2008-11-23
[This Link Proves Ext4's Final Release]("http://www.linuxinsight.com/first_benchmarks_of_the_ext4_file_system.html")

---

### Post by samjh on 2008-11-23
> **k64 said:**
> [This Link Proves Ext4's Final Release]("http://www.linuxinsight.com/first_benchmarks_of_the_ext4_file_system.html")

Huh?  That's a really old article - dated 2006!

---

### Post by MacUntu on 2008-11-23
> **k64 said:**
> [This Link Proves Ext4's Final Release]("http://www.linuxinsight.com/first_benchmarks_of_the_ext4_file_system.html")

Back from the past?

*Submitted by admin on Sat, 2006-10-21 18:07*

---

### Post by autocrosser on 2008-11-23
I included my comment there & I think that several of us should also include comments. I will post to the developers-list & let's see if we can get this to at least be talked about at the Developers Summit.

> **decard_pain said:**
> i took a look in launchpad and the devs seem to be well aware of this problem(although the bug report is marked undecided and is 7 months old)
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311)
 /snip/  

---

### Post by plun on 2008-11-23
> **decard_pain said:**
> 
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311)

basically it seems as there may or may not be a merge of filesystem detection libraries upstream.

theres not much info there really.

Thanks for the bug URL... but this is really terrible when you also sees who reported it.  :-k

Sleepy Ubuntu...

---

### Post by decard_pain on 2008-11-23
slightly off topic but did any one notice that btrfs(with dev tag) may be in kernel 2.6.29.so we may see that working right by end of next year

---

### Post by autocrosser on 2008-11-23
Yes, very troubling---I have sent a note to the developer-list about this topic & Plymouth--we shall see if that brings any movement......If anyone feels that writing to the dev-list can further the case...I would recommend it.

My note is as follows:

Thoughts about EXT4 optional in Jaunty Development & questions about Plymouth

I am active at ubuntuforums in the testing/development support area &  there has been a fair amount of talk in the following thread:   [http://ubuntuforums.org/showthread.php?t=965879](http://ubuntuforums.org/showthread.php?t=965879) 

As EXT4 has just been termed "stable", is there a possibility that it  can be included as optional ?  A use request/bugreport is filed at:  [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311) 

A fair amount of testing users (myself included) are ready to include  EXT4 in their systems for testing use & I would think that this would be  a ideal time in the cycle to testdrive the filesystem that I believe  will be the standard within the next year or so. 

On another topic: 

There has been talk in the testing group about Plymouth & possible  replacement of Usplash...IMO Plymouth provides a better user experience  due to a "more" seamless blending of Grub, Kernel boot & GDM. I realize  that there could be "issues" with this, but it could also net a more  positive user experience . 

Please look at:  [http://ubuntuforums.org/showthread.php?t=965338&highlight=plymouth](http://ubuntuforums.org/showthread.php?t=965338&highlight=plymouth) &   [http://ubuntuforums.org/showthread.php?t=985734&highlight=plymouth](http://ubuntuforums.org/showthread.php?t=985734&highlight=plymouth) 

Thank you for your time. 
Dean Loros 
ubuntuforums--autocrosser 


> **plun said:**
> Thanks for the bug URL... but this is really terrible when you also sees who reported it.  :-k  Sleepy Ubuntu...

---

### Post by k64 on 2008-11-23
Sorry for the inconvenience-- I Actually Googled The Link, whether It Was Old Or Not! Here Is A Different Link: [http://kerneltrap.org/Linux/ext4_2.6.24_Merge_Plans]("http://http://kerneltrap.org/Linux/ext4_2.6.24_Merge_Plans")

---

### Post by plun on 2008-11-24
> **autocrosser said:**
> 
A fair amount of testing users (myself included) are ready to include  EXT4 in their systems for testing use & I would think that this would be  a ideal time in the cycle to testdrive the filesystem that I believe  will be the standard within the next year or so. 



Thanks for this !

Useless knowledge maybe...

Upstream version is 2.14-RC3
[http://www.kernel.org/pub/linux/utils/util-linux-ng/v2.14/](http://www.kernel.org/pub/linux/utils/util-linux-ng/v2.14/)

Changelog
[http://www.kernel.org/pub/linux/utils/util-linux-ng/v2.14/v2.14-rc3-ChangeLog](http://www.kernel.org/pub/linux/utils/util-linux-ng/v2.14/v2.14-rc3-ChangeLog)


Debian 2.14-RC2 within experimental and 2.13 for Sid

[http://packages.debian.org/experimental/util-linux](http://packages.debian.org/experimental/util-linux)

Changelog:
[http://packages.debian.org/changelogs/pool/main/u/util-linux/util-linux_2.14~rc2-0/changelog](http://packages.debian.org/changelogs/pool/main/u/util-linux/util-linux_2.14~rc2-0/changelog)


This file IS system critical and I hope that someone have time
to look at this as soon as possible.  The kernel should also be a 2.6.28 one for best testing. IMHO


EDIT   2.14.1 is released
[http://www.kernel.org/pub/linux/utils/util-linux-ng/v2.14/v2.14.1-ReleaseNotes](http://www.kernel.org/pub/linux/utils/util-linux-ng/v2.14/v2.14.1-ReleaseNotes)

.

---

### Post by autocrosser on 2008-11-24
Thank you for adding to the bug plun!!  If anyone else has constructive comments to add to the bugreport (gnomeuser!!!)--now would be a good time......

My note has hit the dev-list & I expect to see some comments on it today--if anyone wants to chime in there--- [email]ubuntu-devel-discuss@lists.ubuntu.com[/email]
& add something positive to the conversation......

---

### Post by plun on 2008-12-05
Phoronix testing Ext4.....;)

[http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1](http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1)

**9 pages  !!!**

Conclusion:

> EXT4 is **clearly a significant improvement** over EXT3 when it came to the pure disk benchmarks, however, **in the real world**, saying better performance should not be used as a reason to replace your existing EXT3 or XFS partitions. In our tests that cater towards Linux desktop users and gamers, EXT4 hadn't delivered a sizable quantitative advantage. That's not to say though it's not worth switching to EXT4. EXT4 is more scalable, more efficient through the use of Extents, supports larger disk capacities, can handle twice the number of sub-directories, is capable of handling online defragmentation, and there is improved reliability via journal checksums. What perhaps is more important is that with the addition of these new features, the performance hasn't regressed. Also, when testing the EXT4 file-system, we hadn't run into any problems with stability, file corruption, or any other issues.

EXT4 is declared stable in the soon to be released Linux 2.6.28 kernel, but from there it isn't clear how big of a role EXT4 will play within the Linux ecosystem. **Chances are we would see it be adopted officially by Fedora or another bleeding-edge distribution before it's used by default within Ubuntu or a commercially supported distribution**. The development timeline for btrfs places a 1.0 release in Q4'08, but it doesn't look we'll see a stable release of that until next year. Depending upon how fast that file-system is hardened and what adoption rates it sees, it may largely influence how EXT4 fairs as a temporary alternative.


Still testing with one partition and a self-brewed kernel, also built it with 1000Hz and everything is "snappy"....:D

---

### Post by druellan on 2008-12-06
After reading Phoronix test run I'm convinced that EXT4 is called to be the default filesystem on any distro that takes seriously performance and speed.

Speaking of Ubuntu and since ext4 still on vias to be stable on Kernel 2.6.28, adding it as an option now seems risky and a waste of resources. There are plenty of things to improve on Ubuntu, specially on video performance and detection. But once the fs get tested no doubt is amust and should be the default fs for the distro.

---

### Post by Slug71 on 2008-12-22
Anyone know when we can expect to see the Ext4 option in the installer?

---

### Post by Starks on 2008-12-22
I'd still like to see ReiserFS and Reiser4 as options. </sarcasm>

:3

---

### Post by MacUntu on 2008-12-26
Just something about file defragmentation with ext3:

- 15gb ext3 partition formatted for Intrepid
- no heavy use
- 38% free space
- created 10 80MB files

That's how they are spread over the partition [from the smallest block to the largest they use, each file a color]:

[img]http://img.xrmb2.net/images/582328.png[/img]

I'm glad ext4 will have online-defragmentation and I'll try to repeat that "test" when I'll jump to Jaunty dev. :)

---

### Post by Archmage on 2008-12-26
Since the Kernel 2.6.28 ext4 is now official stable, therefore I'm really waiting impatiently to start testing it.

Could someone please inform us when we can use it? I would download the latest daily build as soon as I hear that it is there.

---

### Post by Gina on 2008-12-26
Same here.

---

### Post by int on 2008-12-26
**[ubuntu/jaunty] linux 2.6.28-4.5 (Accepted)** (2 hours ago)
> linux (2.6.28-4.5) jaunty; urgency=low

 [ Andy Whitcroft ]

 * clean up module dependancy information on package removal/purge
   - LP: #300773

 [ Tim Gardner ]

 * Update iscsitarget to 0.4.17
** * Build in ext{234}**
 * Build in Crypto modules AES, CBC, ECB
 * Build in ACPI AC,BATTERY,BUTTON,FAN,PCI_SLOT,PROCESSOR,SBS,THERMAL,WMI
 * Build in AGP intel,via,sis,ali,amd,amd64,efficeon,nvidia,sworks
 * Build in ata,dev_dm,dev_loop,dev_md,dev_sd,dev_sr
 * Build in BT l2cap,rfcomm,sco
 * Reduce CONFIG_LEGACY_PTY_COUNT to 0
 * Build in CDROM_PKTCDVD and CHR_DEV_SG
 * Build in CPU_FREQ
   GOV_CONSERVATIVE,GOV_ONDEMAND,GOV_POWERSAVE,GOV_USERSPACE,STAT,TABLE
 * Build in DM CRYPT,MIRROR,MULTIPATH,SNAPSHOT
 * Build in DRM
 * Build in HID
 * Build in HOTPLUG PCI,PCIE
 * Build in I2C
 * Build in IEEE1394 OHCI1394
 * Build in INPUT EVDEV
 * Build in IPV6
 * Build in MMC
 * Build in PACKET
 * Enable both IEEE1394 (Firewire) stacks as modules
   - LP: #276463
 * Disable SUNRPC_REGISTER_V4
   - LP: #306016
 * Enable dm-raid4-5
   - LP: #309378
 * Build in PPP
 * Build in RFKILL
 * Build in USB SERIAL

 [ Upstream Kernel Changes ]

 * Rebased to v2.6.28

---

### Post by RAOF on 2008-12-26
ext4 has been usable for some time in Jaunty; at least since the first kernel based on 2.6.28 has been in.

---

### Post by plun on 2008-12-27
> **RAOF said:**
> ext4 has been usable for some time in Jaunty; at least since the first kernel based on 2.6.28 has been in.

Yup... my test partition just works.

But this "heavy" bug is still untouched...

[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311)

So please "touch" it !

---

### Post by int on 2008-12-27
**== To test is needed ==**
* Kernel 2.6.28 [COLOR="SeaGreen"]**DONE**[/COLOR]
* ubuntu-installer that support ext4 [COLOR="Red"]**NOT STARTED**[/COLOR]
* e2fsprogs version 1.41.0 or higher is required [COLOR="SeaGreen"]**DONE**[/COLOR]

**== To enable to /boot/ on the same partition. ==**
* grub2 as default bootloader [COLOR="Orange"]**NOT AS DEFAULT**[/COLOR]

**== Tools  ==**
* The next release of GParted (0.4.2). [COLOR="Red"]**NOT RELEASED**[/COLOR]

---

### Post by Gina on 2008-12-27
Looks like there could be a bit of a delay!

---

### Post by vishalrao on 2008-12-27
> **plun said:**
> Yup... my test partition just works.

But this "heavy" bug is still untouched...

[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311)

So please "touch" it !

I just looked at Ted Tso's patch in the first comment, made me laugh... something ain't right

---

### Post by plun on 2008-12-27
> **vishalrao said:**
> I just looked at Ted Tso's patch in the first comment, made me laugh... something ain't right

Well... I am not a developer but Theodore has my 100% respect.. without limitation. One of the real "heavy open source champions".

The patch is also probably against the situation in March...


[http://en.wikipedia.org/wiki/Theodore_Ts%27o](http://en.wikipedia.org/wiki/Theodore_Ts%27o)

:)

---

### Post by ShirishAg75 on 2008-12-27
I made a tracking bug [lpbug]293465[/lpbug] for the same.

I am looking forward when the other pieces get done as well. GRUB 2 is there but not as default :(

e2fsprogs is 1.41.3 released by upstream 

[http://e2fsprogs.sourceforge.net/](http://e2fsprogs.sourceforge.net/)

[http://e2fsprogs.sourceforge.net/e2fsprogs-release.html#1.41.3](http://e2fsprogs.sourceforge.net/e2fsprogs-release.html#1.41.3)

1.41.0 is was released in July 2008. 
[B]
[/B]

---

### Post by vishalrao on 2008-12-27
I know who Ted Tso is that's why I found the patch funny (unless I'm not reading it right) :D

---

### Post by plun on 2008-12-27
> **vishalrao said:**
> I know who Ted Tso is that's why I found the patch funny (unless I'm not reading it right) :D

Ok... with Jaunty it nevertheless works  (without patch) ...:)   I cannot judge about the patch.

My first "Bambi" steps with EXT4.

[http://ubuntuforums.org/showpost.php?p=6104260&postcount=59](http://ubuntuforums.org/showpost.php?p=6104260&postcount=59)

Also to add it to fstab.....

Nevertheless this must be clarified, IMHO !

---

### Post by plun on 2008-12-27
> **ShirishAg75 said:**
> I made a tracking bug [lpbug]293465[/lpbug] for the same.

I am looking forward when the other pieces get done as well. GRUB 2 is there but not as default :(

e2fsprogs is 1.41.3 released by upstream 

[http://e2fsprogs.sourceforge.net/](http://e2fsprogs.sourceforge.net/)

[http://e2fsprogs.sourceforge.net/e2fsprogs-release.html#1.41.3](http://e2fsprogs.sourceforge.net/e2fsprogs-release.html#1.41.3)

1.41.0 is was released in July 2008. 
[B]
[/B]

Ok and thanks...

I cannot understand why any devs doesn't write anything....:confused:

(Grub2 is somthing I let others test first....:) )

EDIT
Scott James Remnants comment..... ?????????????

---

### Post by Gina on 2008-12-27
I'm quite happy to test grub2 - I have a machine dedicated to testing :) In fact if it will work on an old heap, I have two :lolflag:

---

### Post by plun on 2008-12-27
> **Gina said:**
> I'm quite happy to test grub2 - I have a machine dedicated to testing :) In fact if it will work on an old heap, I have two :lolflag:

Well... start with just EXt4, I blowed away a NTFS partion somehow...

I haven't checked Debian for bugs but it was a "full house" a month ago (GRUB2).

---

### Post by castrojo on 2008-12-27
> **plun said:**
> Ok and thanks...
I cannot understand why any devs doesn't write anything....:confused:


You can start by setting the bug to Confirmed.

---

### Post by Gina on 2008-12-27
@plun.... Have you tried testdisk to recover your lost partition?  Worked for me after a Windoze app messed up following resizing my XP system partition.  That was a few years ago now.  I have also recovered a corrupted PT after a dev fiasco - and my lost partitions.

---

### Post by plun on 2008-12-27
> **whiprush said:**
> You can start by setting the bug to Confirmed.

Well... Mr Remnant is a core developer...:lolflag:

---

### Post by autocrosser on 2008-12-27
OK---it's set to Confirmed....Let's just get it changed to blkid so we can just get on with testing EXT4.

---

### Post by Slug71 on 2008-12-27
> **autocrosser said:**
> OK---it's set to Confirmed....Let's just get it changed to blkid so we can just get on with testing EXT4.


Yes please!

---

### Post by Archmage on 2009-01-08
Please ignore/delete.

---

### Post by castrojo on 2009-01-08
[http://brainstorm.ubuntu.com/idea/16854/](http://brainstorm.ubuntu.com/idea/16854/)

Update on ext4 in the installer.

---

### Post by cjwatson on 2009-01-08
Tomorrow's daily builds of Jaunty will include ext4 as a partitioning option. As far as I can tell, it installs and boots fine (including full ext4 /; you don't need a separate /boot). I haven't tested resizing yet although I did add some code which ought to support it to the same degree as ext3, using resize2fs.

Please file bugs if you encounter problems!

---

### Post by Slug71 on 2009-01-08
Excellent News!! Thanks Devs! :D:D

---

### Post by autocrosser on 2009-01-08
Thank you Colin!!!  Any idea on gparted being "brought up to speed?"

---

### Post by ShirishAg75 on 2009-01-08
libparted 8.10 which is parted does have ext4 support. Dunno if something is needed to be changed in gparted or not.

---

### Post by mariuz on 2009-01-09
downloaded the daily build and now i install jounty on an fresh ext4 partition 

let's see if it boots 

ps:i wish it was enabled by default

---

### Post by plun on 2009-01-09
Ubiquity crashes for me when I tries to edit a partition...

i386, todays build.

gparted is outdated and cannot be used.

---

### Post by ShirishAg75 on 2009-01-09
plun, 
 file a bug and give detailed steps how you produced the crash. Please give a link of the bug on the forum as well.

---

### Post by plun on 2009-01-09
> **ShirishAg75 said:**
> plun, 
 file a bug and give detailed steps how you produced the crash. Please give a link of the bug on the forum as well.

Yes... I knows that, but my PC is crazy.  Managed to get 
a kerneloops bug report but Launchpad was also broken.


"The freezing thread" is also frozen...:D   Impossible to write new messages.:confused:

Maybe someone else can confirm and file a bug.

Ubiquity will otherwise be CD tested for Alpha3 so its not a big deal.  Broken is broken...

---

### Post by cjwatson on 2009-01-09
[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/137872](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/137872), which I've targeted for Jaunty. I haven't got as far as looking at the parted frontends yet though.

---

### Post by cjwatson on 2009-01-09
Evan Dandrea committed this fix yesterday evening (not uploaded yet):

  * Fix the edit partition dialog by properly preseeding
    partman/active_partition.

I guess that probably corresponds to the bug you encountered.

---

### Post by plun on 2009-01-09
Thanks Colin...  much appreciated..:D  Just great !

---

### Post by ShirishAg75 on 2009-01-09
Thank you for the info. cjwatson. Looking forward for the fix/next upload. 

Looking at the latest gparted on sourceforge though they are using an old kernel release.

> 


                                                         **File Release Notes and Changelog**

     
**Release Name: [0.4.1-2]("http://sourceforge.net/project/showfiles.php?group_id=115843")**

  
**Notes:**
The release notes for GParted Live 0.4.1-2:
  - New upstream GParted 0.4.1.
  - Based on Debian Lenny repository on Dec/28/2008 with linux kernel 2.6.26-12.
[http://sourceforge.net/project/shownotes.php?release_id=649904&group_id=115843](http://sourceforge.net/project/shownotes.php?release_id=649904&group_id=115843)

Dunno if we will get gparted 0.4.2 which has ext4 in this cycle.

---

### Post by cjwatson on 2009-01-09
I think that just means that that's what the gparted maintainer was testing with. gparted certainly doesn't have bits of the kernel built into it or anything (wouldn't that be a hideous layering violation!), so it's not really important that he was testing with an older kernel version.

---

### Post by cjwatson on 2009-01-09
Oh, disregard my last post, you were talking about the gparted live CD which of course does have a kernel built in.

I don't know anything about the gparted release schedule. The changes for ext4 are not entirely trivial but not all that complicated either, so they're potentially backportable in case 0.4.2 doesn't arrive in time.

---

### Post by Gina on 2009-01-09
Very interesting :) I'm hoping I can find the time to install an ext4 Jaunty at the weekend - looks like there should be a good chance of it working :) Thank you Colin (and others) for all your work on this :):)

---

### Post by Slug71 on 2009-01-09
Yep, thanks to you Devs who made this possible.

---

### Post by Gourgi on 2009-01-09
whoohoooo :popcorn:
ext4 filesystem and an encrypted home dir are going to rock !! 


> **Slug71 said:**
> Yep, thanks to you Devs who made this possible.

+1

---

### Post by Slug71 on 2009-01-09
Let the wait for BTRFS begin. :)

---

### Post by plun on 2009-01-09
> **Slug71 said:**
> Let the wait for BTRFS begin. :)

Evolution is stepwise.

Linus is at GIT12 for the moment....  RC1 soon...:-D

Maybe we are "cannibals"..... :tongue:

---

### Post by autocrosser on 2009-01-09
> **Slug71 said:**
> Let the wait for BTRFS begin. :)

The next shiny thing!!!! :D:D

I'm converting my system  (both testing installs) this weekend & planning on a reinstall at the next release.......

Hey plun--do we "really" eat each other?????

---

### Post by plun on 2009-01-09
> **autocrosser said:**
> 
Hey plun--do we "really" eat each other?????

No but maybe we tries to eat developers...:D

Just wants more and more and more...

---

### Post by ShirishAg75 on 2009-01-09
bits of btrfs are slated for 2.6.29 release but the filesystem is supposed to take a year or more . 

I saw the gparted trunk, most probably the devs will sync from the GNOME SVN.

Didn't know that the gparted guys had moved to GNOME (atleast for coding)

[http://svn.gnome.org/viewvc/gparted/](http://svn.gnome.org/viewvc/gparted/)

i say this because I used gparted first time when it was a baby (0.1) from then it has come a long long way.

---

### Post by LordVeovis on 2009-01-09
Does anyone have a status update for BTRFS?  I am really looking forward to this but their site has not had really any useful information added to it in a while.  (at least not that I can find)

---

### Post by int on 2009-01-09
less off topic please, this thread is only about ext4 in jaunty.

---

### Post by Eclipse. on 2009-01-09
This place seeks to amaze me, ext4 only got on the daily builds today and now we are right on to btrfs.;)

EDIT: ^^ Party-pooper :p

---

### Post by Slug71 on 2009-01-09
~$ blkid
/dev/sda1: UUID="A22AA8492AA81BF3" LABEL="ACER" TYPE="ntfs" 
/dev/sda5: UUID="9672-D88B" TYPE="vfat" 
/dev/sda6: UUID="4f75e46e-f041-488a-a51c-3c665f4b560c" TYPE="ext4" 
/dev/sda7: UUID="3e406a1b-913c-4f44-8960-091534ddd7b1" TYPE="swap" 
/dev/sda8: UUID="5873fe57-2ee8-41a7-af44-2069b78b676b" TYPE="ext4"

---

### Post by Slug71 on 2009-01-09
> **Eclipse. said:**
> This place seeks to amaze me, ext4 only got on the daily builds today and now we are right on to btrfs.;)

EDIT: ^^ Party-pooper :p

:lolflag:


Best leave discussion for BTRFS for KK 9.10

---

### Post by ssam on 2009-01-09
> **LordVeovis said:**
> Does anyone have a status update for BTRFS?  I am really looking forward to this but their site has not had really any useful information added to it in a while.  (at least not that I can find)

[http://lwn.net/Articles/313682/](http://lwn.net/Articles/313682/)
(LWN is subscriber only for a week. its worth the subs fee though. i can PM anyone a free link if they want to read it (PM me))

---

### Post by gnomeuser on 2009-01-09
> **Eclipse. said:**
> This place seeks to amaze me, ext4 only got on the daily builds today and now we are right on to btrfs.;)

EDIT: ^^ Party-pooper :p

what do you mean already, I have been lusting it for months (posted Oct. 18th - my sisters birthday incidently)

[http://brainstorm.ubuntu.com/idea/14527/](http://brainstorm.ubuntu.com/idea/14527/)

---

### Post by MacUntu on 2009-01-10
> **Gourgi said:**
> 
ext4 filesystem and an encrypted home dir are going to rock !! 


Just installed this config via the current alternate CD - works fine (dual boot with Vista SP2...uhm Windows 7 Beta).

---

### Post by Slug71 on 2009-01-10
> **MacUntu said:**
> Just installed this config via the current alternate CD - works fine (dual boot with Vista SP2...uhm Windows 7 Beta).


Yep, works well. :)

---

### Post by MacUntu on 2009-01-10
Next task: Encrypting the swap partition, but that's a different kettle of fish. :)

---

### Post by plun on 2009-01-10
> **MacUntu said:**
> Just installed this config via the current alternate CD - works fine (dual boot with Vista SP2...uhm Windows 7 Beta).

Well, I took the normal Cd and its still broken....

Back to Windows 7....:redface:

---

### Post by Slug71 on 2009-01-10
> **plun said:**
> Well, I took the normal Cd and its still broken....

Back to Windows 7....:redface:

Get AMD64

---

### Post by autocrosser on 2009-01-10
Well, I converted my testing installs over last night---and did not leave myself a easy way out......To make a long story short, my boot partition didn't like what I did & thumbed it's nose at me........6 hours later & replacing a drive with a spare that just happened to have a much older bootable version of Jaunty on it---I'm now running Jaunty totally in EXT4. :)

Just glad that I thought to keep that drive I changed out a month ago.........:P:P:P

Got to love being on the "bleeding" edge..........

---

### Post by Slug71 on 2009-01-10
> **autocrosser said:**
> Well, I converted my testing installs over last night---and did not leave myself a easy way out......To make a long story short, my boot partition didn't like what I did & thumbed it's nose at me........6 hours later & replacing a drive with a spare that just happened to have a much older bootable version of Jaunty on it---I'm now running Jaunty totally in EXT4. :)

Just glad that I thought to keep that drive I changed out a month ago.........:P:P:P

Got to love being on the "bleeding" edge..........

:lolflag: At least you won in the end. :guitar:

---

### Post by Slug71 on 2009-01-10
I'm contemplating installing Grub2 to see how it likes Ext4.

---

### Post by zolookas on 2009-01-10
If someone is interested: There was suse's [summer of code project to implement ext4 support in grub1]("http://code.google.com/soc/2008/suse/appinfo.html?csaid=91DC4C762E7EE6D7") and it appears that there is a patch for grub to support ext4 here: [http://code.google.com/p/grub4ext4/](http://code.google.com/p/grub4ext4/) (source and compiled .rpm's)

---

### Post by Slug71 on 2009-01-10
> **zolookas said:**
> If someone is interested: There was suse's [summer of code project to implement ext4 support in grub1]("http://code.google.com/soc/2008/suse/appinfo.html?csaid=91DC4C762E7EE6D7") and it appears that there is a patch for grub to support ext4 here: [http://code.google.com/p/grub4ext4/](http://code.google.com/p/grub4ext4/) (source and compiled .rpm's)

Its already in Jaunty.

---

### Post by Etheric Seed on 2009-01-10
"Tomorrow's daily builds of Jaunty will include ext4 as a partitioning option. As far as I can tell, it installs and boots fine (including full ext4 /; you don't need a separate /boot)"

First ever post to a Linux forum so forgive me if I do something incorrectly or should be posting this elsewhere.

I installed Jaunty with this build.  I used ext4 exclusively but did seperate /boot, /,/home,/usr,/var, et. al. into seperate partitions.

I made /boot bootable and left the rest with the standard default.

I gave /boot 500mb of space and the rest all received 40 GB except /home (which I allocated 100GB) and /data which I allocated the rest I believe. My swap is 6-12GB. /tmp wasn't allocated 40GB but was quite generous with it as well.  I thought most of that would be overkill for space. Don't quote me on the /data as I do want to install other linux distros and may have left some of the remaining space unallocated.


Everything installed great. Unfortunately when I tried to login in, I keep getting incorrect user name and password.  I know what I set as username and the password had to be typed twice to make certain there are no errors. So either I made matching typos twice or I errored in some other manner. 

As a wild guess I wondered if it had anything to do with the way I set my partitions.  I did read at first that when using ext4 one had to use a seperate ext3 /boot partion in order to boot. But when I read the quote above, I partially went with it and made the seperate /boot partion but with ext4. Maybe I errored here and either should have made the /boot ext3 or not made a seperate partion for it?  Grub is 1.5. Seems I read somewhere that Grub 2 was necessary for boot with ext4? 

I am semi new to linux obviously. :D 

Still, I put together a cheap system for testing purposes. Thought I would try Jaunty.  The testing system is an amd 64 x2 5000+ processor, asus m2n-mx se plus motherboard, 4GB corsair 800mhz memory, (2) 1 TB Hitachi sata HDs. Second HD entirely ext4 with /data as mount point. 

If I did happen to make the typo errors for user name and password during install, is there any way to find out without blowing it up and reinstalling? If it is something else I errored at that is obvious to you pros, any help  would be appreciated. Thanks.

Oh, I don't know what or if this has to do with anything but on boot I received a 8324 error. Don't quote me on the number but it had to do with apic/apci.  I disabled it in Bios instead of putting noapic(sp) in boot up with grub. No more error. Could not use the wireless keyboard to install Jaunty as it would lock up at start of install. Still received the error message with standard keyboard but it did install. I disabled in Bios after install. Again, don't know if it has anything to do with my issue or not, but thought I'd mention the only error I did receive.

---

### Post by autocrosser on 2009-01-10
> **Slug71 said:**
> I'm contemplating installing Grub2 to see how it likes Ext4.

When you see if it will work/not---post about it--after the problem I just had with the "patched" Grub1---I'd really be inclined to try Grub2--been wanting to for quite a while now.....and Grub1 really was a pain in the A** this morning..........:mad::mad::mad:

---

### Post by Slug71 on 2009-01-10
> **Etheric Seed said:**
> "Tomorrow's daily builds of Jaunty will include ext4 as a partitioning option. As far as I can tell, it installs and boots fine (including full ext4 /; you don't need a separate /boot)"

First ever post to a Linux forum so forgive me if I do something incorrectly or should be posting this elsewhere.

I installed Jaunty with this build.  I used ext4 exclusively but did seperate /boot, /,/home,/usr,/var, et. al. into seperate partitions.

I made /boot bootable and left the rest with the standard default.

I gave /boot 500mb of space and the rest all received 40 GB except /home (which I allocated 100GB) and /data which I allocated the rest I believe. My swap is 6-12GB. /tmp wasn't allocated 40GB but was quite generous with it as well.  I thought most of that would be overkill for space. Don't quote me on the /data as I do want to install other linux distros and may have left some of the remaining space unallocated.


Everything installed great. Unfortunately when I tried to login in, I keep getting incorrect user name and password.  I know what I set as username and the password had to be typed twice to make certain there are no errors. So either I made matching typos twice or I errored in some other manner. 

As a wild guess I wondered if it had anything to do with the way I set my partitions.  I did read at first that when using ext4 one had to use a seperate ext3 /boot partion in order to boot. But when I read the quote above, I partially went with it and made the seperate /boot partion but with ext4. Maybe I errored here and either should have made the /boot ext3 or not made a seperate partion for it?  Grub is 1.5. Seems I read somewhere that Grub 2 was necessary for boot with ext4? 

I am semi new to linux obviously. :D 

Still, I put together a cheap system for testing purposes. Thought I would try Jaunty.  The testing system is an amd 64 x2 5000+ processor, asus m2n-mx se plus motherboard, 4GB corsair 800mhz memory, (2) 1 TB Hitachi sata HDs. Second HD entirely ext4 with /data as mount point. 

If I did happen to make the typo errors for user name and password during install, is there any way to find out without blowing it up and reinstalling? If it is something else I errored at that is obvious to you pros, any help  would be appreciated. Thanks.

Oh, I don't know what or if this has to do with anything but on boot I received a 8324 error. Don't quote me on the number but it had to do with apic/apci.  I disabled it in Bios instead of putting noapic(sp) in boot up with grub. No more error. Could not use the wireless keyboard to install Jaunty as it would lock up at start of install. Still received the error message with standard keyboard but it did install. I disabled in Bios after install. Again, don't know if it has anything to do with my issue or not, but thought I'd mention the only error I did receive.

Why so many partitions??

Just need
Use Ext4 and mount as /(root) 40GB   More than enough
Swap                           2GB,   6-12 is WAY Overkill!! 
Use Ext4 and mount as /home.  50GB   More than enough

I'd maybe make a Fat32 partition too and mount as Windows which would be a shared partition and give it like 100GB. Linux can read and write to Fat32 partitions so if you have any more OSs on there they can all share that. Good for keeping files on there you may need in another OS. 

Grub 1.5 is fine


Sweet test system though!

---

### Post by Slug71 on 2009-01-10
> **autocrosser said:**
> When you see if it will work/not---post about it--after the problem I just had with the "patched" Grub1---I'd really be inclined to try Grub2--been wanting to for quite a while now.....and Grub1 really was a pain in the A** this morning..........:mad::mad::mad:

Will do. :)

---

### Post by autocrosser on 2009-01-10
> **Etheric Seed said:**
> "Tomorrow's daily builds of Jaunty will include ext4 as a partitioning option. As far as I can tell, it installs and boots fine (including full ext4 /; you don't need a separate /boot)"

First ever post to a Linux forum so forgive me if I do something incorrectly or should be posting this elsewhere.

I installed Jaunty with this build.  I used ext4 exclusively but did seperate /boot, /,/home,/usr,/var, et. al. into seperate partitions.

I made /boot bootable and left the rest with the standard default.

I gave /boot 500mb of space and the rest all received 40 GB except /home (which I allocated 100GB) and /data which I allocated the rest I believe. My swap is 6-12GB. /tmp wasn't allocated 40GB but was quite generous with it as well.  I thought most of that would be overkill for space. Don't quote me on the /data as I do want to install other linux distros and may have left some of the remaining space unallocated.


Everything installed great. Unfortunately when I tried to login in, I keep getting incorrect user name and password.  I know what I set as username and the password had to be typed twice to make certain there are no errors. So either I made matching typos twice or I errored in some other manner. 

As a wild guess I wondered if it had anything to do with the way I set my partitions.  I did read at first that when using ext4 one had to use a seperate ext3 /boot partion in order to boot. But when I read the quote above, I partially went with it and made the seperate /boot partion but with ext4. Maybe I errored here and either should have made the /boot ext3 or not made a seperate partion for it?  Grub is 1.5. Seems I read somewhere that Grub 2 was necessary for boot with ext4? 

I am semi new to linux obviously. :D 


If I did happen to make the typo errors for user name and password during install, is there any way to find out without blowing it up and reinstalling? If it is something else I errored at that is obvious to you pros, any help  would be appreciated. Thanks.

Well--You should cruise the forums a bit---normally to test or normal use--setup a / (root) partition & a /home partition--it is not needed or recommended to create all those /usr /lib etc partitions...creates a nightmare to install/admin your system that way.....a seperate /home will allow you to reinstall if/when the testing install "blows" up on you....Got to admire your guts to dive into a early alpha as a noob....I would normally recommend you get some time under your belt with stable installs first....And setting up with EXT4 is really for the advanced users right now.....


And yes, you are in the right place..we'll go easy on you....We don't bite (much....)

---

### Post by plun on 2009-01-10
> **autocrosser said:**
> 

Got to love being on the "bleeding" edge..........

Congrats...:D


Well, I landed within a mess....

The alternate CD cannot be used on a USB stick....:---) 

(bla bla bla looking for a CD...)

Burned it and choosed manual partition and kept 2 of my partitions > OK

Copy error during install...:tongue:

Good night...

---

### Post by autocrosser on 2009-01-10
Hey plun--do you know that .gif "hit any key to continue"?  I quit at about 1:30am last night (felt like I had bloddy stumps for arms:P) & the "fix" for me came about 4:00am--sat bolt upright in bed with the answer....almost ran to my system & slapped my "spare" SATAI with a month-old Jaunty install in it...then booted the current Live & setup grub for the old drive.....It worked......

There is ALWAYS an answer---hang in there!!!!!!


slug---have you checked with bootchart? I did a run earlier & EXT4 shaved about 3 sec off of my boot time...wondering if you see about the same......

---

### Post by plun on 2009-01-10
> **autocrosser said:**
> 
There is ALWAYS an answer---hang in there!!!!!!



Yes for sure...:grin:

I kept my /home and my /media partition so this not a problem.

Just annoying...):P

---

### Post by autocrosser on 2009-01-10
Good show my friend!!! Have a good one & talk to you tomorrow.....

---

### Post by Slug71 on 2009-01-10
> **autocrosser said:**
> 
slug---have you checked with bootchart? I did a run earlier & EXT4 shaved about 3 sec off of my boot time...wondering if you see about the same......

I havent, dont think i actually ever have but it is definitely faster.
I noticed immediately after the install. I think lots of people will be happy about that. :)

---

### Post by Etheric Seed on 2009-01-10
"Why so many partitions??

Just need
Use Ext4 and mount as /(root) 40GB   More than enough
Swap                           2GB   6-12 is WAY Overkill!! 
Use Ext4 and mount as /home.  50GB   More than enough

Grub 1.5 is fine"

:),

If you let system pic for ya it will make swap 12 GB on a 1TB hd. 

I know most say 2GB but I think I made it 6GB.  Still overkill I realize but got plenty of space to work with and figured I could try and change things around in the partion editor once I was in Gnome. 

So many partitions---I had read it is more secure. Not that familiar with Linux security at all. Don't know anything about ipstables, apparmor, SElinux, etc.  Thought I'd give the seperate partions a whirl. I realize I have the space for the seperate partions or the way you mentioned it. I just like to keep things seperate. Also a learning process.

"Well--You should cruise the forums a bit---normally to test or normal use--setup a / (root) partition & a /home partition--it is not needed or recommended to create all those /usr /lib etc partitions...creates a nightmare to install/admin your system that way.....a seperate /home will allow you to reinstall if/when the testing install "blows" up on you....Got to admire your guts to dive into a early alpha as a noob....I would normally recommend you get some time under your belt with stable installs first....And setting up with EXT4 is really for the advanced users right now.....


And yes, you are in the right place..we'll go easy on you....We don't bite (much....)"


I don't mind the nightmare. Gotta learn. ;)  What could I possible learn from point and click? Setting up a /home, swap, /root only seems nearly as simple as it gets. I jump into a lot of things without knowing. Has been how I learn it seems. Heck I read things such as string theory for fun without any advanced mathmatical knowledge beyond algebra and geometry and minor experience with basic physics. lol 
Complexity is the spice of life.

I do use Ubuntu on the computer I am at currently.  Intrepid Ibex. Started out with version right before Hardy. Have played around with a few things. Screwed up a bunch of things it seems from Transmission to Compiz and beyond. Always have been able to correct them on my own. I do cruise the forums as well as other sites with info. I don't expect to be handfed. :)  I just figured that folks were being nicer to noobies these days? :P  A long time ago, I tried linux when much had to be done on ones own due to Linux folks bascially saying....read the MAN. Seemed many either liked to wallow in supposed superiority or thought it was more beneficial to spend hours searching for an answer that could be solved in minutes.  Was aggrevating. I know one learns better when figuring out for oneself but that attitude got old.  

I am not new to a computer nor am I incapable of learning quickly. I have had some networking courses in college at ITT Tech and elsewhere. I also have stayed at a Holiday Inn. :D

Just figured my question was a simple one to get answered without blowing it all up and reinstalling.  But it seems the time I have spent writing and waiting for a response could have been spent reinstalling and I probably could have been mostly done with it by now. Still, if the same situation arose, I'd be right back at square one and searching around reading for hours for something that seems should be simple. 

"we'll go easy on you....We don't bite (much....)"...I'll tell that to my backside when I find it. :D 

So the only help I get is basically blow it up and start over and put most everything on one partion? lmao. This is an advanced user solution?
:P  Just kidding around. :guitar: I'm pushin the hump of midlife. Be gentle on an old hillbilly. ***cue dueling banjos***

---

### Post by Slug71 on 2009-01-10
> **autocrosser said:**
> When you see if it will work/not---post about it--after the problem I just had with the "patched" Grub1---I'd really be inclined to try Grub2--been wanting to for quite a while now.....and Grub1 really was a pain in the A** this morning..........:mad::mad::mad:

Just did the install and will do the reboot after this message.
Everything seems to have gone ok thus far and i noticed that os-prober was a dependency. Wonder if it is because of what plun and i added to bug #312310.

---

### Post by autocrosser on 2009-01-10
Not a problem---I started with UNIX in the early 70's, so I'm not exactly a spring chicken myself....The only reason I recommended the / & /home method is after you install/reinstall multiple times...it gets a bit tiresome to redo all those separate partitions (and a update/reinstall is murder--I've been there before)...and as far as security--well, just a / & /home is several levels above anything Windows can do.

---

### Post by autocrosser on 2009-01-10
> **Slug71 said:**
> Just did the install and will do the reboot after this message.
Everything seems to have gone ok thus far and i noticed that os-prober was a dependency. Wonder if it is because of what plun and i added to bug #312310.

Sounds good---I'll stabilize my system over the next few days & look towards Grub2 this next weekend.......

---

### Post by Slug71 on 2009-01-10
> **Etheric Seed said:**
> "Why so many partitions??

Just need
Use Ext4 and mount as /(root) 40GB   More than enough
Swap                           2GB   6-12 is WAY Overkill!! 
Use Ext4 and mount as /home.  50GB   More than enough

Grub 1.5 is fine"

:),

If you let system pic for ya it will make swap 12 GB on a 1TB hd. 

I know most say 2GB but I think I made it 6GB.  Still overkill I realize but got plenty of space to work with and figured I could try and change things around in the partion editor once I was in Gnome. 

So many partitions---I had read it is more secure. Not that familiar with Linux security at all. Don't know anything about ipstables, apparmor, SElinux, etc.  Thought I'd give the seperate partions a whirl. I realize I have the space for the seperate partions or the way you mentioned it. I just like to keep things seperate. Also a learning process.

"Well--You should cruise the forums a bit---normally to test or normal use--setup a / (root) partition & a /home partition--it is not needed or recommended to create all those /usr /lib etc partitions...creates a nightmare to install/admin your system that way.....a seperate /home will allow you to reinstall if/when the testing install "blows" up on you....Got to admire your guts to dive into a early alpha as a noob....I would normally recommend you get some time under your belt with stable installs first....And setting up with EXT4 is really for the advanced users right now.....


And yes, you are in the right place..we'll go easy on you....We don't bite (much....)"


I don't mind the nightmare. Gotta learn. ;)  What could I possible learn from point and click? Setting up a /home, swap, /root only seems nearly as simple as it gets. I jump into a lot of things without knowing. Has been how I learn it seems. Heck I read things such as string theory for fun without any advanced mathmatical knowledge beyond algebra and geometry and minor experience with basic physics. lol 
Complexity is the spice of life.

I do use Ubuntu on the computer I am at currently.  Intrepid Ibex. Started out with version right before Hardy. Have played around with a few things. Screwed up a bunch of things it seems from Transmission to Compiz and beyond. Always have been able to correct them on my own. I do cruise the forums as well as other sites with info. I don't expect to be handfed.  I just figured that folks were being nicer to noobies these days? :P  A long time ago, I tried linux when much had to be done on ones own due to Linux folks bascially saying....read the MAN. Seemed many either liked to wallow in supposed superiority or thought it was more beneficial to spend hours searching for an answer that could be solved in minutes.  Was aggrevating. I know one learns better when figuring out for oneself but that attitude got old.  

I am not new to a computer nor am I incapable of learning quickly. I have had some networking courses in college at ITT Tech and elsewhere. I also have stayed at a Holiday Inn. :D

Just figured my question was a simple one to get answered without blowing it all up and reinstalling.  But it seems the time I have spent writing and waiting for a response could have been spent reinstalling and I probably could have been mostly done with it by now. Still, if the same situation arose, I'd be right back at square one and searching around reading for hours for something that seems should be simple. 

"we'll go easy on you....We don't bite (much....)"...I'll tell that to my backside when I find it. :D 

So the only help I get is basically blow it up and start over and put most everything on one partion? lmao. This is an advanced user solution?
:P  Just kidding around. :guitar: I'm pushin the hump of midlife. Be gentle on an old hillbilly. ***cue dueling banjos***

Hope you have fun with Jaunty. I like it very much so far and has been good to me. 

About the partitions though, i think youre the first person ive come across that has used them all or had more than / and /home. 
Nothing wrong with learning though. :)

---

### Post by Slug71 on 2009-01-10
> **autocrosser said:**
> Sounds good---I'll stabilize my system over the next few days & look towards Grub2 this next weekend.......

Done, everything went sweet. Just made sure my Vista partition booted too.
Everything just seems to work with Jaunty.
I didnt use the Chainload method though. I just went ahead and did the complete upgrade right after install because of the probs i had with it before.
Might of worked now though with os-prober but not sure and i didnt really feel like doing a reinstall. :P

---

### Post by Etheric Seed on 2009-01-10
"Hope you have fun with Jaunty"

I will when I can log into it. ;)

---

### Post by autocrosser on 2009-01-10
Sounds good---I'll get it together & do it sometime in the next week or so....

---

### Post by Slug71 on 2009-01-10
> **Etheric Seed said:**
> "Hope you have fun with Jaunty"

I will when I can log into it. ;)

:lolflag: I'm guessing its something to do with all the partitions. Unfortunately i dont have a work around or solution though as ive never used that many partitions. :(

You might wanna try here.
[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

---

### Post by Etheric Seed on 2009-01-10
Problem self-solved. 

I decided I would go try my hand at it again. 
Restarted computer. Went to recovery mode and droped down to root prompt.

Did a ls to make sure everything was there.

Did cd /home

Did a ls

wala...a typo in setting up user name. lmao

restarted.  Used typo user name and password. Wala...in like flynn with the gazillion partitions and all. ;)  Thought it was simple. lol at self. So..at least my partioning wasn't the issue. it was My Edward Scissorhands manuever on the keyboard. lol No blowing it up and starting all over. Time to have some fun. Thanks all for responding.

---

### Post by autocrosser on 2009-01-10
Good job---enjoy Jaunty--the ride has been a bit "bumpy"--but never dull :)

---

### Post by Slug71 on 2009-01-10
> **Etheric Seed said:**
> Problem self-solved. 

I decided I would go try my hand at it again. 
Restarted computer. Went to recovery mode and droped down to root prompt.

Did a ls to make sure everything was there.

Did cd /home

Did a ls

wala...a typo in setting up user name. lmao

restarted.  Used typo user name and password. Wala...in like flynn with the gazillion partitions and all. ;)  Thought it was simple. lol at self. So..at least my partioning wasn't the issue. it was My Edward Scissorhands manuever on the keyboard. lol No blowing it up and starting all over. Time to have some fun. Thanks all for responding.

:lolflag: Nice job, it happens. Now enjoy. :)

---

### Post by autocrosser on 2009-01-11
Just got a very good reply from Scott Remnant about the underlying libraries that slowed the introduction of EXT4--makes some very good reading. You can follow the bug report/request at: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/197311)

Scott's information really shed light on the reasons we are using the vol_id library instead of blkid & show the start of one library to replace both (I REALLY vote a +1 to get blkid functions in Ubuntu!!!).

I have also reported that there is a 3sec faster boot from grub to gdm in my system with EXT4--I encourage everyone to run bootchart--you need to have a good base of results before changing to EXT4 & try to run it within the same kernel to try & negate any other variables other than the change from EXT3 to EXT4.

As one of the aims of Jaunty is a faster boot--anything that shaves 3sec off boot is a very good start.........

---

### Post by plun on 2009-01-11
EXT4 up and running....:lolflag:

Daily-live and alternate are both broken with manual partitioning

Took the mini.iso

[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/)

Ubuntu-desktop install broke but Ubuntu-server works....

The server runs fine and now to figure out Ubuntu-desktop):P

---

### Post by Gina on 2009-01-11
I have just installed Jaunty with ext4 partitions for / and /home on an old desktop.  This has a K6-2/450Mhz processor 256MB RAM and 8.6GB HD with very old SIS AGP graphics card.  It's struggling a bit but it's working.  I used yesterday's daily build Alternate i386 CD and manual partitioning.  3.5, 4.5 and 0.6 GB partitions for / /home and swap.

I think it's being hampered by low memory as it's using swap with very little running.  I might be able to get more RAM into it from my P3 desktop which seems to be on the way out.  Pity about the P3 - it's got a better processor.

---

### Post by autocrosser on 2009-01-11
> **plun said:**
> EXT4 up and running....:lolflag:

Daily-live and alternate are both broken with manual partitioning

Took the mini.iso

[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/)

Ubuntu-desktop install broke but Ubuntu-server works....

The server runs fine and now to figure out Ubuntu-desktop):P

Welcome back!! Did you take a look at the thread I posted? I figured you would be interested.....

---

### Post by plun on 2009-01-11
> **autocrosser said:**
> Welcome back!! Did you take a look at the thread I posted? I figured you would be interested.....

Well... I am trapped within my server..:^o

Inredible package mess for ubuntu-desktop, the generic kernel seems to be broken and gconf goes crazy during configurations

leads to apt seg-fault...  never seen that before..:-k

Aptitude also cannot sort it out

---

### Post by ShirishAg75 on 2009-01-11
> **plun said:**
> EXT4 up and running....:lolflag:

Daily-live and alternate are both broken with manual partitioning


what do you mean broken? Any screenshots or something about what happens when you try to do partitioning in ubiquity using daily. 

Also has anybody tried using the alternate-installer, any luck with that anybody?

---

### Post by Slug71 on 2009-01-11
> **ShirishAg75 said:**
> what do you mean broken? Any screenshots or something about what happens when you try to do partitioning in ubiquity using daily. 

Also has anybody tried using the alternate-installer, any luck with that anybody?

I used the AMD64 Alternate to install. Worked fine for me.
I had a DOS like screen all through setup and partitioning though.

---

### Post by plun on 2009-01-11
> **ShirishAg75 said:**
> what do you mean broken? Any screenshots or something about what happens when you try to do partitioning in ubiquity using daily. 

Also has anybody tried using the alternate-installer, any luck with that anybody?

You cannot use **Manual partitioning**...

Blow the whole disk is working...

I have **2 partitions I want to preserve**, my old /home and my /media partition

-----------------------------------

Phoronix with a brand new test...

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=1)


And 2.6.29-RC1 is out... and I have no GUI...:^o:redface:

---

### Post by Slug71 on 2009-01-11
> **plun said:**
> You cannot use **Manual partitioning**...

Blow the whole disk is working...

I have **2 partitions I want to preserve**, my old /home and my /media partition

-----------------------------------

Phoronix with a brand new test...

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=1)


And 2.6.29-RC1 is out... and I have no GUI...:^o:redface:

Hmm... I used manual. I always do.

---

### Post by ShirishAg75 on 2009-01-11
The phoronix test suite also shows a screenshot of being able to partition without an issue (using ext4)

---

### Post by plun on 2009-01-11
> **Slug71 said:**
> Hmm... I used manual. I always do.

Yes for 64 bit but I am using 32 bit...

The **text based** _manual_  partitioner works with the mini.iso and the alternate installer

(ColinW wrote a note about this and Ubiquity)

But then gnome is broken...

Trying LXDE desktop environment...):P

---

### Post by plun on 2009-01-11
Followup....   LXDE up and running

This was my situation

> plun@plun:~$ sudo blkid
[sudo] password for plun: 
/dev/sda1: UUID="9E7864E67864BEA1" TYPE="ntfs" 
/dev/sda2: UUID="ea3deaca-ed2f-417a-80d8-5f6e77a17591" TYPE="ext4" 
/dev/sda3: UUID="1bd53d0e-a190-4358-a24f-cdea59941581" TYPE="ext4" 
/dev/sda4: UUID="ea60a35d-3a50-4b02-8eda-60da18ad08fd" TYPE="ext3" 

sda2 is my system partition, also includes /home for a while, EXT4... 

sda3 media which already was a EXT4 partition

sda4 is my old /home which I preserved as EXT3...  I am a coward..


On sda2 I got my home now because I wanted a complete clean environment..

---

### Post by MacUntu on 2009-01-11
> **autocrosser said:**
> I have also reported that there is a 3sec faster boot from grub to gdm in my system with EXT4--I encourage everyone to run bootchart
No difference here but 2.6.28 boots a lot faster than 2.6.27. Some numbers for my 1.83GHz Core Duo, 2GB RAM notebook:

Intrepid, 80GB 5400rpm, EXT3: 28 sec.
Intrepid, 320GB 7200rpm, EXT3: 21 sec.
Jaunty, 80GB 5400rpm, EXT3: 21 sec.
Jaunty, 80GB 5400rpm, EXT4: 21 sec.

Damn, I didn't need that faster hard disk! :D Too bad I can't test Jaunty on the 7200rpm disk as I need it for my productive system.

---

### Post by Gina on 2009-01-11
> **ShirishAg75 said:**
> Also has anybody tried using the alternate-installer, any luck with that anybody?32bit yes - 64bit no.

---

### Post by Gina on 2009-01-12
I'm hoping to have another go at installing a new Jaunty system on my AMD64.  Alt CD won't work with CD or DVD so I'm goint to try the "install from Ubuntu" way (or maybe unetbootin).  I have a working Jaunty system on my AMD64 using ext3 and I want to check out ext4.  The **Alt CD** and **manual** partitioning worked fine on a very old desktop.  So having got it going on my oldest working machine, I want to try it on my newest and best :lol:

---

### Post by plun on 2009-01-12
> **Gina said:**
> I'm hoping to have another go at installing a new Jaunty system on my AMD64.  Alt CD won't work with CD or DVD so I'm goint to try the "install from Ubuntu" way (or maybe unetbootin).  I have a working Jaunty system on my AMD64 using ext3 and I want to check out ext4.  The **Alt CD** and **manual** partitioning worked fine on a very old desktop.  So having got it going on my oldest working machine, I want to try it on my newest and best :lol:

Well.....it seems to be bugs around.

A bug which I confirmed nevertheless

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/316148/](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/316148/)

---

### Post by Gina on 2009-01-12
I've been having that problem with the Live CD too.

Added to the bug report in Launchpad.

---

### Post by ShirishAg75 on 2009-01-12
Have nominated the bug for jaunty release. Let's see if the developers accept the same.

---

### Post by plun on 2009-01-12
> **ShirishAg75 said:**
> Have nominated the bug for jaunty release. Let's see if the developers accept the same.

Well...  "Proof of concept"...

[[img]http://ubuntu-pics.de/thumb/8281/screenshot_8L3RxY.png[/img]](http://ubuntu-pics.de/bild/8281/screenshot_8L3RxY.png)

For Alpha 3 maybe I shall study QA for CD testing and Ubiquity.. this should just work, more then basic functionality, IMHO.

---

### Post by ShirishAg75 on 2009-01-12
the master bug [lpbug]310083[/lpbug]was found and our bug was marked as a duplicate. 

Would do a clean install only when this is resolved.

---

### Post by Gina on 2009-01-12
To check whether the "media change" problem was due to the host machine or system to install, I tried installing a 32 bit version on my AMD64 and it failed.  This was the same CD I used to install  Jaunty successfully on my AMD K6-2 machine.

I've added a 128MB RAM module making 384MB and it's made a big difference - it's now reasonable for that level of machine.

---

### Post by ShirishAg75 on 2009-01-13
Hi all, 
 A new ubiquity is in the offing. 

> 

ubiquity (1.11.3) jaunty; urgency=low

  [ Colin Watson ]
  * Correct Bazaar link in debian/copyright, really this time.
  * Update copyright years.
  * Fetch subarchitecture in remove_extras (LP: #316446).

  [ Evan Dandrea ]
  * Fix the edit partition dialog by properly preseeding
    partman/active_partition.
  * Add support for encrypting the home directory to the gtk frontend.
  * Automatic update of included source packages: apt-setup
    1:0.37ubuntu8, partconf 1.30ubuntu1.

  [ Mario Limonciello ]
  * Reset random mysql password on every ubiquity mythbuntu invocation.
  * Don't set anything in the mythbuntu_summary step.
  * Transition apply-type code into python to be called directly from
    mythbuntu_install.py instead.
    - Along with this, handling for leaving files when not reformatting
      /home should be fixed. (LP: #305236)
    - Mythweb acl to SQL should be fixed now, but not necessarily
      authentication.
[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/003167.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/003167.html)

Its building as we speak.

Update:- The i386 build is supposed to start an hour. Others as late as 17 hours from now. Few archs already done. 

Those would be in the publishing queue

---

### Post by plun on 2009-01-14
It works....:lolflag:


> plun@plun:~$ sudo blkid
[sudo] password for plun: 
/dev/sda1: UUID="493fdede-d2e2-41a8-9f01-cfe5e913456c" TYPE="ext4" 
/dev/sda2: TYPE="swap" UUID="e906f957-cd3c-4ab4-a090-ae300d69c94a" 
/dev/sda3: UUID="8d38a58b-0a78-4e13-9ee6-d5c797bed386" TYPE="ext4" 
/dev/sda4: UUID="957a15fb-1257-44a1-b9fe-3a1bb918ee6d" TYPE="ext4" 
/dev/ramzswap0: TYPE="swap" 



What a "La grande"  mess I got....):P

Just to fix it....:D

---

### Post by Archmage on 2009-01-14
Please forgive me but what alternate AMD64-CDs will be able to create a ext4 at the installation?

The one from yesterday (13th), Today (14th) or Tomorrow (15th - is this Alpha 3?).

---

### Post by autocrosser on 2009-01-14
(image of crossed fingers) The 15th "should" be Alpha 3

---

### Post by Slug71 on 2009-01-14
> **Archmage said:**
> Please forgive me but what alternate AMD64-CDs will be able to create a ext4 at the installation?

The one from yesterday (13th), Today (14th) or Tomorrow (15th - is this Alpha 3?).

They will all be able to but i'd wait for the Alpha tomorrow. :)

---

### Post by Gina on 2009-01-14
Well, up to yesterday, no daily builds of Alt AMD64 CDs have installed with ext4 (or ext3 for that matter) nor have I had any joy with the 32 bit version on my 64 bit machine.  I'm not bothering to try again until Alpha 3.

---

### Post by obscur156 on 2009-01-14
By default.
Just if there is no risk of bug or anything goes wrong.
regards

---

### Post by karlmp on 2009-01-14
optional 

it requires too much defragmentation

---

### Post by karlmp on 2009-01-14
[http://linux.slashdot.org/article.pl?sid=09%2F01%2F14%2F2152200&from=rss](http://linux.slashdot.org/article.pl?sid=09%2F01%2F14%2F2152200&from=rss)

---

### Post by MacUntu on 2009-01-14
> **karlmp said:**
> it requires too much defragmentation

Huh? Aren't delayed allocation and preallocation two key features that would even more reduce the likeliness of fragmentation compared to ext3...

---

### Post by cjwatson on 2009-01-14
If you're new to Linux, separating out your partitions so finely is probably just making trouble for yourself down the line, as you don't have the experience to know what a good split of disk space would be. (Personally, I do have the experience and I just use a single giant partition; life's too short to mess about with resizing and moving partitions all the time.)

It's not obvious to me what your username/password problem is, but I rather doubt that it has anything to do with ext4; I would suggest booting in recovery mode and resetting it. It's accessible from the GRUB menu.

---

### Post by cjwatson on 2009-01-14
I believe I fixed the "media change" problem today. (I couldn't reproduce it myself, annoyingly, but I did get one report that my semi-guesswork fix had done the job, so I'm hopeful.)

Seriously (and this goes to everyone mentioning installation failures here, though I know some of you did file bugs), please file bugs about installation failures. Even though I have trouble following all the bug reports that get filed, I have even less chance of following all the forum posts that get made! If you don't file a bug, you're betting that the problem is not specific to you and that somebody else will report it; if neither of those is the case then it's entirely possible that your bug won't get fixed.

With regard to installation failures, I operate mainly on noise. If lots of people are shouting about something, then I'd better go and have a look at it - however, that shouting does need to be in a place where I'll see it, which is more likely to be the bug tracking system.

---

### Post by autocrosser on 2009-01-14
Thank You Colin!!!

It's good to have you here....:guitar:

---

### Post by karlmp on 2009-01-15
[QUOTE=MacUntu]Huh? Aren't delayed allocation and preallocation two key features that would even more reduce the likeliness of fragmentation compared to ext3...[/QUOTE]




Oddly enough, these are major new features in ext4, which is also getting support for online defragmentation [http://lwn.net/Articles/284529/](http://lwn.net/Articles/284529/)

---

### Post by MacUntu on 2009-01-15
> **karlmp said:**
> Oddly enough, these are major new features in ext4, which is also getting support for online defragmentation [http://lwn.net/Articles/284529/](http://lwn.net/Articles/284529/)
And having a defragmentation tool leads to "it requires too much defragmentation"? Sorry, that doesn't sound reasonable.

---

### Post by Gina on 2009-01-15
Thank you Colin from me too :) Will the fix make it to Alpha 3?

---

### Post by MacUntu on 2009-01-16
Are there any stress tools available (fsstress?) to test EXT4?

---

### Post by blazemore on 2009-01-16
The advanced users will all choose ext4. That gives them time to fix the bugs and iron everything out, so they can make it the default in 9.10, which is the idea I think.

---

### Post by Radon on 2009-01-16
> **blazemore said:**
> The advanced users will all choose ext4. That gives them time to fix the bugs and iron everything out, so they can make it the default in 9.10, which is the idea I think.
How would one go about finding what problem was caused by the FS and which by the Ubuntu Testing release?  (FYI downloading Ubu9.04 A3 ATM)

---

### Post by ShirishAg75 on 2009-01-17
> **cjwatson said:**
> I believe I fixed the "media change" problem today. (I couldn't reproduce it myself, annoyingly, but I did get one report that my semi-guesswork fix had done the job, so I'm hopeful.)

Seriously (and this goes to everyone mentioning installation failures here, though I know some of you did file bugs), please file bugs about installation failures. Even though I have trouble following all the bug reports that get filed, I have even less chance of following all the forum posts that get made! If you don't file a bug, you're betting that the problem is not specific to you and that somebody else will report it; if neither of those is the case then it's entirely possible that your bug won't get fixed.

With regard to installation failures, I operate mainly on noise. If lots of people are shouting about something, then I'd better go and have a look at it - however, that shouting does need to be in a place where I'll see it, which is more likely to be the bug tracking system.

Colin, 
where or which package has the fix ? Perhaps need to move to daily build of 17th January?

---

### Post by sirlatrom on 2009-02-06
> **plun said:**
> Ubiquity crashes for me when I tries to edit a partition...

i386, todays build.

gparted is outdated and cannot be used.

News flash: [http://sourceforge.net/project/shownotes.php?group_id=115843&release_id=658832](http://sourceforge.net/project/shownotes.php?group_id=115843&release_id=658832)

---

### Post by spudgunner on 2009-02-09
I'm interested in studying the ext4 source code to help me with a programming project in school. Does anybody know where I could download it from (and if it exists, a site that keeps track of code for multiple open source projects)?

---

### Post by cjwatson on 2009-02-09
[https://launchpad.net/linux](https://launchpad.net/linux) has the download links; grab the most current version, extract it, and look in the fs/ext4/ directory.

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git) is the master revision control tree for the kernel.

As for a site that keeps track of multiple open source projects, that's part of [Launchpad]("https://launchpad.net/")'s purpose.

---

### Post by spudgunner on 2009-02-10
Thank you very much!

---

### Post by int on 2009-02-10
```
5 February 2009 : GParted 0.4.2
The big news for this GParted release is support for ext4 file systems, and the addition of an application help manual.

Key changes include:

    * Added support for ext4 file system
          o Support for ext4 is built into version 2.6.28 of the Linux kernel
          o e2fsprogs version 1.41.0 or higher required
    * Created application help manual
    * Updated gparted manual page
    * Made text beside field labels selectable (i.e., copy/paste UUID)
    * Added lvm2 physical volume detection
    * Reduced file system information disk reads to improve performance
    * Fixed application crash when saving details and locale not set
    * Enhanced copy/paste checks when MBR/EBR involve
```
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

---

### Post by zedx555 on 2009-02-23
I don't think GRUB supports EXT4 does it? It boots up but it is not officialy supported. GRUB 2 officialy supports it.

---

### Post by MacUntu on 2009-02-23
It does.

---

### Post by cjwatson on 2009-02-23
It's supported by Ubuntu's GRUB (Legacy) package, even if not by upstream.

---

### Post by deepclutch on 2009-02-23
Does a Ubuntu Intrepid on a ext4 is straight installable.does the kernel detects?should I need debian-installer based cd ?

---

### Post by forcecore on 2009-02-23
i always do manual installs only so ext4 exist for me and i chose ext4 by option.

---

### Post by cjwatson on 2009-02-23
Intrepid is not installable on ext4, and there are no plans to make it so.

---

### Post by autocrosser on 2009-02-23
> **deepclutch said:**
> Does a Ubuntu Intrepid on a ext4 is straight installable.does the kernel detects?should I need debian-installer based cd ?

Intrepid's kernel will not support it---you would need a 2.6.28 kernel. That would be the only limiting factor.

Wait a couple of months & install Jaunty at the RC release......

---

### Post by autocrosser on 2009-02-23
Greeting Colin!!!!!;)

---

### Post by cjwatson on 2009-02-23
No, it would not be the only limiting factor; there were several other components that needed small tweaks in order to support ext4.

---

### Post by forcecore on 2009-02-23
> **cjwatson said:**
> Intrepid is not installable on ext4, and there are no plans to make it so.

but in manual mode it is or not? so far alphas was insallable with ext4 on manual mode.

---

### Post by cjwatson on 2009-02-23
I repeat that Intrepid is not installable with ext4, regardless of whether you use manual or automatic partitioning. **Jaunty** alpha releases are installable with ext4; that feature was added well after the release of Intrepid. We do not intend to backport it.

---

### Post by Kow on 2009-02-24
> **cjwatson said:**
> Intrepid is not installable on ext4, and there are no plans to make it so.

I have no idea what you are talking about....
[[IMG]http://img5.imageshack.us/img5/6332/intrepidamd64.th.png[/IMG]](http://img5.imageshack.us/my.php?image=intrepidamd64.png)
[[IMG]http://img5.imageshack.us/img5/4193/intrepidamd642.th.png[/IMG]](http://img5.imageshack.us/my.php?image=intrepidamd642.png)

I am using the intrepid repos... kinda. :)

---

### Post by ugkbunb on 2009-02-24
> **Kow said:**
> I have no idea what you are talking about....
[[IMG]http://img5.imageshack.us/img5/6332/intrepidamd64.th.png[/IMG]](http://img5.imageshack.us/my.php?image=intrepidamd64.png)
[[IMG]http://img5.imageshack.us/img5/4193/intrepidamd642.th.png[/IMG]](http://img5.imageshack.us/my.php?image=intrepidamd642.png)

I am using the intrepid repos... kinda. :)

He says it not possible to *install* Intrepid on an EXT4 partition... not that is impossible to switch an Intrepid install over to ext4 via updating the kernel/booting off a liveCD

---

### Post by Kow on 2009-02-24
> **ugkbunb said:**
> He says it not possible to *install* Intrepid on an EXT4 partition... not that is impossible to switch an Intrepid install over to ext4 via updating the kernel/booting off a liveCD

That's not true either. The 2.6.27 kernel does support ext4, but I don't know if it should be trusted.

---

### Post by cjwatson on 2009-02-24
I'm sure you can make it work on something that started out being Intrepid if you try hard enough (it's all just software after all), but it won't work out of the box in any reasonable meaning of that term. In Intrepid's 2.6.27 kernel, it's only available as ext4dev; klibc doesn't have the necessary patch to let you boot off it; the module isn't copied into the initramfs; the installer's partitioner has no support for it; and so on. Obviously you can do anything with software if you try hard enough, but my statement is still true for most people.

(I'd also think twice before risking it given the ext4dev status, myself; but I'm not a filesystem developer.)

---

### Post by deepclutch on 2009-02-24
interesting :) .If I compile a custom 2.6.28 kernel(latest) with optimizations and with built-in ext4 support on Intrepid - Then ,Can I do a mirror(dd) of the current partition to  a new ext4 partition created ?(ofcourse ,with new kernel).I would like to know.thanks.Already e2fsprogs is 1.41 in Intrepid.

Is there anything I am missing ? :confused: ;I had already tried such kind of copying of installation from failing hdd's(where ,the transfer sometimes cease temparorily).Only thing ,I found difficult is ,some files/permissions(like suid bit etc messed out) problems ,which ,can be solvable .

---

### Post by cjwatson on 2009-02-24
It's all theoretically possible, but if you're going to mess about with this then maybe you might as well just use Jaunty ...

---

### Post by Starks on 2009-02-24
I'm getting "no space left on device" messages at least 5 times a week and they don't go away until I do a fsck from a livecd/liveusb environment.

---

### Post by forcecore on 2009-02-24
> **cjwatson said:**
> I repeat that Intrepid is not installable with ext4, regardless of whether you use manual or automatic partitioning. **Jaunty** alpha releases are installable with ext4; that feature was added well after the release of Intrepid. We do not intend to backport it.

sorry if i posted i wanted to say jaunty manual mode not intrepid.

---

### Post by plun on 2009-02-25
gparted is updated :popcorn:

[https://lists.ubuntu.com/archives/jaunty-changes/2009-February/005945.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-February/005945.html)


> **gparted (0.4.3-0ubuntu1**) jaunty; urgency=low

  [ Surfaz Gemon Meme, Colin Watson ]
  * New upstream release (LP: #305280)
    + **Added support for ext4 file system (LP: #137872)**
      [I][B]- Support for ext4 is built into version 2.6.28 of the Linux kernel
      - e2fsprogs version 1.41.0 or higher required[/B][/I]
    + Fixed bug in german translation (LP: #45449)
    + Fixed 'fails to recognize newly created swap partition'
      (LP: #137700, #114713)
    + Reduced file system information disk reads to improve performance
      (LP: #311470)
    + Fixed typo of "freedeskdesktop" in hal-lock name (LP: #37768)

  * debian/patches
    + dropped 05_GParted_Core.cc.diff, merged upstream
    + refreshed 10_dev_mapper.patch to be applied correctly
    + refreshed 01_fix-desktop.patch to be applied correctly


---

### Post by Nullack on 2009-02-25
Yep nice to see my / and /home showing ext4 in gparted

---

### Post by Kow on 2009-02-25
> **Starks said:**
> I'm getting "no space left on device" messages at least 5 times a week and they don't go away until I do a fsck from a livecd/liveusb environment.

This is why it won't be default in jaunty. Known bug. Won't lose you data... just very annoying and the novice user won't know how to fix it (or have the patience for it).

[http://news.gmane.org/gmane.comp.file-systems.ext4](http://news.gmane.org/gmane.comp.file-systems.ext4) take a look at the official ext4 mailing list and try and convince me it's "stable".

---

### Post by geoff123 on 2009-02-25
Not sure it should be default yet, but definitely should be at the next version.  A quick informal test on my computer shows it can copy files more than twice as fast than ext3.  (on jaunty using "time cp -r from to") Now that's a serious improvement.  Thanks EXT4 people.
:p

---


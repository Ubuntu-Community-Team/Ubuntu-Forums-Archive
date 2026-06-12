---
title: "Is anyone trying this with a Ext4 filesystem?"
date: 2009-07-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tjeremiah on 2009-07-09
If so, hows everything going so far?

---

### Post by ghindo on 2009-07-09
Just fine :popcorn:

---

### Post by taavikko on 2009-07-09
Been running splendid since Jaunty.

Waiting for online-defrag...

---

### Post by tjeremiah on 2009-07-09
cool. Im right now doing a fresh install, without wubi this time around and will give ext4 a go.

---

### Post by descendent87 on 2009-07-09
Been using ext4 for ages now, had no problems at all and fsck is much quicker (especially with big drives)

---

### Post by graphius on 2009-07-09
> fsck is much quicker
Confirmed...
and no problems with ext4.

---

### Post by bhishan on 2009-07-09
i have been using it since jaunty, the experience is normal

---

### Post by Darkshade on 2009-07-09
I'm using ext4 for / and I've never had any problems with it. Actually the only reason my /home is still ext3 is because I don't have another hard disk to move my files, format it and copy back.

---

### Post by bob-linux-user on 2009-07-09
No problems with it. Boots a lot faster than Hardy with ext 3. on my Athlon XP2500 with 2 gig RAM goes from leaving Grub to ready to use in about one minute. This is about 5 times as quick as Xp on the same PC.

---

### Post by Gina on 2009-07-09
No problems with ext4 either :)

---

### Post by izizzle on 2009-07-09
Everything is working flawlessly. 

You may want to read [THIS]("http://ubuntuforums.org/showthread.php?t=1194205") before you install.

---

### Post by tjeremiah on 2009-07-09
> **izizzle said:**
> Everything is working flawlessly. 

You may want to read [THIS]("http://ubuntuforums.org/showthread.php?t=1194205") before you install.

thanks, I havent done it yet (burns to cd but always saids its missing two file :()

---

### Post by Regenweald on 2009-07-09
pretty normal here. root and home ext4. Converted an ext3 250 gig to ext4 in Karmic and ran into a small problem with inodes. One manual fsck fixed all.

---

### Post by celticbhoy on 2009-07-09
Whole Karmic install on ext4 and not had an ounce of bother from it.

---

### Post by martinpm24 on 2009-07-09
fresh install with ext4, no probem here.

---

### Post by mrsurb on 2009-07-09
All good here - formatted / to ext4 and then fresh install, my separate /home partition I converted from ext3 to 4, no problems. Definite speed improvement.

---

### Post by wayne_cat on 2009-07-09
> **mrsurb said:**
> All good here - formatted / to ext4 and then fresh install, my separate /home partition I converted from ext3 to 4, no problems. Definite speed improvement.

I have tested ext3 and ext4 with bonnie++ ... not much differences. On converted file systems only new files are "ext4 files" ... the old file should be as slow as before. Copy the files around (not move inside one partition!) to increase the speed a little bit.


I'm still on ext3 ... waiting for brtfs ... Mmmm ... snapshots.

---

### Post by tjeremiah on 2009-07-09
I have a question. Since im having trouble installing ext4 without wubi, will 9.10, when upgraded to final, force a ext4?

---

### Post by wayne_cat on 2009-07-09
> **tjeremiah said:**
> I have a question. Since im having trouble installing ext4 without wubi, will 9.10, when upgraded to final, force a ext4?

ext4 is the default file system (since alpha2)

see chapter "ext4 by default"

[http://www.ubuntu.com/testing/karmic/alpha2](http://www.ubuntu.com/testing/karmic/alpha2)

but you could still use ext3

---

### Post by mrsurb on 2009-07-09
> **wayne_cat said:**
> I have tested ext3 and ext4 with bonnie++ ... not much differences. On converted file systems only new files are "ext4 files" ... the old file should be as slow as before. Copy the files around (not move inside one partition!) to increase the speed a little bit.


I'm still on ext3 ... waiting for brtfs ... Mmmm ... snapshots.

The main speed improvement I've noticed has been on boot - ie reading lots of files off the newly formatted /

I'm waiting for next week when I'm getting a 32Gb SSD - thinking of putting ext4 on that unless anyone has any better ideas?

---

### Post by tjeremiah on 2009-07-09
> **wayne_cat said:**
> ext4 is the default file system (since alpha2)

see chapter "ext4 by default"

[http://www.ubuntu.com/testing/karmic/alpha2](http://www.ubuntu.com/testing/karmic/alpha2)

but you could still use ext3

eh, thanks because I forgot all about the alpha 2 download, just get it straight from there. Instead, I spent half of the afternoon downloading 9.04 which always ended up with one missing file  :(

---

### Post by wayne_cat on 2009-07-09
> **mrsurb said:**
> The main speed improvement I've noticed has been on boot - ie reading lots of files off the newly formatted /

I'm waiting for next week when I'm getting a 32Gb SSD - thinking of putting ext4 on that unless anyone has any better ideas?

Be careful if the ssd is "an older model" ... Even Theodor Ts'o would be careful :biggrin:

[http://www.linux-mag.com/id/7272](http://www.linux-mag.com/id/7272)

ext4 is a good file system ... but it is just an evolution ... not a revolution.

---

### Post by wayne_cat on 2009-07-09
> **tjeremiah said:**
> eh, thanks because I forgot all about the alpha 2 download, just get it straight from there. Instead, I spent half of the afternoon downloading 9.04 which always ended up with one missing file  :(

You could also use the "daily build"

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

---

### Post by tjeremiah on 2009-07-09
> **wayne_cat said:**
> You could also use the "daily build"

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

thanks ;)

---

### Post by Martin Marshalek on 2009-07-09
Ext4 is running great, now that I'm running Jaunty 64bit I decided to go all out and try the newest Linux filesystem.

---

### Post by autocrosser on 2009-07-09
Nothing but ext4 from shortly after it was released--no problems from day1---will never go back to ext3.........

---

### Post by alphacrucis2 on 2009-07-09
> **autocrosser said:**
> Nothing but ext4 from shortly after it was released--no problems from day1---will never go back to ext3.........

Anyone know the status of btrfs in 2.6.31? I'd be curious to try it out.

---

### Post by autocrosser on 2009-07-10
Have not looked into it in a while--you might browse linux.com or one of the kernel-centric sites..there are several new FS coming up.......

---

### Post by alphacrucis2 on 2009-07-10
> **autocrosser said:**
> Have not looked into it in a while--you might browse linux.com or one of the kernel-centric sites..there are several new FS coming up.......

I notice that the version of gparted I have in Karmic doesn't list btrfs as an option. Will check those sites.

---

### Post by wayne_cat on 2009-07-10
> **alphacrucis2 said:**
> I notice that the version of gparted I have in Karmic doesn't list btrfs as an option. Will check those sites.

I'm "playing" with btrfs at the moment .... You will need something like this:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

if you want a gparted version with btrfs.

this could be an option:

[http://packages.ubuntu.com/hu/karmic/admin/btrfs-tools](http://packages.ubuntu.com/hu/karmic/admin/btrfs-tools)

---

### Post by Regenweald on 2009-07-10
> **alphacrucis2 said:**
> Anyone know the status of btrfs in 2.6.31? I'd be curious to try it out.

Gnomeuser has been testing it for a while now. You could ask him. Still early days though. I've more been looking out for news on ext4 online defrag. I've got a media drive at 17.5% fragmentation.

---

### Post by renkinjutsu on 2009-07-10
> **Regenweald said:**
> Gnomeuser has been testing it for a while now. You could ask him. Still early days though. I've more been looking out for news on ext4 online defrag. I've got a media drive at 17.5% fragmentation.

How many drives do you have?
to get rid of fragmentation, the quickest way would be to move the whole drive onto another drive, then move the files back onto the original drive.. also requires much less read/write than a defragmentation i think.

---

### Post by Zack McCool on 2009-07-10
> **renkinjutsu said:**
> How many drives do you have?
to get rid of fragmentation, the quickest way would be to move the whole drive onto another drive, then move the files back onto the original drive.. also requires much less read/write than a defragmentation i think.

That's the way we used to do it on the old Sun boxes back in the early 90's, but the drives were much smaller than they are now...

---

### Post by wayne_cat on 2009-07-10
> **Zack McCool said:**
> That's the way we used to do it on the old Sun boxes back in the early 90's, but the drives were much smaller than they are now...

and today we have these silly notebooks with huge disks ... with only one huge disk :biggrin:

---

### Post by tjeremiah on 2009-07-10
I get this annoying error every time I try to install...

---

### Post by psyke83 on 2009-07-10
> **tjeremiah said:**
> I get this annoying error every time I try to install...

The problem could be "exactly what it says on the tin"... :P

Check the [md5sum]("http://cdimage.ubuntu.com/releases/karmic/alpha-2/MD5SUMS").

If the file is corrupt, grab the torrent and point the download to the existing .iso file - transmission (or any bittorrent client) will re-download only the corrupt chunks.

When you're burning, always burn at the lowest speed and make sure to do a verification afterwards.

---

### Post by tjeremiah on 2009-07-10
> **psyke83 said:**
> The problem could be "exactly what it says on the tin"... :P

Check the [md5sum]("http://cdimage.ubuntu.com/releases/karmic/alpha-2/MD5SUMS").

If the file is corrupt, grab the torrent and point the download to the existing .iso file - transmission (or any bittorrent client) will re-download only the corrupt chunks.

When you're burning, always burn at the lowest speed and make sure to do a verification afterwards.

I did all of that, things are ok including the iso, drive, and cd. Ill burned it once again at its lowest speed. Im going to try one more time, if fails, bed time because I have work in 7 hrs :p

---

### Post by Sepanderi on 2009-07-10
I'm thinking of creating a HTPC/server on Ubuntu 9.04 and I'm still wondering whether I should use ext4 or ext3. Though ext4 sounds tempting, I'm still a bit concerned about the file corruption issues. IMO not a good thing at all, whether you have a desktop or a server system. I'll propably go for the ext4 and hope for the best. :p

---

### Post by descendent87 on 2009-07-10
Been using it since before Januty was released and haven't had any curroption issues, had to hard reset a few times aswell and just needed a fsck (which was flying compared to ext3 on a 400GB drive)

---

### Post by tad1073 on 2009-07-10
I have used ext4 since 9.04. Works great for my needs.

---

### Post by tjeremiah on 2009-07-10
> **psyke83 said:**
> The problem could be "exactly what it says on the tin"... :P

Check the [md5sum]("http://cdimage.ubuntu.com/releases/karmic/alpha-2/MD5SUMS").

If the file is corrupt, grab the torrent and point the download to the existing .iso file - transmission (or any bittorrent client) will re-download only the corrupt chunks.

When you're burning, always burn at the lowest speed and make sure to do a verification afterwards.

Ok, it installed but after an update I got a grub error and nothing loaded ( I forgot all about the sticky warning ). So now im reinstalling again. One question, how do I bypass grub when I boot? I cant access my other OS's.

---

### Post by Regenweald on 2009-07-10
> **renkinjutsu said:**
> How many drives do you have?
to get rid of fragmentation, the quickest way would be to move the whole drive onto another drive, then move the files back onto the original drive.. also requires much less read/write than a defragmentation i think.

Thanks man, knew about this one :) Guess a shot is the easiest answer: Drive is dev/sdc1
On the other side of that coin, / is at a laughable .02% fragmentation.

---

### Post by mrsurb on 2009-07-10
> **descendent87 said:**
> Been using it since before Januty was released and haven't had any curroption issues, had to hard reset a few times aswell and just needed a fsck (which was flying compared to ext3 on a 400GB drive)

ext4 - how to give a flying fsck!

Quick question - how do you find out the fragmentation level of your partitions?

---

### Post by tjeremiah on 2009-07-10
I give up. Everytime I try to download, alpha2 or daily updated one, I always get an error. Ill wait for 9.10 to break away from wubi. Ill continue testing Karmic on wubi.

---

### Post by wayne_cat on 2009-07-10
> **mrsurb said:**
> 

Quick question - how do you find out the fragmentation level of your partitions?

I'm using ext2_frag (supports ext2, ext3 and ext4)

(sample report in the attachement)

---

### Post by Col-1023 on 2009-07-11
Does ext4 still allocate 5% of the usable disk space for root, and if it does, will the tune2fs command that works for ext3 work for ext4, so I can reduce the space alotted to say 1%?

Is ext4 a good option for external drives?

TIA.

---

### Post by mrsurb on 2009-07-11
Yes to both - ext4 reserves 5% and tune2fs can change it. I've been using ext4 on an external 60GB HDD used for bittorrents for a couple of weeks quite happily, even after I tuned the reserved space out of existence.

---

### Post by jocko on 2009-07-11
> **tjeremiah said:**
> I get this annoying error every time I try to install...
I get the same. 

Edit: I moved the rest of this post [here]("http://ubuntuforums.org/showthread.php?p=7598701#post7598701"), to avoid double posting...

---

### Post by Col-1023 on 2009-07-14
Thanks Mrsurb for your reply.

---

### Post by phenest on 2009-07-26
I had been using Jaunty with / as ext4 and /home as ext3. I've just moved /home to a new ext4 partition, and WOW! What a speed increase! I have Karmic as ext4 too.

---

### Post by xx58 on 2009-07-27
:rolleyes: Work like charm.

---

### Post by halovivek on 2009-07-27
I have installed and using it only. It is really fast and going better.

---

### Post by Gina on 2009-07-27
Been using ext4 since it's introduction and using it with Jaunty on main system.  No problem :)

---

### Post by VladNistor on 2009-07-27
Been using Ext4 since Jaunty. It's faster in most respects methinks. No issues so far. Also waiting for online defrag.

---

### Post by jongkind on 2009-07-27
> **renkinjutsu said:**
> How many drives do you have?
to get rid of fragmentation, the quickest way would be to move the whole drive onto another drive, then move the files back onto the original drive.. also requires much less read/write than a defragmentation i think.

Pyfragtools works even better:

[http://ubuntuforums.org/showthread.php?t=169551]("http://ubuntuforums.org/showthread.php?t=169551")

---

### Post by izizzle on 2009-07-27
I've been running on EXT4 and everything is going just fine...and fast.

---

### Post by Nburnes on 2009-07-27
ext4 hasn't caused me any pains and I was even using it on Jaunty as others have said.:)

---

### Post by ranch hand on 2009-07-27
I can not believe that this thread is still going.  This is the forum for 9.10 TESTING.

A more interesting thread may be "Is anyone trying this with ext2".

---

### Post by Darkshade on 2009-07-27
> **Darkshade said:**
> I'm using ext4 for / and I've never had any problems with it. Actually the only reason my /home is still ext3 is because I don't have another hard disk to move my files, format it and copy back.

Woot finally done! :D
Now all my systems - Ubuntu Karmic (main OS), Kubuntu Karmic (testing) and Ubuntu Jaunty (backup OS, which I have never used since installing Karmic, maybe I'll wipe it up and install something different to play with) plus my separate /home for my main install are ext4 :popcorn:
Everything works like a charm :)

---

### Post by wayne_cat on 2009-07-27
> **ranch hand said:**
> I can not believe that this thread is still going.  This is the forum for 9.10 TESTING.


Wait for reply #399402939205993281

```
Do you remember ... Karmic with ext4... 15 years ago ... worked like a charm
```:biggrin:

---

### Post by PGHammer on 2009-07-28
> **wayne_cat said:**
> Wait for reply #399402939205993281

```
Do you remember ... Karmic with ext4... 15 years ago ... worked like a charm
```:biggrin:

Which is why he's asking about ext4 (which is supposed to be the *default* when Karmic ships).  Though Jaunty supports ext4, ext3 is the default (and it's still the default with Karmic's alphas).  However, I'm running with ext4 just fine.

Part of testing a new build is testing new filesystems (especially a major change such as ext4, since it will be the likely default).

---

### Post by W2IBC on 2009-07-28
ext4 been working like a charm.

---

### Post by wilko on 2009-07-29
Absolutely fine - quicker too!

---

### Post by Crunchy the Headcrab on 2009-07-29
Can't speak for Ubuntu, but I am using Ext4.  Working great.

---

### Post by nanog on 2009-07-29
Don't know if anyone else has mentioned this but its quicker and boots faster!

#sarcasm

---

### Post by wayne_cat on 2009-07-29
> **nanog said:**
> Don't know if anyone else has mentioned this but its quicker and boots faster!

#sarcasm

Sir, thank you for this brand new information :biggrin:

---

### Post by Darkshade on 2009-07-29
> **nanog said:**
> Don't know if anyone else has mentioned this but its quicker and boots faster!

#sarcasm

No way! :o :o :o

---


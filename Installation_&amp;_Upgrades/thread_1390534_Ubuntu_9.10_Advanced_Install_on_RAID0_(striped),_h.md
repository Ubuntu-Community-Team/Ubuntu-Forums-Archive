---
title: "Ubuntu 9.10 Advanced Install on RAID0 (striped), hit a brick wall."
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by Phosphorror on 2010-01-25
Greetings all,

I have a RAID0 (striped RAID) configured hard disc, with is 2x500GB SATA drives set up as 1TB. The pc is a Medion 2.6ghz Quad Core Q6600 with various bells and whistles such as e-SATA, DVB-T/S TV Card, 2gb memory etc, with Windows Vista.

Now, I have set aside a partiton on 161.6gb which was not given a drive letter. The installer notices that RAID is working, so I entered YES to detect raid.

To the best of my knowledge, I don't have to use the partitioner as I created one.

I have:
#1 primary 815.7Gb B NTFS (Windows Vista install)
#6 logical 161.6gb ext4 (where I want Ubuntu to go to)
#7 logical 6.2gb F swap (I assume a Ubuntu 'swap file area?)
#5 logical 16.7gb fat32 (backup recovery for Windows Vista)

This is displayed in the 'Partition Disks' menu. 

As I stated, I want Ubuntu to live in this 160 I created without the drive letter, as I know Ubunbtu would not need such a thing.

I have gone through all the detecting keyboard yaddayadda bits now, and so on. 

But now, I have hit a block.

Where do I go from here? I am itching to get Ubuntu to work on this somehow! Others have said totally remove raid, and bring the PC back to it seeing the drives as two seperate 500gb ones. But a forum member on here pointed out that the advanced install disc I obtained the ISO for should do the job.

I look forward to the co-operation from you guys. Help liberate another PC from the dreaded M$!

Many thanks in advance...

---

### Post by Nightstrike2009 on 2010-01-26
Hiya mate, nice to see you here at long last old friend,

I've heard that Ubuntu 9.10 Live CD now supports Raid0 as standard, so why not try the standard one instead of advanced, you never know it may work. As well as saving you a serious headache trying to work out that advanced installer. ;-)

PS: I eventually intend to go over to a Ubuntu only system (instead of dual-boot) and only use XP within Sun Microsystems "Virtual Box" if I can't avoid it any other way. I am very, very close to achieving this, I too thought I would be a dual-booter for ever, but never say never.

---

### Post by Nightstrike2009 on 2010-01-26
Whoops - I Multiple posted (x2) due to my impatience and slow net connection - Message Removed

---

### Post by Nightstrike2009 on 2010-01-26
PS if you have problems burning CD/DVD with Ubuntu try "Gnome Baker" it resolved my disc burning issues. :-) 
I ain't using "Brasero" ever again unless I wish to create a CD clock or I am short of drinks coasters. :-(

Gnome Baker link below;
[http://packages.ubuntu.com/karmic/gnomebaker]("http://packages.ubuntu.com/karmic/gnomebaker")

PPS: I know this may not be relevant but i posted twice by accident and didn't want to make myself look stupid. 
Whoops I have anyhow. LOL :-)

---

### Post by Phosphorror on 2010-01-26
Cheers Nightstrike,

I feel like a total plank for not trying the normal CD. In an ideal world, I would get rid of RAID and have 500gb for Windows, 500gb for Ubuntu. But, it's not quite as easy as that just yet.

Anyway, I shall give it a whirl and keep you posted.

---

### Post by phillw on 2010-01-26
> **Phosphorror said:**
> Cheers Nightstrike,

I feel like a total plank for not trying the normal CD. In an ideal world, I would get rid of RAID and have 500gb for Windows, 500gb for Ubuntu. But, it's not quite as easy as that just yet.

Anyway, I shall give it a whirl and keep you posted.

Raid and 9.10 haven't had the best of starts. a couple of choices ... 9.04, which should be fine, but you're stuck for upgrade to 10.04 (the raid is pretty much already fixed)

another option is 8.04.3 - in the next couple of days 8.04.4 is due out - that will be upgradeable to 10.04 as an LTS --> LTS upgrade.

Or, if it is not a production machine, you can try out 10.04 now - it's pretty stable - but is still a development release, so it may 'break' occasionally before it is released at the end of April. Grub1.98 (used in 10.04) has added raid support that 1.97beta (Karmic) doesn't have. A further choice would be to use burg on 9.10 instead of grub - that has raid support and has been backported for Karmic Koala. There's some stuff on burg over here --> [http://ubuntuforums.org/showthread.php?t=1378951](http://ubuntuforums.org/showthread.php?t=1378951)  (My request to back-port support for 9.10). you can possibly PM bean123 for further information.

Hope the above is of help.

Regards,

Phill.

---


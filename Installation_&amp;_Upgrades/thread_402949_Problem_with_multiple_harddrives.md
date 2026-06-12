---
title: "Problem with multiple harddrives"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by someusername on 2007-04-06
I have two physical harddrives. HD1 is running Raid 0, (striped mode) and HD2 is partitioned into two/three partitions, or rather is partitioned into two as it is right now, but I could do it in three.

I would like to get some help with how I should go about making the computer boot and present me with the choice of either windows or linux. 

GRUB failed me when I tried installing with the CD-wizard; the computer started, windows chkdsk started, said there was a problem with the second drive, "fixed it", and when I then gave BIOS a different HDD prio., so that the second harddrive was prio one, it said that no operating system was installed (in a DOS-look-a-like background).

---

### Post by Ken in Seattle on 2007-04-06
I think more info is needed. I am probably not the one to give you the answer either being new to ubuntu (but a long time unix user) 
I came to post my own issue and yours is similar. I had two sata drives set up as JBOD on a raid controller and install of edgy went fine. GRUB worked fine as well.

Then I added an IDE disk to the mix and used WD data lifeguard tools to migrate the xp over to it.
XP refused to boot or even load the grub menu until I reinstalled it using rescue mode on the alternative install cd.
Then it would give me the menu and load xp or ubuntu fine until I did a hard power cycle. At that point it would not load the grub until I went back through the rescue mode reinstall grub.

I understand this is probably because Windoze always treats the IDE as hd0 so I reinstalled xp over on the migrated IDE partition one.
This worked for XP (but lost the settings in the registry which was ok with me) 

Today I did the recovery dance from the alternative cd and reinstalled grub.
It boots ubunto ok now but the xp entry on the grub menu is for the OLD XP install which oddly enough also works fine.

I am going to try adding an entry to the grub lst to choose which xp to load on boot just to see if it works or goes horribly wrong.

If you did not use the alternative cd, (and figure out how to load support for your raid hardware (some of which are really softraids)) you may need to look up that alley.

Hopefully someone who knows more will drop in to comment.

---

### Post by someusername on 2007-04-07
Hi,

Thanks for the answer.

I think a thing here is that I've got multiple physical harddrives and hence more than one MBR. I'm not sure on how to tackle the situation at all, so I'm posting here to get suggestions: suggestions on what information would help you all give me suggestions is also welcome, because I really don't know what "more information" to give you or how to acquire that info.

Regards
someusername

---

### Post by someusername on 2007-04-11
This really fu.cking insane. I post two threads and wait a month for an answer, and noone seems to be able to answer my question... 

Are the devs really that incompetent? Why would you ever choose to use Ubuntu?

---


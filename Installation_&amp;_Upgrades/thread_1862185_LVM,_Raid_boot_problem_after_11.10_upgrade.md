---
title: "LVM, Raid boot problem after 11.10 upgrade"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by _dolittle_ on 2011-10-16
Hi,
just upgraded from 11.04 to 11.10. The system (/) is located on a small SSD that still has some space left. My data files and my home directories are on a RAID+LVM setup consisting of three hdds.

After the upgrade the system shows a very strange boot behavior. At the first boot atempt the system shows the grub2 screen containing the linux 3 kernel. When trying to boot it the system hangs. Caps lock is still working, but no boot activity seems to occour. Crtl-shift-del can be used to make a soft reset. After the reset the next boot attempt shows a screen indicating a degraded RAID with the option to boot it in this state. After commencing the process by confirming to boot the degraded array the system starts fast and flawless. The file /proc/mdstat shows no signs of a degraded array. No signs of error are shown in the messages log.

Any ideas about the reason of the initial boot fail? Any hints how to track down the cause?

BTW. I'm using grub2.

Thanks

dolittle

---

### Post by Gideon Eisenstadter on 2011-10-18
_Dolittle_,

Have you found a solution yet?  If so, it might help me.

You might be hitting either [Bug #802626]("https://bugs.launchpad.net/ubuntu/oneiric/+source/udev/+bug/802626"), or something similar.  Maybe it's worth keeping the "heat" up on that bug.

I have a similar problem that

[LIST=1]
[*]*does* involve LVs not becoming available;
[*]*doesn't* involve RAID; but
[*]*appears* to be sensitive to the filesystem types of the LVs.  (In my case, substituting ext4 for ext2 appears to ameliorate the problem, so I wonder if the problem is timing-sensitive.)
[/LIST]
I'm able to manually issue a few[INDENT][FONT=Courier New]lvchange -a y ...
mount ...[/FONT]
[/INDENT]and get my system booted.

---

### Post by guiclaw on 2012-01-17
Hi,
Did either of you ever find a fix for this? I've been having the same issues exactly recently and it's very annoying to have to plug a keyboard in to boot! I've also noticed that upon logging init says that my RAID LVM volume will be checked for errors at next reboot but it never does, and fscking my volumes hasn't helped either.

Cheers

---

### Post by _dolittle_ on 2012-01-19
Hi guiclaw,
unfortunately I was not able to overcome this bug. Therefore I went back to ubuntu 10.04 LTS. May be I'll try 12.04 LTS as soon as it's available. But this time I'll make a backup :-\".

Sorry that I'm not able to help you more.

dolittle

---


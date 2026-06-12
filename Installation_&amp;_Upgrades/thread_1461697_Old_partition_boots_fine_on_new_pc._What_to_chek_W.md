---
title: "Old partition boots fine on new pc. What to chek? What should have broken?"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by alias_knagg on 2010-04-24
Just moved my Karmic installation from one Dell laptop to another and booted right up. Pretty happy about that :) 
Synopsis of steps:
Boot old laptop from cd. Connect new laptop disk using usb. Partition in gparted, then copy paste Karmic partition.
[Fix grub using chroot, grub-install, update-grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Preparing Your Working Environment")
Put disk back. Boot. Joy :)
Freeze up swapping a few times. Fix uuid for swap in fstab.

I expect sound is broken, but so is the soundcard, so I haven't bothered looking into that. 

Only problem I am aware of right now is some crazy font and frame size problem making Emacs unusable. I figure it must be somehow related to X, but no clue so far.

Now the question is, what else *should* have broken?
What should I check? There must surely be more hardware dependency than this? Suspend resume and wifi just worked.

Kind of hard to find the right terms to google to zero in on this particular situation, so I'm happy for any pointers.

Thanks.

---

### Post by srs5694 on 2010-04-24
Unless you customize it by building your own kernel with a restricted set of hardware options, Linux is much less sensitive to changes in its hardware than is Windows. Most drivers are part of the kernel, and most distributions install every driver that's even remotely likely to be used, so when you moved your install, everything would just keep working, aside from a few quirks like the ones you found.

One issue you may run into is that some devices may have changed names. For instance, /dev/dvd is normally your DVD drive; but when you switched hardware, it might have changed from /dev/dvd to /dev/dvd0 or /dev/dvd1. This probably won't affect anything in terms of usability unless you've got an application hard-coded to use /dev/dvd, in which case it might break. (Something like this could be the cause of your audio problems.)

---

### Post by alias_knagg on 2010-04-24
That's good news and bad news I guess :)
It's not a fluke that it works, but there's no obvious place to look for the cause of my problems either. 

I don't really know if I have any audio problems, as I know from before that the audio hardware is broken.
Just assumed that would be a likely area for problems from some random comment I read :) 

But devices changing numbers.. why is that really?
Something about the order in which they happen to be detected, is it not?
But partition devices are explicitly named I guess.

Hmm.. of course the partition numbering changed as well.
But grep '/dev/sd' -ir /etc/* no relevant hits.

If I had the time I guess the definitive answer could be had by doing a diff for /etc/ for fresh installs on the two laptops..

---

### Post by srs5694 on 2010-04-24
I'm not sure about your emacs font problems. It could be something about the dpi value detected or assumed by X. Try Googling relevant keywords, like "dpi xorg.conf". You could also peruse /etc/X11/xorg.conf; you might stumble across something obvious. (Most modern systems have pretty minimal xorg.conf files, though, since most details are auto-detected.) You might also try posting some screen shots, since your description is a bit vague.

The device numbers change because Ubuntu, like many modern distributions, remembers certain hardware details -- if you've got a FooMatic SuperDVD 1010 and you replace it with a BarDrive DVD-o-Rama 7912, Ubuntu will see that it's changed and give the new drive a slightly different /dev entry name. Sometimes this makes sense, as for USB devices that might be removed and added back on a whim. Other times it's more of a pain, as when you permanently replace a broken DVD drive or transfer your system as you've done. You can affect some of these changes by editing the /etc/udev/rules.d/70-persistent*rules files.

Your partition numbering should *not* have changed, although it's conceivable that the main device could have changed. That is, /dev/sda1 should either be /dev/sda1 or might have changed to partition 1 on some other device (/dev/hda1 or /dev/sdb1, for instance). Ubuntu has moved away from using partition IDs for most purposes, so it's no surprise you didn't find any references in /etc. Instead, Ubuntu uses the partitions' UUID codes. Check in /etc/fstab, for example. Using the UUID codes has the advantage of being more robust against changes in partition numbers caused by partition table changes or moving disk devices around; however, I've seen a few posts from people who've had problems because their partitions' UUID numbers have become mysteriously unreadable. I personally also dislike the UUID codes because they're hard for me as a mere human to parse -- a UUID of d6b00e86-b7c8-4c89-b54a-365343977f9e doesn't tell me anything useful, but /dev/sdb5 does.

---

### Post by alias_knagg on 2010-04-25
> **srs5694 said:**
> I'm not sure about your emacs font problems. It could be something about the dpi value detected or assumed by X. Try Googling relevant keywords, like "dpi xorg.conf". You could also peruse /etc/X11/xorg.conf; you might stumble across something obvious. (Most modern systems have pretty minimal xorg.conf files, though, since most details are auto-detected.) You might also try posting some screen shots, since your description is a bit vague.

Already did that :)
[http://lists.gnu.org/archive/html/help-gnu-emacs/2010-04/msg00266.html](http://lists.gnu.org/archive/html/help-gnu-emacs/2010-04/msg00266.html)
[http://lists.gnu.org/archive/html/help-gnu-emacs/2010-04/msg00269.html](http://lists.gnu.org/archive/html/help-gnu-emacs/2010-04/msg00269.html)
xorg.conf is dead simple, and I'm pretty certain its not really a dpi problem. 
Not to derail this completely into an emacs thread, but here are the screenshots.
If you happen to have a flash of insight I'm of course very happy :)

Started, maximized.
[IMG]http://www.div.org/emacs/Screenshot-emacs@totiki.png[/IMG]
"Restored"
[IMG]http://www.div.org/emacs/Screenshot-emacs@totiki-1.png[/IMG]
Default font saved as 11pt. And similar briefly during startup. 
[IMG]http://www.div.org/emacs/Screenshot-emacs@totiki-2.png[/IMG]

> **srs5694 said:**
> 
The device numbers change because Ubuntu, like many modern distributions, remembers certain hardware details -- if you've got a FooMatic SuperDVD 1010 and you replace it with a BarDrive DVD-o-Rama 7912, Ubuntu will see that it's changed and give the new drive a slightly different /dev entry name. Sometimes this makes sense, as for USB devices that might be removed and added back on a whim. Other times it's more of a pain, as when you permanently replace a broken DVD drive or transfer your system as you've done. You can affect some of these changes by editing the /etc/udev/rules.d/70-persistent*rules files.

Interesting. But hard imagine font or X problems from this :(

> **srs5694 said:**
> 
Your partition numbering should *not* have changed, although it's conceivable that the main device could have changed. 

No no. I changed it!
I copied the partition, not the disk.
The old drive had WinXp and some Dell-restore crap on it, so root was on sda5 and swap on sda6.
On the new drive I made a new swap on sdb1 and copied sda5 to the remaining empty space, which then became sda1 and sda2 when booted. 
I guess that's why root kept it's uuid while I had to update fstab for the swap.
( Yes, I forgot it's better to have swap on the faster spinning outer sectors. )

> **srs5694 said:**
> 
That is, /dev/sda1 should either be /dev/sda1 or might have changed to partition 1 on some other device (/dev/hda1 or /dev/sdb1, for instance). Ubuntu has moved away from using partition IDs for most purposes, so it's no surprise you didn't find any references in /etc. Instead, Ubuntu uses the partitions' UUID codes. Check in /etc/fstab, for example. Using the UUID codes has the advantage of being more robust against changes in partition numbers caused by partition table changes or moving disk devices around; however, I've seen a few posts from people who've had problems because their partitions' UUID numbers have become mysteriously unreadable. I personally also dislike the UUID codes because they're hard for me as a mere human to parse -- a UUID of d6b00e86-b7c8-4c89-b54a-365343977f9e doesn't tell me anything useful, but /dev/sdb5 does.

Precisely. 
Greping etc for uuid yielded a few more hits, but only one obvious error. 
/etc/initramfs-tools/conf.d/resume pointed to the old swap uuid.
Should have thought to grep for that when I had to fix fstab.

All in all I guess I', left to conclude that there's no obvious error sources to pursue "from bottom up", and I should probably concentrate on nailing my problem "from top down" by tracing what emacs is choking on.

Thaks

Gaute

---


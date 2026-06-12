---
title: "Windows partition boot problem"
date: 2005-10-23
forum: Installation &amp; Upgrades
---

### Post by Excom on 2005-10-23
Ok, here's the way my system was before I tried to install Ubuntu:

IDE 0 Master HD:
partition 1 - my primary windows partition, about 130 gigs
partition 2 - another 100 gigs of unused space on this drive
My system is custom built, running Windows XP.

I wanted to install Ubuntu on the second partition and make my machine a duel boot.  I got the point in the install where it asked me to select a parition (because I also have a backup drive on IDE 1 either as master or slave).

At that point, I tried to select the second paritition as being the install directory for Ubuntu; I selected some file system to be installed on this process (without deleting the NTFS partition that had already existed).

Then I got an error, I believe something about not having a destination to install the root or something.  So I went back and tried another file system, and I think I got some sort of error where a file couldn't be installed.  From there, I went back and deleted the secondary paritition and tried to install the new file system fresh.

That failed as well and now I've given up for the time being; I left the installation before it was complele and I just want to be able to log into my Windows partition again.  Whenever I try to boot off of the harddrive, though, it tells me to put the installation disk in (for Ubuntu) and press enter.  I used my Windows XP restore disk to see that the first partition SEEMS to be intact, and the second was being recognized as having some unknown filesystem.

I tried to delete the second partition, but it no longer recognizes the extra space due to the 133 Gig ceiling on pre-SP1 XP systems (there was a HD memory addressing issue on XP prior to SP1 where it would only recognize the first 133 gigs of space - I later fixed this problem by patching some system files with a utility I found on that net that allowed me to see the missing 100 gigs of HD space or so and create that second partition).

So! All of this leads into my question (and I apologize for being lengthy, but not for being thorough):

What do I need to do to get the first partition on my IDE 0 HD to boot?  What do I need to do to remove all traces of Linux so I can boot into XP and just take care of everything else from there?  Is my partition file corrupted somehow or what?  How do I fix this?  A million dollars...er, thanks, to whoever can first help me solve this. ;)

~ ExCom

---

### Post by Jenda on 2005-10-23
Ubuntu ate up your MBR. The Master Boot Record. I do NOT know how to fix it in a way that you end up like before. I can help you, however.

You should install Ubuntu: the problem was that you need to set a mount point for root (/). To do this, when the partitioner pops up during installation, make a new ext3 partition on the 100Gig space (Use as: ext3 journaled fs) and set mount point to "/". It is advisable to create three partitions, though (/, /home and swap). I'd recommend the first, "/", to be about 10 Gigs, swap should be twice the size of your ram (Use as: swap) and the remaining ext3 partition should be as big as possible (Use as: ext3...)(mount point: /home).

---

### Post by Excom on 2005-10-24
Actually, neither the Windows CD nor the Ubuntu CD will recognize my drive past the first 133 gigs because I made the mistake of deleting it via the Windows CD (the CD is XP pre-SP1 so as I said before, I've got the 133 gig ceiling problem) - the only way to proceed from here would be to erase the Windows partition, which I am loathe to do.  But thank you as this will be a great help whenever I next attempt to set up Ubuntu properly (whenever that is).

Anyone have any ideas on how to repair my MBR so I can boot off my Windows partition?

---

### Post by brentoboy on 2005-10-24
I think this is what you are looking for
[http://www.ubuntuforums.org/showthread.php?t=26984](http://www.ubuntuforums.org/showthread.php?t=26984)

---

### Post by jack-78 on 2005-10-24
Hi. Try to use your Windows Restore CD, and there should be an option to repair MBR (Master Boot Record). But better way is: try to finish Ubu instalation and delete Win :-)

---

### Post by Excom on 2005-10-24
Fixmbr? Tried that, it does nothing (well, almost nothing - it prints out a single blank line before returning me to the command prompt).

---

### Post by Excom on 2005-10-24
jack: I don't WANT to delete Windows, the whole idea was to duel boot the system in the first place to preserve what information I already had on there. At this point, I don't care about installing Linux, I just need to get Windows working so I don't lose my files.

Edit: Additional note: The second partition to which I was attempting to install Linux has now been deleted; the only partition I have left on my IDE 0 HD is the original Windows one which I do NOT want to lose.  I need to know how to get the system to recognize that I want Windows to boot and not Linux, which seems to realize its install was incomplete.  Hopefully that will clarify things some.

---

### Post by Jenda on 2005-10-25
In that case, I cannot help you.

---

### Post by leezer3 on 2005-10-25
To get the Windoze boot back, you need to run two things from the recovery console on the Winxp cd-
```
fixboot
fixmbr
```
Run these in this order and you should be fine.

Edit: Oh, you might want to try turning on LBA in your BIOS, as this might fix a few of your problems.

Cheers

-Leezer-

---

### Post by Hugo Bio on 2005-10-25
You can try using Norton's Partition Magic to make a new usable partition AND to activate the first partition as the main one... You just have to right-click it and set active... I think there is a free boot disk download for norton partition magic... if not, PM me, ok?

---


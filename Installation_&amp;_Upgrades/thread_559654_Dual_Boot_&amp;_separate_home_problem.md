---
title: "Dual Boot &amp; separate /home problem"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by flyingsolo on 2007-09-25
I've had a dual boot on my laptop for some time with a small WinXP partition for one essential work application.  I want to change my Ubuntu install to have a separate /home but I've run out of primary partitions available to create the /home.
My question is about the WinXP install which has its ntfs partition but also a very small fat32 partition of ~50MB (not GB!)  Anyone know what this little partition would be?  Can it be 'discarded'?  (I don't recall explicitly creating it when I set this up--just ran the WinXP install disc)  If this can be discarded, then I have another primary partition available to create /home.
Hopefully, that's clear enough & thanks.

---

### Post by rsambuca on 2007-09-25
What is your laptop manufacturer?  Some of the big name laptops have special media keys on them.  Often the files required for those special keys are contained in those mini partitions.  You can delete the partition, but then your media keys won't function properly in Windows.  

I don't suppose you can view the partition files so we could have a little looksee?

---

### Post by dabl on 2007-09-25
rsambuca is right -- that teeny partition is not required by Win XP, it's a "recovery" thing that your laptop builder put on the drive.

My other thought is -- you can use an extended partition, and put multiple logical partitions in it, if that helps. The extended partition has to be one of the 4 primary partitions that you are allowed.

But, it sounds like you're pretty proficient.  Were it me, I'd "FDISK" the whole hard drive (i.e. nuking the "recovery" partition), then install Win XP in one partition (and do that first), and then use the balance of 3 primary partitions for "/", "/home", and "swap".

:)

---

### Post by elsaturnino on 2007-09-25
If it's a dell, then it's probably the recovery or utility partition they put on all their computers. You can safely delete those (I just did that yesterday, in fact :) ).

---

### Post by flyingsolo on 2007-09-25
Thanks all of you for your help.  I posted that question earlier today at work but didn't get back 'til now.  In the meantime, I figured it out and, yes, you're all correct--it is a Dell Utility package.  I'll be getting rid of that shortly & be able **_[COLOR="DarkSlateBlue"]to do what I want[/COLOR]_** with this computer!

@dabl:  By the way, your suggestion of totally formatting the disk is what I did when I received it new, to remove crap-ware and only install WinXP but since it is a Dell branded install disc I have, the Dell utility partition gets installed as well.  I remember trying to get a separate /home then as well but didn't figure out the problem was a result of the extra partition consumed by Dell themselves!  As long as XP still works without the Dell Utility partition, I think I'll just remove it with gparted and carry on.

---


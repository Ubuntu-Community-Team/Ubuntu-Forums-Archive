---
title: "Ubuntu &amp; Windows Vista"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by Th3Professor on 2008-04-30
I'm about to set up a laptop to work with both Ubuntu Studio and Windows Vista.
 
Should I install Vista first? (And will it let me set up partitions?)

---

### Post by Dougie187 on 2008-04-30
Usually when I install windows. I install windows first. And i dont set up the partitions in it. I just make one partition with the space for windows and leave everything else blank. Then I use the ubuntu installer to make both my swap and my root installation. I have found that installing windows last messes up grub, so grub was my reason for installing windows first. Though I guess if you wanted to use windows chain loader thing, you could install it in any order. Theoretically it should work in either order, but its up to you how you want to do it.

---

### Post by Th3Professor on 2008-04-30
Are you talking about Windows XP or Windows Vista?
 
This laptop has Vista right now and it appears to have a different approach towards system management, pretty restrictive, so I'm not sure if the install CDs will cooperate with a *nix install.
 
The CDs that came with the laptop, by the way, are:
"Toshiba Recovery and Applications/Drivers - Windows Vista Home...etc."
Since it says Vista, I'm hoping it actually does allow for a Vista reinstall.
 
What's the minimum hard drive space required for Vista?
 
It's only a 160 GB hard drive.

---

### Post by Dougie187 on 2008-04-30
I would allow at least 20 gigs for your vista. But since you have to use the restore cd, I would install linux first. just to set up partitions. And then try to use the restore cd on one of the partitions. but i dont know how it will work out for you. But I have done this with both Vista and XP

---

### Post by Th3Professor on 2008-04-30
20 gigs! WOW! Sheesh... that's crazy.
I noticed that the default install, right now, uses almost 18gigs, so that makes sense.
 
But that's just overkill for *just* an operating system to require 20 gigs.
 
I don't know, I might just go back to XP so I can do an 8 gig partition and have the additional gigs set aside for *nix. :)

---

### Post by Dougie187 on 2008-04-30
Id think you would want to use xp over vista any day personally. heh. So it might be better to go back to xp anyways.

---

### Post by Th3Professor on 2008-04-30
before i do this... does ubuntu work on intel centrino?

---

### Post by Dougie187 on 2008-04-30
Yeah. thats what my laptop was.

---

### Post by Th3Professor on 2008-04-30
Cool beans. :)

---

### Post by madrobber23 on 2008-04-30
I am currently doing the exact opposite of the person above...eliminating vista from my ubuntu/vista duel-boot. What is the first step? Is there a location where I can find written, linear instructions?

-Evan

---

### Post by Dougie187 on 2008-04-30
I dont know about written linear instructions. But you can just use gparted to clean out your windows, and then resize your ubuntu to the full size.

---

### Post by Th3Professor on 2008-04-30
If you want Vista back in the future make sure you have the install CDs/DVD. I decided to go with XP on a small partition and just throw out Vista all together, though before doing that I tested the CDs that came with the laptop (Windows Vista CDs) and they actually are *not* operating system (Vista) install CDs, they are only for recovering back-up data.

Actually, if anybody is familiar with the:
"Toshiba Recovery and Applications/Drivers: Satellite A200 Series: Windows Vista Home Premium 32-bit SP1" CDs
...that come with Toshiba laptops, and if you know that they do in fact offer for re-installing Vista from scratch (and are not just used for recovering back-up files), it'd be good to know if they do that. I didn't see anything related to fresh OS install on them.

If Vista used less hard drive space I'd probably use it as my left-over partition other than XP. Vista's otherwise too "fat".

---

### Post by Dougie187 on 2008-04-30
The toshiba things allow you to restore a partition. So it doesnt have to be the entire drive. Just for future reference.

---

### Post by Rallg on 2008-04-30
On my previous computer, the Windows XP validation key was somehow linked to where the Windows partition started on the hard drive. After I moved the starting point of the Windows partition, I had to fix the Windows bootloader, then get a new validation code by calling Microsoft.

I don't know if it works that way for Vista, but I imagine it does.

Probably the validation had something to do with the fact that Windows came pre-installed with the computer, so it did not like being moved. Your results may differ. Changing the Windows partition size, by moving its end point, was not a problem.

---

### Post by Dougie187 on 2008-04-30
That would be a vendor specific method though. My toshiba didn't have that same issue. What brand of comptuer did you have. Also, I should mention. I have 2 toshiba laptops. and My parents have 3, and my brothers both have 2 as well. And none of them have this issue. 

But if you have a single use XP license you may have to call before you can reinstall. Toshiba's use ghost to reinstall your computer and it uses some sort of license key that just works when you restore.

---


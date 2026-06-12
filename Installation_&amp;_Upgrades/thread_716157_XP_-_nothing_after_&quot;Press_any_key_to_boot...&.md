---
title: "XP - nothing after &quot;Press any key to boot...&quot;"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by noah420 on 2008-03-05
Firstly, sorry if this is the wrong category for this post, I don't know how to categorize it. Searched posts using and didn't bring up any similar results

I am trying to install Windows XP Home SP1a as dualboot, by replacing the current version of windows on the computer (Gutsy Gibbon and Windows XP Home SP2 installed currently) but after "Press any key to boot from cd..." nothing happens.

I am sure the disc is good as I just used it (after trying on this computer) on another one and it worked fine. Ubuntu was installed after Windows XP was installed the first time I did it, however I do not want to uninstalled Ubuntu the install windows, and reinstall Ubuntu, as it was a pain to get the wifi working and I don't know how I did it. I am pretty sure it is a problem with Ubuntu, as the other computer I did it on only had windows xp sp2 on it. (It is not a pirated disk)

Thanks

---

### Post by Kerin on 2008-03-06
Pretty simple, actually - Windows won't boot the installer if it's attached to a volume with Linux on it.  It's some screwed up anti-competitive measure, I believe - you might need to do something radical like use your Ubuntu LiveCD to partition the drive non-destructively and create a NTFS primary partition before using the Windows CD.

---

### Post by noah420 on 2008-03-07
Okay, I used GParted to delete the old NTFS and create a new one as primary (first partition on drive) and it still does the same thing. Is this because when I setup Ubuntu I set ext3 as  Primary as well? Can I change it to logical (I believe that was the other option) without deleting all the files in linux? If so, how do I do that, as I did not see an option for it in GParted. I appreciate the help, and hope I can figure this out without having to completely annihilate linux. I like it so much now that I got my WiFi working on it. :P

P.S. The only reason I need Windows is to run Nobeltec Admiral (the navigation software I use on my boats) as it simply will not run on linux with wine. That is also the reason I am downgrading from SP2 to SP1 because SP2 interferes with the uhh.... "borrowed" software.

---

### Post by noah420 on 2008-03-09
bump

---

### Post by noah420 on 2008-03-16
any ideas?

---


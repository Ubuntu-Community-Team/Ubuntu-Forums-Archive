---
title: "Why does 10.10 installation have 'Swap Area' configuration?!TAT"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by lifeicd on 2010-10-12
I was so excited that finally I can get the newest version of Ubuntu installed on my computer. Yesterday I downloaded the iso file and emptied my F:/ disk, hoping I can install it this morning. 

Everything was perfect until I met 'swap area'. I thought it was just that the installing program needed some free space during the process. Storage hierarchy, caching, something like that. So I configured my E:/ disk as the 'swap area'. 

Bad decision! After everything was done, I rebooted ubuntu, only finding that my E:/ no longer existed!!!! I couldn't believe my eyes, so I rebooted back to Win7. E:/ disk wasn't there any more!  Now I have to accept the bitter truth. All my journals, photos, and documents are ruined.     

My point is that: if something like 'swap area' is not so common sense to everybody, why does it have to be there? And if it will format that disk, why aren't I noticed?     

Not so long ago, I heard some one claimed that the ubuntu10.10 installing process would be revolutionized, much more user-friendly. Well, this is not what I've expected.

---

### Post by prshah on 2010-10-12
> **lifeicd said:**
> Now I have to accept the bitter truth. All my journals, photos, and documents are ruined.

Actually, you may be able to recover quite a bit if you haven't used the "e: drive / swap area" much. Use TestDisk / Photorec from one of the live CDs listed [here]("http://www.cgsecurity.org/wiki/TestDisk_Livecd")

I suggest it's better you download and burn the liveCD from elsewhere (ie, not from your affected computer).

Also, when you boot into the live CD please turn OFF swap usage (eg, by using the root terminal command "swapoff -a")

From what you describe, I think you have a WUBI install; in which case, the chances are all the more greater that stuff can be recovered (esp using PhotoDisk). The downside is that all the filenames will be wiped out; you will have to manually go through all the files to figure out what is what.

I don't know anything about your complaint though; I have always found that the installer warns me about any and every potential data loss activity.

---

### Post by lifeicd on 2010-10-12
Thanks for the tips. I got most of the important stuff back. 

> I have always found that the installer warns me about any and every potential data loss activity.

Well, experts(or senior users) must assume that something like 'swap area' is just common sense. They don't even need any warning actually. But, for someone like me, only wanting to trying something new, this is painful. 

Ubuntu is great, but it CAN be improved in details, especially the INSTALLER.

---


---
title: "Am I running 4gigs of RAM or 6?"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by Fooshnik on 2010-02-25
Using Ubuntu 8.04 Server I noticed it was running Zimbra damn slow with 2gigs of RAM. My intention was to upgrade it to 4 gigs RAM, as I'm running the 32bit kernel and assumed there would be no point in adding any more. I added two more DIMMs, they're mismatched with the existing but sometimes I get away with this by putting the slower DIMMs in the lower numbered slots. This appears to have worked, the comp posted and started fine. 

I wanted to run a memtest since mismatching RAM is inviting failure. However when I ran TOP, it showed I have 6.143 Gigs of RAM. Evidently I didn't read the label closely on the DIMMs I added, I added (2) 2gig DIMMs instead of (2) 1gig, for a total of 6gig. My question that I'm taking a long time getting to is, since I'm running an i686 kernel, why am I seeing 6gigs RAM? Top shows 6gigs, so does Webmin, I'm running Memtest86 now off the Ubuntu CD, it shows "Memory: 6134M", "Testing: 120K - 3071M" followed by "Testing: 4096M - 6144M".

Why am I seeing this box running 6 gigs with the 32-bit kernel? I didn't intentionally install PAE or anything else.

---

### Post by marshmallow1304 on 2010-02-25
I do believe that the server kernel has PAE.

---


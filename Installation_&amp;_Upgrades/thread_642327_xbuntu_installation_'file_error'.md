---
title: "xbuntu installation 'file error'"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by licorice_sticks on 2007-12-16
Hello! I'm as n00b as they get. 

I got a virus on my XP (no way.) and decided that it was time to go into the whole Ubuntu OS lifestyle. I had some copies of Ubuntu 5.10 around but when I tried to install them, i got the same 'intrid' file error. 'something/bootstrap.log' couldn't install and thus the whole base system could not install. A long time ago, I installed Ubuntu to try it out and it worked before so I thought it was my hardware that was messed up. 

I decided to install windows xp again. After installing windows, I went on the net and got xbuntu (that was what I was going to eventually install anyway). i did the whole hash-check after downloading the iso and i copied it onto a cd. however, when i was ready to install the sucker, it wouldn't work. the loading screen with that blue bar was all that i saw. so after restarting several times, i had xbuntu do a check of the cd. it said there was one file error. 

now i am about to download xbuntu again and put it on a cd and doing it all over again. i doubt i will be able to install it however because i have tried to install ubuntu and xbuntu several times now. i might have to stick to XP even though i don't really want to.

what's going on?

---

### Post by mikewhatever on 2007-12-16
1. Download over bittorrent if you can to avoid hash errors.

2. If you have to download over ftp/http, run md5sum check on the iso before burning [https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29](https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29).

3. Use a good quality CD and adjust the burning speed to max x4 [https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28iso%29)

---

### Post by licorice_sticks on 2007-12-16
> **mikewhatever said:**
> 
3. Use a good quality CD and adjust the burning speed to max x4 [https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28iso%29)

Thanks mikewhatever! I should have read your comment before I messed around with everything, but I got it to work! Hooray! It was because the burning speed was too fast, just as you said. I got it to install and everything so xbuntu works on my computer without the live CD, however it's unbelievably slow. Is this due to partitioning? Do you know?

---

### Post by mikewhatever on 2007-12-16
> **licorice_sticks said:**
> Thanks mikewhatever! I should have read your comment before I messed around with everything, but I got it to work! Hooray! It was because the burning speed was too fast, just as you said. I got it to install and everything so xbuntu works on my computer without the live CD, however it's unbelievably slow. Is this due to partitioning? Do you know?

What are the specs of the computer (CPU, RAM, graphics)? Do you suspect something is wrong with partitions? What partitions do you have? How large is the swap?

---


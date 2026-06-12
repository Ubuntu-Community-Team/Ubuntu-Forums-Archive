---
title: "GROW RAID 5 error: resize2fs memory allocation failed"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by zac_haryy on 2008-08-19
I am trying to grow my RAID 5 and running into one problem. This is the guide that I am following [HTML]http://scotgate.org/?p=107[/HTML] and I am having problems with this part:
```
resize2fs /dev/md1
```
When I run this it runs for like 30-45 minutes and it gives me this error:
```
resize2fs memory allocation failed while trying to resize /dev/md0
```
Then I try to remount and the RAID is still the old size. I have no idea what to do and I cannot find anything on the net about this at all besides a little chat (it appears to be) and there is nothing helpful in there about this. If anybody knows what I could do please help, thanks!

-haryy

---

### Post by zac_haryy on 2008-08-19
I dont know if this matters or not but this a 8tb hard drives. If there is some size limitation or something.

---

### Post by zac_haryy on 2008-08-25
Still have not founs a solution for this. Is there different programs that I could use that would resize evertyhing for me?

---

### Post by zac_haryy on 2008-08-29
Still have not clue what I can do to fix this...If anybody has anything please help me out!

---

### Post by ormeskirk on 2010-07-09
I don't know if you found an answer, but just in case.  I solved this problem by increasing my swap file size.  For some reason i actually did not have a swap file.

I used this site: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---


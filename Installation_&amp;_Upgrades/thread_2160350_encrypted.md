---
title: "encrypted"
date: 2013-07-06
forum: Installation &amp; Upgrades
---

### Post by scarrabri on 2013-07-06
Hi when i installed lubuntu  which was the latest one i had trouble with the  encrypted part as it would not let me enter all the pass phase in before timing itself out ,im not sure why this was ,but i only got half of my pass phase in and now i am not sure if any thing is  encrypted and should i have to do a complete re stall knowing that i may have the same problem ,i hasten to add i not that well up on ubuntu  code writing or entering it lol

---

### Post by Bashtard on 2013-07-06
```
sudo ls -lA /home/bashtard/
``` will tell you. Replace "bashtard" with your user name. If the output includes ```
ecryptfs
``` then it is encrypted. You might have to run this from a live cd as the user can't be logged in for it to work.

---

### Post by scarrabri on 2013-07-07
> **Bashtard said:**
> ```
sudo ls -lA /home/bashtard/
``` will tell you. Replace "bashtard" with your user name. If the output includes ```
ecryptfs
``` then it is encrypted. You might have to run this from a live cd as the user can't be logged in for it to work.
  Hi thanks very much for your help i will go have a go thanks again

---


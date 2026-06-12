---
title: "Upgrade from 8.04 to 9.10 direct"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by swaprava on 2010-01-22
I saw there is a way of 8.04 to 8.10 to 9.04 to 9.10, but it's a long detour. Can anybody suggest a better way of upgrading from 8.04 to 9.10?

thanks in advance

---

### Post by myth1914 on 2010-01-22
If it's not pressing, there will be a direct path from LTS to LTS if you can wait until sometime in April.  Unfortunately, I recently wanted to do the same and found that the safest path is still the longest.

Looking back, without reinstalling, all went well.  The only issues I had were a few of my htaccess passwords getting wiped and 1 samba share I had to re-export.

BTW, it's fairly painless.  I upgraded 8.04 to 9.10 on 4 separate machines and had them all back to normal in about 5 hours including the babysitting/wait time.

---

### Post by drs305 on 2010-01-22
Upgrading from 8.04 to 10.04 should be fairly easy, as they are both LTS (long term support) versions. Here is a link on Lucid:
[http://www.ubuntu.com/testing/lucid/alpha2#Upgrading%20from%20Ubuntu%209.10%20or%20Ubuntu%208.04%20LTS]("http://www.ubuntu.com/testing/lucid/alpha2#Upgrading%20from%20Ubuntu%209.10%20or%20Ubuntu%208.04%20LTS")

The command to update from 8.04 is 
```
sudo update-manager -d
``` 

HOWEVER:
Updating your normal machine to an Alpha release is probably not something you should do yet. Although Lucid testing is going well, it is still being developed. If you have been using a LTS version of Ubuntu, it would be a fair guess to think you are not anxious to be on the 'cutting edge'. You might want to wait until Lucid is released in April or at least until it gets later into the testing cycle.

---

### Post by snowpine on 2010-01-22
1. Back up data
2. Burn 9.10 Live CD
3. Install 9.10
4. Restore data from backup

---


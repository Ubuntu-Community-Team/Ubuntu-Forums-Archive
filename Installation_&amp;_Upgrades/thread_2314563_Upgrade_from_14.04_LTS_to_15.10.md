---
title: "Upgrade from 14.04 LTS to 15.10"
date: 2016-02-22
forum: Installation &amp; Upgrades
---

### Post by rob161 on 2016-02-22
All,

Following the directions on step 2 on the Ubuntu site, [http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade), I was unable to upgrade from 14.04 LTS to 15.10. Every post pointed to doing an incremental upgrade 14.04 to 14.10. 14.10 to 15.04. Too much. I kept getting the same message, System updated. Finally, I opened the terminal and then typed in "update-manager" the system then ran a search and then read system updated, do you want to upgrade? First time I ever seen this. I typed Y for yes. The upgrade started and then returned a core error. I typed in "update-manager" again in the terminal. Again, it ran a check, replied system updated, do you want to upgrade? Again I typed Y. Now my system is at 15.10 and running fine. This may work for you if you are stuck at 14.04. good luck

---

### Post by justen_m on 2016-02-22
Maybe try...
update-manager -d

It updated my 15.10 systems to 16.04 dev release.

---

### Post by kansasnoob on 2016-02-22
> **justen_m said:**
> Maybe try...
update-manager -d

It updated my 15.10 systems to 16.04 dev release.

But most casual users should NOT be using a development version!

---

### Post by grahammechanical on 2016-02-22
We have had several posts on this forum from people who are making the jump from 14.04 to 15.10 and some even mistakenly jumping to 16.04 while it is still in its development period and risking a broken system in the process. So, for those who do not know.

Ubuntu 16.04 will be released at the end of April this year. And users of both 14.04 and 15.10 will be notified of the release and prompted to upgrade to it. Users of 14.04 can decline if they want to as 14.04 will still have 3 years of support left to it. But users of 15.10 will need to upgrade to 16.04 before 15.10 reaches end of life in July.

The ability to upgrade directly from 14.04 to 15.10 is a new feature. I have never tried it myself. Not even as a test to see how it works. So, those who are making use of this new feature are gaining useful experience that can be used to advise others.

Regards

---


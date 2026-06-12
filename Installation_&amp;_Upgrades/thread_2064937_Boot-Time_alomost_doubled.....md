---
title: "Boot-Time alomost doubled...."
date: 2012-09-30
forum: Installation &amp; Upgrades
---

### Post by satyamM on 2012-09-30
Recently I upgraded to 12.04 from 10.04....!!!

In 10.04 the boot time was was very less that I instantly became fan of Ubuntu.

But now I have upgraded to 12.04, the boot time has almost doubled. [B]After choosing the option at grub menu, it takes 15-20 seconds to appear a black screen, then Ubuntu Violet Screen takes sometime to come and go, then my screen brightness goes back to what I had set earlier, then after 15-20 seconds my  Desktop appears...
[/B]
What could have happened to 12.04? Has the boot-time been increased by Ubuntu in 12.04?

Somebody please help.

---

### Post by cwsnyder on 2012-09-30
Yes, the boot time into a working desktop has increased since 10.04 because the Unity desktop is doing a lot more at bootup.  Try Xubuntu or Lubuntu for a quick boot.

---

### Post by satyamM on 2012-09-30
But that is NOT good at all......Boot-Time is a very imp. feature in any operating system, and almost everyone hates waiting for Desktop to appear, not only few..

But Unity plug-in is quite good, so may be few people may compromise on that.....

Any tips/tricks to check my boot time and how can I decrease it with Unity plugin enabled in the system...

---

### Post by darkod on 2012-09-30
In the boot menu, you can hit 'e' for edit when the ubuntu entry is highlighted and remove the 'quiet splash' at the end. Then press Ctrl + X or F10 to boot.

This is only a one time change (all will be the same at next boot) and it will show the text during boot so you can see if it gets stuck at some particular point.

If you have only ubuntu and are not getting a boot menu, hold Shift when booting to show it.

---


---
title: "RAID dual boot question"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by ryanfx on 2007-10-15
Hey all,

I was wondering if there was any way to have a dual boot raid 5 setup with three 500GB's, using 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131073](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131073)

that mobo.

ASUS's site only has drivers for windows.  Is there any way to have a complete raid 5 solution for dual booting ubuntu / windows?

Thank you.

---

### Post by ryanfx on 2007-10-16
bump!!

---

### Post by Pumalite on 2007-10-16
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by ryanfx on 2007-10-16
is there a reason to do fakeRaid over LVM?

---

### Post by Pumalite on 2007-10-16
No, I just wanted to make you aware of this link.

---

### Post by ryanfx on 2007-10-16
if my motherboard supports "hardware raid", and I want to dual boot with vista, which form would you recommend of the two?

---

### Post by Pumalite on 2007-10-16
Sorry, but I have never used LVM; so, I don't feel qualified. Some Forum Staff will come around and answer your question.

---

### Post by pjman on 2007-10-18
I've never used LVM either... Currently I'm setup with a dual-boot and fakeraid (dmraid) 1 mirror. I believe if your motherboard handles actual hardware RAID you wont need either since Ubuntu should just see it as another drive. According to the newegg link, that mobo uses NV RAID, same thing I have which is actually software raid :-( 

I could be wrong but I don't think you can setup a dual-boot with LVM so dmraid is probably your only choice.. This thread helped me out: 

Successful and "easy" install DUALBOOT FeistyFawn/XP with nvdia raid0 stripeset
[http://ubuntuforums.org/showthread.php?t=464758](http://ubuntuforums.org/showthread.php?t=464758)

---


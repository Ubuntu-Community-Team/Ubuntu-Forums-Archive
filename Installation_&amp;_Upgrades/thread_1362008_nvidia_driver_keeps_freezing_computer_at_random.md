---
title: "nvidia driver keeps freezing computer at random"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by MightyMe on 2009-12-22
After upgrade my screen keeps freezing at random intervals. It has been working for some weeks and now it suddenly stops working. Even the login screen is invisible or partly visible after reboot.

After several reboots, it may suddenly correct itself and the computer works for a little while before the next freeze. I have rebooted in "safe mode" and logged in as root and renamed/removed xorg.conf (which seems to be put there after installing the drivers). This solves the problem partly in the sense that I now have a graphic interface but with the wrong resolution, fuzzy fonts etc.

I have never had these kind of problems before in previous releases. Anyone have any asuggestions before i revert to Jaunty? Any help would be appreciated.

---

### Post by phillw on 2009-12-22
Hi,

have a read thru' the sticky at the top of this page - I think they cover just about every eventuality for both nvid & ati graphics.

Regards,

Phill.

---

### Post by MightyMe on 2009-12-22
Ok, thanks. Updated the driver to the 190 version. Hope this helps. So far so good.

---

### Post by MightyMe on 2009-12-30
After a few days of testing, the new driver did not fix things. Comp is still freezing on me at random. I dont know what it is, but the combination of kernel versions ,9.10 and nvidia drivers just doesnt work on my computer which never has had any such problems since 7.04. 

So I did what I should have done in the first place - revert to 9.04. Works like a charm. 9.10 was just not for me it seems. I hope 10.4 will be a better release.

---


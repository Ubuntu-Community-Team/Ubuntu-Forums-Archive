---
title: "My problem on linux and Ubuntu"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by limoral on 2007-09-26
I wanna bought a new laptop but I have known that it will use another style of linux but not ubuntu.
Now my question is: if I decide to buy the laptop, what will I do to delete the original linux OS and instal the new Ubuntu OS?

&#25105;&#24819;&#35201;&#20080;&#19968;&#21488;&#26032;&#30340;&#31508;&#35760;&#26412;&#30005;&#33041;,&#20294;&#26159;&#25105;&#30693;&#36947;&#23427;&#23558;&#39044;&#35013;&#20854;&#20182;&#31867;&#22411;&#30340;linux&#25805;&#20316;&#31995;&#32479;&#32780;&#38750;&#37030;&#22303;&#31995;&#32479;&#12290;
&#25105;&#30340;&#38382;&#39064;&#26159;:&#22914;&#26524;&#25105;&#20915;&#23450;&#20102;&#20080;&#36825;&#21488;&#30005;&#33041;,&#24590;&#20040;&#20570;&#25165;&#33021;&#21024;&#38500;&#25481;&#21407;&#22987;&#30340;Linux&#31995;&#32479;&#24182;&#19988;&#23433;&#35013;&#25104;&#21151;&#37030;&#22303;&#31995;&#32479;?

---

### Post by Wim Sturkenboom on 2007-09-26
Just install it; somewhere during the installation you can partition your HD and that will wipe the previous OS of the box if you do it correctly.

---

### Post by dabl on 2007-09-26
Boot GParted Live CD and use it to delete all partitions and filesystems on the hard drive.  Then make new partitions and format them (ext3 or reiserfs, except for swap).  Download ISO for GParted Live CD from here:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

When hard drive is ready, then boot Ubuntu Alternate Install CD, and use it to install Linux.

:)

---


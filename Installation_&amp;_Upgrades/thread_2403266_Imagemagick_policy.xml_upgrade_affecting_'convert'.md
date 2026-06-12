---
title: "Imagemagick policy.xml upgrade affecting 'convert' to pdf"
date: 2018-10-09
forum: Installation &amp; Upgrades
---

### Post by moray-jones on 2018-10-09
I just upgraded to 18.04 recently and then tried to use a script I have that includes a convert command (which is part of Imagemagick).

The command was no longer working. It looks like a later version of Imagemagick has some security upgrades in a file called policy.xml which includes messing up my pdf conversions.

Found this answer: [https://askubuntu.com/questions/1081895/trouble-with-batch-conversion-of-png-tp-pdf](https://askubuntu.com/questions/1081895/trouble-with-batch-conversion-of-png-tp-pdf)

Posting it here in case anyone has done an upgrade and is looking here instead of there.

(summary: rename the file to something else which removes all security provisions or comment out the pdf line)

---

### Post by deadflowr on 2018-10-09
It would affect any other version on any supported release of Ubuntu as well.
It's part of this security fix:
[https://usn.ubuntu.com/3785-1/]("https://usn.ubuntu.com/3785-1/")
There was a somewhat related thread here:
[https://ubuntuforums.org/showthread.php?t=2400606]("https://ubuntuforums.org/showthread.php?t=2400606")

It is nice that it is more of a soft fix and not like a hard fix.
Where the fix would not be reversible.

---


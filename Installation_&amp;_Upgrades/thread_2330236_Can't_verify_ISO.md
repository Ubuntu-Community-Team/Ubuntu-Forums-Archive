---
title: "Can't verify ISO"
date: 2016-07-09
forum: Installation &amp; Upgrades
---

### Post by jhenager on 2016-07-09
Following the instructions on the site for verifying the download.

fx-5300@fx5300-desktop:~$ gpg --keyserver hkp://keyserver.ubuntu.com --recv-keys "8439 38DF 228D 22F7 B374 2BC0 D94A A3F0 EFE2 1092" "C598 6B4F 1257 FFA8 6632 CBA7 4618 1433 FBB7 5451"
gpg: "8439 38DF 228D 22F7 B374 2BC0 D94A A3F0 EFE2 1092" not a key ID: skipping
gpg: "C598 6B4F 1257 FFA8 6632 CBA7 4618 1433 FBB7 5451" not a key ID: skipping

---

### Post by Bashing-om on 2016-07-09
jhenagerl Hello;

What platform are you working from ?
There are easier ways to verify the .iso file:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

[INDENT][INDENT]many paths to and end
[INDENT][INDENT][INDENT]choose what suits the best
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ubfan1 on 2016-07-09
What instructions are you following?  Those are not key ids, should look something like:
gpg --keyserver hkp://keyserver.ubuntu.com --recv-keys 0xFBB75451 0xEFE21092

---

### Post by jhenager on 2016-07-09
These instructions were from the Ubuntu site and I always copy/paste. I wondered why they didn't just do md5, but Bashing-om has answered my question. Problem is, the hash matches, and so far, trying from USB and burning to DVD, I can't even get 16.04 to boot on the computer I am currently typing on, which is about a year old. I'll keep troubleshooting it, but at this rate, I might as well go back to M$. I left windoze because of this kind of crap - just trying to do something simple, and getting mired down in installing/configuring until I forgot what I was originally trying to do.

---


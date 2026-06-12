---
title: "Ubuntu 19.04 won't boot with Nvidia proprietary drivers (418)"
date: 2019-04-21
forum: Installation &amp; Upgrades
---

### Post by boruno on 2019-04-21
[COLOR=#242729][FONT=Arial][FONT=inherit][FONT=inherit][COLOR=#242729][FONT=inherit]I upgraded today from 18.04 to 19.04, and after the installation my system refused to boot (it was stuck on that black screen with the green [ok] lines). I then installed it without the third party extras, and it booted normally, but as soon as I installed the most recent nvidia drivers from the software & updates menu, it refused to boot again. Right now i'm using the nouveau drivers without problems, but I still want to update them to be able to play my games. How can I solve this problem? 
My GPU is a GTX 1060 6GB.
 Thanks in advance[/FONT][/COLOR][/FONT][/FONT][/FONT][/COLOR][FONT=Arial][FONT=inherit]
[/FONT]
[/FONT]

---

### Post by cruzer001 on 2019-04-22
Could you be running wayland and need to switch to xorg?

[https://www.google.com/search?client=firefox-b-1-e&ei=_9y9XM-HC5XN-gTq1L3wAw&q=ubuntu+18.04+switch+from+wayland+to+xorg&oq=ubuntu+wayland+to+xorg&gs_l=psy-ab.1.0.0i7i30l3j0i8i30.34314.36874..41658...0.0..0.171.1102.0j7......0....1..gws-wiz.......0i71j0i8i7i30.SOpi65ZKXko](https://www.google.com/search?client=firefox-b-1-e&ei=_9y9XM-HC5XN-gTq1L3wAw&q=ubuntu+18.04+switch+from+wayland+to+xorg&oq=ubuntu+wayland+to+xorg&gs_l=psy-ab.1.0.0i7i30l3j0i8i30.34314.36874..41658...0.0..0.171.1102.0j7......0....1..gws-wiz.......0i71j0i8i7i30.SOpi65ZKXko)

---

### Post by hgkrug1 on 2019-05-23
I have encountered the same issue.  I have seen some solution at [https://ubuntuforums.org/showthread.php?t=2392117&highlight=problem+nvidia+drivers](https://ubuntuforums.org/showthread.php?t=2392117&highlight=problem+nvidia+drivers) that seems to make most sense.

Unfortunately the description is a bit vague and I am not able to follow it.

I have found 2 solution on restoring the Ubuntu desktop when that happens (without fixing the nvidiainstall issue).  See  entry #17 at [https://ubuntuforums.org/showthread.php?t=2411777&page=2](https://ubuntuforums.org/showthread.php?t=2411777&page=2)

---

### Post by hgkrug1 on 2019-05-23
I eventually found a solution for this Nvidia driver issue (on ubuntu 18 and 19). See instructions at the top at [https://ubuntuforums.org/showthread....nvidia+drivers]("https://ubuntuforums.org/showthread.php?t=2419319&highlight=nvidia+drivers"), it worked for me!

Unfortunately, I could not reproduce the installation on a freshly installed system.

However, I found a suitable fix at entry #19 of [https://bugs.launchpad.net/gdm/+bug/1798790](https://bugs.launchpad.net/gdm/+bug/1798790)

Try this as a workaround: edit /etc/gdm3/custom.conf 
and uncomment the line: 
#WaylandEnable=false

---

### Post by scpatl4now on 2019-05-27
I had this problem and this fixed it.  You have to uncomment Wayland=false

 sudo gedit /etc/gdm3/custom.conf

Change the statement

#Wayland=false
Wayland=false

I have had 3 boots without issue since I did that

---


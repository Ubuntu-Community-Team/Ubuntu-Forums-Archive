---
title: "Weird problem with Firefox"
date: 2006-06-25
forum: Installation &amp; Upgrades
---

### Post by gonzlobo on 2006-06-25
First off, Ubuntu is a nice distro. I've only been with it since 6.06 was released, but I was a Debian guy when 3.0 was first out (a *long* time ago :) ). After that I spent a year with Gentoo & another with Suse 9.x. All nice - in their own ways - but I wanted to get back to apt-get. 

Through out my distro travels, I've had this unusual problem with Firefox. Whenever the power is cycled to my Acti*ntec GT701WG wireless DSL modem, I temporarily lose browser access for a few days. Well not completely, some websites are immediately accessable, but other bookmarked websites take a few days to regain access, then after that, I can browse the world. 

My dual-boot machine works fine with Firefox once booted into XP, and Konquerer works fine (well it did with Suse, I don't have KDE installed with Ubuntu).

My hardware has changed over the years and of course OSes, but the only constants are Firefox, my Linux-friendly ISP and the Actiontec modem. Needless to say, I'm more than willing to blame the modem (I've had to replace 2 already), but any help from Ubuntu users will be *very* helpful. 

Note: Both OSes use dynamic IPs... curious, could my problem be IPV6-related?

---

### Post by mips on 2006-06-25
[http://www.ubuntuforums.org/showthread.php?t=95350](http://www.ubuntuforums.org/showthread.php?t=95350)
[http://www.ubuntuforums.org/showthread.php?t=133599](http://www.ubuntuforums.org/showthread.php?t=133599)
[http://www.ubuntuforums.org/showthread.php?t=187534](http://www.ubuntuforums.org/showthread.php?t=187534)

or just try searching for actiontec in these forums.

---

### Post by gonzlobo on 2006-06-25
Thanks, you have been a great help.

---

### Post by mips on 2006-06-25
What exactly fixed your problem, for future reference incase anybody else needs to know ?

---

### Post by gonzlobo on 2006-06-25
[B]Ah, but of course! I followed your advice from the first link.

[/B]> [B]
Step1[/B]
In the firefox address/URL space type "**about:config**" , scroll down to **network.dns.disableIPV6 = false** ,double click this line to change it to **true**.
In the above do NOT type in any quotes.

**Step2**
Open a terminal and enter:
**sudo gedit /etc/modprobe.d/aliases**

Look for the line that reads:
**alias net-pf-10 ipv6**

Change it to:
**[COLOR=Red]#[/COLOR]alias net-pf-10 ipv6**

Save and reboot your PC.

---

### Post by mips on 2006-06-25
Thanks.

---


---
title: "Ubuntu on Mini ITX. Easy or Hard??"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by risager on 2006-06-19
Im considering buying a Mini ITX (MB VIA Epia M10000N Onboard C3 Ezra 1000) for a home music/mail/web/backup server, running Ubuntu 6.06 server. I have no experience with this kind of MB. Will Ubuntu work out of the box?? I do not really care for the whole tweeking and recompiling kernel stuff.

---

### Post by MetalMusicAddict on 2006-06-19
I think it will depend on whether unicrome driver support has gotten better. Im still waiting on a couple threads to find out. I wanna build a tiny HTPC.

---

### Post by Patje on 2006-06-19
[QUOTE=risager]Im considering buying a Mini ITX (MB VIA Epia M10000N Onboard C3 Ezra 1000) for a home music/mail/web/backup server, running Ubuntu 6.06 server. I have no experience with this kind of MB. Will Ubuntu work out of the box?? I do not really care for the whole tweeking and recompiling kernel stuff.[/QUOTE]


I use it as a small webserver, mailserver, backup storage and FW for my home network. It works great for that purpose. Just look out with the Ubuntu 6.06 server iso (ubuntu-6.06-server-i386.iso). It gives intstallation errors when rebooting after install. With ubuntu-6.06-alternate-i386.iso it installs great.

---

### Post by gregb49 on 2006-06-20
[QUOTE=risager]Im considering buying a Mini ITX (MB VIA Epia M10000N Onboard C3 Ezra 1000) for a home music/mail/web/backup server, running Ubuntu 6.06 server. I have no experience with this kind of MB.[/QUOTE]I use an M10000 but have found graphics problems with 6.06. I had to change some xorg.conf settings - see [http://www.ubuntuforums.org/showthread.php?t=187177&page=10](http://www.ubuntuforums.org/showthread.php?t=187177&page=10)
Apart from that it is very stable and a delight to use. (And works in a tiny box). Greg

---

### Post by MatBi on 2006-06-21
Just installed yesterday Xubuntu on a via ME6000, works pretty fine, i'll try to add openchrome drivers and custom optimized kernel soon.

---

### Post by markba on 2006-06-25
[QUOTE=Patje]It gives intstallation errors when rebooting after install. With ubuntu-6.06-alternate-i386.iso it installs great.[/QUOTE]
I've run into this very problem also. I solved this by installing 5.10 (server) and do an inplace migration to 6.06 (modify sources.list, update and dist-upgrade). My guess is that the kernel version provided in the server install (2.6.15.23) is the cause for the reboot problem: after upgrading to 6.06, the kernel version is 2.6.15.25.

---

### Post by MatBi on 2006-06-26
Was anybody successful in booting from USB on a Epia?

---

### Post by bretticus on 2007-07-28
> **Patje said:**
> I use it as a small webserver, mailserver, backup storage and FW for my home network. It works great for that purpose. Just look out with the Ubuntu 6.06 server iso (ubuntu-6.06-server-i386.iso). It gives intstallation errors when rebooting after install. With ubuntu-6.06-alternate-i386.iso it installs great.

Just wanted to report that the server install for 7.04 still fails to boot. Some months ago (April 2007) I installed Ubuntu 7.04 Alternative Herd 5 (last pre-release I think) via install cd successfully. I'm dowloading  ubuntu-7.04-alternate-i386.iso as I type (probably not much different than Herd 5.)

---

### Post by MatBi on 2007-07-29
Had no problems here installing 7.04 from the server cd.

---


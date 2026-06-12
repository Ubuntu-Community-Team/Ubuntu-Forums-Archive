---
title: "problem with snap"
date: 2024-11-06
forum: Installation &amp; Upgrades
---

### Post by jgw on 2024-11-06
I had been having with snap.  So I deleted it all and re-installed snap.  I now have apparently have snap.  It is, however, kinda odd.  When I goto 'snap' there is one thing in it 'firefox'.  The problem is that everything under 'firefox' is zero and its not installed there.  That's fine but I don't understand that one.  Then there is the snap store - not here.  I tried to install it and failed.  I can live with this but I would rather not.  

When I checked snap I got:
[HTML]snapd.service - Snap Daemon
     Loaded: loaded (/lib/systemd/system/snapd.service; enabled; vendor pres>
     Active: active (running) since Wed 2024-11-06 09:14:47 PST; 45min ago
TriggeredBy: &#9679; snapd.socket
   Main PID: 737 (snapd)
      Tasks: 14 (limit: 19049)
     Memory: 57.8M
        CPU: 2.192s
     CGroup: /system.slice/snapd.service
             &#9492;&#9472;737 /usr/lib/snapd/snapd

Nov 06 09:14:47 greg-HP-Compaq-8200-Elite-CMT-PC snapd[737]: backends.go:58:>
Nov 06 09:14:46 greg-HP-Compaq-8200-Elite-CMT-PC systemd[1]: Starting Snap D>
Nov 06 09:14:47 greg-HP-Compaq-8200-Elite-CMT-PC systemd[1]: Started Snap Da>
Nov 06 09:15:56 greg-HP-Compaq-8200-Elite-CMT-PC snapd[737]: storehelpers.go>
Nov 06 09:15:58 greg-HP-Compaq-8200-Elite-CMT-PC snapd[737]: storehelpers.go>
Nov 06 09:16:02 greg-HP-Compaq-8200-Elite-CMT-PC snapd[737]: storehelpers.go>
Nov 06 09:16:05 greg-HP-Compaq-8200-Elite-CMT-PC snapd[737]: storehelpers.go>
Nov 06 09:16:06 greg-HP-Compaq-8200-Elite-CMT-PC snapd[737]: storehelpers.go>
Nov 06 09:16:08 greg-HP-Compaq-8200-Elite-CMT-PC snapd[737]: storehelpers.go>
Nov 06 09:19:51 greg-HP-Compaq-8200-Elite-CMT-PC snapd[737]: storehelpers.go>
~[/HTML]

Thoughts?

---

### Post by Holger_Gehrke on 2024-11-06
Are you talking about '/snap/' or about '~/snap/' ? The first is the directory snaps are mounted into (snaps are basically compressed filesystem images ...) the other is the directory in your $HOME where installed snaps store their per user configuration. If it's the latter then whatever is in there is just leftovers from the snaps you previously had (your Firefox configuration). If it's the first, then the problem is probably a lot deeper, possibly a broken snap-file left over and getting mounted there. Installed snaps are stored in '/var/lib/snapd/snaps/' and then mounted into subdirectories of '/snap/'.

Holger

---

### Post by jgw on 2024-11-06
Thank you for the reply............

I did: sudo snap install core

it seemed to fix the problem, not sure.  

I will mark this as solved.........

---


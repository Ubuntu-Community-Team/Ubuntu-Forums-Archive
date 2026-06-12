---
title: "japan...internet configuration"
date: 2005-11-04
forum: Installation &amp; Upgrades
---

### Post by nico_paris_in_japan on 2005-11-04
I neeeed help!

I tried some differents distros, when I came to ubuntu, I saw how nice it is, god...

I explain. 

I'm in Japan for work for a period of 6 monthes. Company that send me there gave me a laptop (HP NC6000). Company that i go to(japaneese) found for me a Provider, so I have an internet connexion with an ethernet modem. When I wanted to install the ISP's CD on my laptop , came the surprise: I don't have admin rights to install ISP program, so everything wrong...

OK, I said to myself

No trouble, test some liveCDs, (I have linux at home,but Mandrake) this should work, ethernet connexion, computer, no problem....

so, after knoppix (this was to old, didnt recognize my network card)
and Damnsmalllinux (cool, light, but difficult to use in case of problems..., and few users...)I came to ubuntu.My wife is from Africa, so I liked the concept.
So I put CD in drive and switch on computer.
Choose parameters of language and country.
starts.

Nice surprise, nice music, nice graphics, CoOoL.

I go to system, networks.

He recognizes three inactive plots:

ath0 (should be wireless port of computer)
eth0 (network card, where my modem is pluged in)
ppp0 (think there is an intern dialup modem)

I say , cool, recognizes my network card. so, activating, with DHCP. As I understood, DHCP makes everything automatically...

Connected on my ethernet port, there is a VDSL modem (VH100S) pluged into the wall. So I launch pppoeconf in root mode. I say yes everywhere, put in login and pass."should work" with firefox, say to myself...if worked, I wouldn't be here telling my life.

So, does not work, i tape plog what happened, it says

localhost pppd[xxxxx] ppp session is yyyyy
localhost pppd[xxxxx] using interface ppp0
localhost pppd[xxxxx] connect ppp0 <--->eth0
localhost pppd[xxxxx] couldn't increase MTU to 1500
localhost pppd[xxxxx] couldn't increase MRU to 1500
localhost pppd[xxxxx] couldn't increase MRU to 1500
localhost pppd[xxxxx] CHAP authentication failed:authentication failed
localhost pppd[xxxxx] couldn't increase MTU to 1500
localhost pppd[xxxxx] couldn't increase MRU to 1500
localhost pppd[xxxxx] connection terminated

lsmod  gives me (3 firsts lines)
 
module       size       used    by

pppoe         13120      0
pppox         3404        1       pppoe
ppp-generic 25748      2       pppoe,pppox
slhc            6656       1       ppp-generic

bon, I go to tape ISP's DNS in resolv.conf, no results.

Maybe someone could help me to configure my connection?

Thx!

---


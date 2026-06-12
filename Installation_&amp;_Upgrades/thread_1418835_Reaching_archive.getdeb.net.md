---
title: "Reaching archive.getdeb.net"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by nyarnon on 2010-03-01
Synaptic is failing frequently the last couple of days while updating. The message I receive is that it cannot reach archive.getdeb.net which resolves to 94.126.144.44. A traceroute ends in limbo:

Hop	Hostnaam	IP	Tijd 1	Tijd 2
1	roelf-desktop	192.168.1.104	0.169ms	
1	speedtouch.lan	192.168.1.254	58.927ms	
1	speedtouch.lan	192.168.1.254	90.764ms	
2	speedtouch.lan	192.168.1.254	89.924ms	
2	no	reply	*	
3	bl3-74-81.dsl.telepac.pt	213.13.74.81	49.192ms	
4	te-1-1.lcatrt2.telepac.net	213.13.135.150	49.196ms	
5	xe21-1GE.xmr1.as25137.net	82.102.1.249	48.948ms

The later being NFSi Telecom Lda 

What is going on here some misplaced spamblock in de routing?

I tried changing the repository from main to the dutch one but it doesn't change anything.

---

### Post by robert shearer on 2010-03-01
This may be of interest...
[http://ubuntuforums.org/showthread.php?t=1418429&highlight=getdeb](http://ubuntuforums.org/showthread.php?t=1418429&highlight=getdeb)

---


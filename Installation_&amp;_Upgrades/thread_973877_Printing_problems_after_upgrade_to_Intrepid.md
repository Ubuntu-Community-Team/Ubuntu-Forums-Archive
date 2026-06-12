---
title: "Printing problems after upgrade to Intrepid"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by fancyl on 2008-11-07
I have been successfully using my RICOH IPSiO NX650S laser printer under Hardy (on my Dell Vostro 200) for a while now. But when I upgraded to Intrepid, it just stopped. 

RICOH doesn't seem to officially support linux, but I found a random driver that worked before. The same driver doesn't work now. Moreover, it isn't even available (from what I can tell) in the repositories. I WAS using a driver for the "Ricoh RPDL IV Laser Printer" that just happened to work for a while under Hardy Heron. So I went on a quest to find a ppd file. I have a mac at home, so I downloaded the mac drivers off the RICOH website and extracted the mac ppd file. But it doesn't work on the linux box. It send the document to the printer, and is listed as completed, but nothing ACTUALLY gets printed.

Attached is the .ppd that I have been trying to use. I commented out 2 lines which I understand to be mac only. The "cupsfilter" and the "apdialogextension" lines have been commented out.

A similar problem was discussed [here]("http://ph.ubuntuforums.com/showthread.php?t=957132&highlight=ricoh+ipsio") but was closed before it was solved.

Any help would be great.
Thanks.

---


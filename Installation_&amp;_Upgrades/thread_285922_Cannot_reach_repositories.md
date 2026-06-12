---
title: "Cannot reach repositories"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by tesseract420 on 2006-10-27
Hi,

I'm behind a proxy server (as is this whole country, don't ask). I can surf the web with no difficulty. When I try to use 'apt-get" or synaptic or the update manager, I have no success connecting. Apt-get gives me 502 proxy errors with a reference to an ISA server. There was a solution to this posted in 2005; but that page referenced is no longer accurate and I can only use one proxy server, not two. Synaptic and Update Manager can't reach the network. I manually configured the proxy in Synaptic, there's no choice to do this for Update Manager.

I also changed the preferred dns, but that didn't help.

Anyone have any ideas?


Thanks.

---

### Post by tesseract420 on 2006-10-28
I found the answer so I thought I'd answer this if anyone is having the same problem. The problem is that I have a static assigned IP address, not a dynamically assigned IP address. The reason why it's confusing is that if you set the IP address to dynamically assigned, even though it isn't, you can still pull web pages though you can't reach the respositories. Once I changed the network settings to an IP address assigned by my ISP,everything worked properly.

So that's the answer.

---

### Post by Carbonfish on 2006-10-28
That's good information tesseract420.  Thanks

---


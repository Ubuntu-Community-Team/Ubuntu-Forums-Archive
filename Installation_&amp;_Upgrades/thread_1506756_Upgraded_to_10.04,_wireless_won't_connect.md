---
title: "Upgraded to 10.04, wireless won't connect"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by RIT_girl on 2010-06-10
I have a feeling this might be quick fix, but I'm beating my head on it. 

I have no wireless problems with 9.10. I upgraded via synaptic package manager to 10.04, and the only things that seems to be off is my wireless. It sees my network, other networks, ect, but it won't connect. I can get a wired connection no problem, but thats not the point of a netbook :) 

I tried  

```
 sudo service network-manager stop
sudo service network-manager start
```

and ran ```
lspci
``` to determine I have

 03:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)


Any help getting this running would be appreciated :)

---

### Post by davidmohammed on 2010-06-10
number of threads state that this is broken in lucid.  [This thread]("http://ubuntuforums.org/showthread.php?p=9226510") mentions of a possible work-around using ndiswrapper.  Worth a read.

---

### Post by RIT_girl on 2010-06-12
I have been trying to understand these threads, but I haven't found a conclusion. 

Can someone please provide some more support? I've been trying things off and on, but most of the other threads seem to be a bit above my head :) 

thanks!

---


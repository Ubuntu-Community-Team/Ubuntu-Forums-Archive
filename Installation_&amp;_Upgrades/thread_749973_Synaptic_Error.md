---
title: "Synaptic Error"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by Blind Tiger on 2008-04-09
When trying to fix an otherwise inoperable Synaptic, I get the following error:
> # sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Error!
E: Could not open file /var/lib/apt/extended_states - open (5 Input/output error)
E: Unable to determine the file size - fstat (9 Bad file descriptor)

I'm lost, and cannot configure my system any further!  Please help.  Thanks.

--NOTE: SOLVED--

With another search using "extended_states" I found this solution:
> sudo mv /var/lib/apt/extended_states /var/lib/apt/extended_states_tmp

---


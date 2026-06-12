---
title: "Dual-booting: some queries on partitions and swaps"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by chezzo on 2009-12-27
I'm currently looking into getting a new laptop, and so have been doing some research into the best way to go about dual-booting Ubuntu with Win7 (my current laptop is dual-booting Ubuntu and XP).

[This lifehacker tutorial]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony") contains some interesting suggestions which I would be grateful to have some input on.

Firstly, having a single large NTFS partition for data and linking the Ubuntu and Windows documents folders to it seems very sensible, although if anyone has any ideas why it might not be...?

Secondly, it suggests simply using a file on the NTFS partition for swap, rather than creating a separate partition. I've no idea about the relative merits of swap partitions and files - according to some things I've read, although partitions used to be better there is now little difference. However, I don't really see the benefit of using a file over a partition - why shouldn't I simply create a swap partition in the same extended partition as my NTFS one while I'm there? Creating a swap file seems like extra effort for little gain.

Finally, how much swap do I need? One site I found recommended that for RAM over 2GB, the swap size should be the size of your RAM plus 2GB. Since my laptop is likely to have 4GB of RAM, that means a 6GB swap. Is a swap this big really necessary?

Responses to any or all of these questions would be much appreciated.

EDIT: also, I read somewhere that Ubuntu does not need to be installed to a primary partition, and so could be installed in the extended partition along with my NTFS partition and (potentially) swap partition. Is this correct/advisable?

---

### Post by prshah on 2009-12-27
> **chezzo said:**
> a single large NTFS partition for data and linking the Ubuntu and Windows documents folders 

Secondly, it suggests simply using a file on the NTFS partition for swap, rather than creating a separate partition. 

Finally, how much swap do I need?

Ubuntu does not need to be installed to a primary partition, and so could be installed in the extended partition along with my NTFS partition and (potentially) swap partition. Is this correct/advisable?

1st) It is a good idea.

2nd) Using a file on the NTFS partition for swap is not advisable in my opinion. If your NTFS partition is "dirty" (for example without proper Windows shutdown) then the swap file will not be mounted / available. This will especially become a big problem if you plan to use hibernation, since during hibernation, memory information is written to the swap.

3rd) Swap size: No rules, only recommendations. I recommend:
[indent]RAM <=512Mb ==> Swap 1Gb-3Gb (depending on type of work on computer)
RAM >512MB < 2GB ==> Swap 2GB+ if using hibernation, else 512MB+
RAM >=2GB ==> 1.25* RAM if using hibernation, otherwise just 0.25* RAM is OK.
[/indent] Swap is not compulsory, but there are some (undocumented) incidents that seem to suggest that even a nominal swap is required.

4th) Yes, true. However, if put in an extended partition, you may run into problems with resizing later on; in the sense that you will have to take some additional steps when (if) you decide to resize. (Eg, first resize extended partition, then resize logical partition).

Good luck with your installation.

---

### Post by chezzo on 2009-12-27
Great, thanks for the advice!

---


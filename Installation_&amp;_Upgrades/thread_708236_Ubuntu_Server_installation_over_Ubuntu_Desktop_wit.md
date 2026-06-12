---
title: "Ubuntu Server installation over Ubuntu Desktop with /home in existent RAID 5"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by tpinheiro on 2008-02-26
Hi.
This is my first post in this forum. The reason for that is that, normally, I can find all the answers I need. However, this time it seems that is not the case.

The situation is the following:

After having recently felt the strong hand of Murphy's Law landing in my computer systems at home (a network drive broke at the same time my desktop's CPU stopped working (PC1)), I acquired a new computer (PC2), and a new CPU for PC1.

While the CPU did not arrive, I installed the desktop x64 version of Ubuntu 7.10 in PC2.
I installed everything  in the following configuration:
- / in a RAID 1 in hda1 and hdb1;
- swap in RAID0 using the same hda1 and hdb1;
- /home in RAID5 in sda1, sdb1 and sdb3, containing the data I manage to recover from my network drive.

Now that the CPU arrived, I would like to transform PC2 in a file server and, for that, I would like to perform a clean install of Ubuntu 7.10 server 32 bits, while keeping my RAID 5 /home intact (all my data is there, and I do not have an option to back it up at the moment).

Can that be done? If yes, could I be given some tips on how to do it?

Thanks in advance.
T. Pinheiro

---

### Post by tpinheiro on 2008-03-04
Hi,

Apparently, I didn't get very lucky with the community. Let me try again.

If I use the alternate installer and choose not to reformat the md2 array, can I still mention md2 and the mount point for /home? That is, will my existent RAID 5 array be recognised and kept untouched? Or will the data be overwritten?

If I am not making much sense please tell me. Perhaps I can try to explain it in a different manner.

Cheers!

---


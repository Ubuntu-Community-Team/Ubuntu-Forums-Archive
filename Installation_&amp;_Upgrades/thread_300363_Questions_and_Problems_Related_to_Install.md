---
title: "Questions and Problems Related to Install"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by SteveF on 2006-11-15
I apologize if this gets posted twice.  My first post did not show - not sure why.

I tried upgrading to Edgy and ran into problems.  To keep a long debug session short, the problem turns out to be that grub menu.lst had the wrong partition information and the wrong UUID.  I changed it to use the old way to reference root and changed the partitions and it works now.

Some questions:
1) Any ideas on why the wrong UUID and partition were used (it ended up using the one for my Kubuntu partition which was not upgraded)?
2) How do I find the correct UUID of my Ubuntu installation so I can reset grub.
3) Because I had UUID problems, should I worry about the issue people have had with losing their swap partition?
4) I use a desktop not a laptop so is this an issue anyway.
5) How can I tell in vim-tiny is used or regular vim.  I had vim installed with Dapper and so far I don't notice a difference (other than being v7).

Thanks for any info,

Steve

---


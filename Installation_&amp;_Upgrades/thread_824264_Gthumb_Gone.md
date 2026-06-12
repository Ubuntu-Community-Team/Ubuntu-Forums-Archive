---
title: "Gthumb Gone"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by loyal one on 2008-06-09
Hi All:

Late night here in Maine, meds are working a bit too good: removed Gthumb, for no good reason, then decided I really do like it, and reinstalled using Synaptic. But, no love tonight; Gthumb will not load. I suppose some dependency is not met or ???? It worked fine before I borked it. Any help will be appreciated.

Ubuntu Hardy 8.04
P-4 2.4 Ghz
1 Gb ram
Intel system
Loyal One
TIA

---

### Post by Partyboi2 on 2008-06-10
Are you having problems installing it? Or running it after it is installed? If having problems running it after install try starting it from a terminal and posting the output.

---

### Post by loyal one on 2008-06-10
Partyboi2, thanks for the response. 

As they say in Law and Order: "now is the time to come clean, and tell all" So, before I deleted gthumb, I discovered that there was 44,000 thubnails in .thubnails. Surely, I thought, that is just wrong; so, I removed all those files to trash, and, following an adventerous   thought path, I decided that gthumb ( thumb ) had caused all this bad housekeeping. Just remove it, I reasoned, and see what happens -- not good.

I later discovered that it was Gwenview that had caused the massive bloat in .thumbnails because I had not checked the empty cashe box when closing gwenview. I was warned that this would remove .thumbnails, but so what ? And so I did, and now .thumbnails is gone.

Running gwenview in terminal results in a segmentation error. Since .thumbnails is gone, I cannot check it for ownership errors, and I do not know how to check memory errors in Linux.
Thanks again for the response, wish I could be more helpful

Loyal

---

### Post by Partyboi2 on 2008-06-11
have you tried purging and reinstalling those 2 packages?
sudo apt-get remove --purge <package>
sudo apt-get install <package>

You can use a package called [[COLOR=Blue]valgrind[/COLOR]]("https://wiki.ubuntu.com/Valgrind") that can help you track down segment faults.

---


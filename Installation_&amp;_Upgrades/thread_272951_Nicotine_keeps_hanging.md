---
title: "Nicotine keeps hanging"
date: 2006-10-07
forum: Installation &amp; Upgrades
---

### Post by Asmodis on 2006-10-07
Hi there,

I'm a great fan of the program nicotine, which I suppose almost everyone here knows. But I don't seem to get it running on my Ubuntu (6.10) Installation.

It just hangs after a while. No error, nothing. When I'm running it in the terminal it just comes up with a lot of gtk.TRUE is deprecated and so on messages, but that seems to be usual for nicotine, as I had the same message on my other distros.

I also tried nicotine+ (1.2.5.1) with the same results. I deleted my whole .nicotine folder no result.

I don't know anything else to do. Nicotine+ came up with a hint to install psyco, so I even did this, still no result.

Does anyone have an idea how to solve this?
thx in advance

Jesus, just found out, what the problem was:

I mounted my music files via NFS and wanted to write the incomplete files directly onto my remote machine. This apparently doesn't work.

---


---
title: "Persistent and consistant Updating problems"
date: 2016-11-05
forum: Installation &amp; Upgrades
---

### Post by Mark Phelps on 2016-11-05
I run two distros daily -- Ubuntu 16.04 Mate and Mint 18 Mate, and I tend to do Updates on each once a week.

This last week, BOTH failed while doing updates -- and from what I could tell, for the same reasons.

Any attempt to download from either archive.canonical.com or security.ubuntu.com hung at ZERO percent.

When I used the GUI tools, all I could see was that the update process hung -- until I terminated it.

But, when I used the terminal and "sudo apt-get update", then I could see the downloads hanging at zero percent.

I tried a host of different mirrors, from local to International, and the result was always the same.

I ended up hand-editing the repositories.list file for each distro and commenting out the two related lines.

After that, both distros updated OK.

But, I really don't like having those lines omitted, especially the security lines.

UPDATE 

I had some lines commented out in sources.list and when I used the GUI tool to change the Mirror, I only looked at the top part of the file to confirm the changes had taken place. When I then did an update test and it worked, I went down and UNCOMMENTED the lower lines -- but failed to notice that the GUI tool had NOT changed the mirror location in each of those lines, so, of course, they failed.

When I went back and change the mirror location in ALL the uncommented lines, and ran apt-get update again, this time it worked!

---


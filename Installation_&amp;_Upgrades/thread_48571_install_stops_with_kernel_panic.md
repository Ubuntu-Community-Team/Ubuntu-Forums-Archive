---
title: "install stops with kernel panic"
date: 2005-07-13
forum: Installation &amp; Upgrades
---

### Post by t2kburl on 2005-07-13
I am trying to reinstall Ubuntu on a 200Mhz p1 machine with only 24 MB of RAM. The HD already has Ubuntu on it but it fails to boot (grub error 18 ???)
the installation attempt doesnt get very far before it dies with a kernel panic and a bunch of lines regarding memory usage.
All 4 banks are loaded with the old 72 pin SIMMs, but it is still only 24 MB.
Is this install even possible?
Or should I try something like DSL?

---

### Post by codejunkie on 2005-07-13
you could try a server install it doesn't include a gui just a console enviorment and then install a lightweight desktop enviorment like xfce or open box or do an expert install might be more useful because you can just skip the packages you dont need   hope this helps.

---

### Post by andlinux21 on 2005-07-13
you need to make sure the memory is good you need to have at least 32M I think

---

### Post by t2kburl on 2005-07-13
The memory is OK ... tested that with DSL (Dam Small Linux) live CD.
I'll give the server install a shot. I was planning on using IceWM as the default wm for this machine. I'm donating it to a local day care center for kids to play games on (just the Linux included stuff, nothing extravagant)

Also I looked up the GRUB error ... (BIOS doesn't support partitions larger than 8 gigs) no option in BIOS on this old box that I can adjust for that ...  its an 8.6 GB HD and I only used 256M for swap.   I'll just have to make that a little bigger (I'm sure it will need it  :)  ) and the new install will boot.

actually ....   I may try just resizing the swap partition with qtparted (I have it on a system rescue CD) then maybe I can avoid the reinstall altogether  :)

---

### Post by t2kburl on 2005-07-13
well ... so far ... no luck with anything  :???: 

it passes memtests
system rescue CD hangs at starting hotplugging, so no chance for qtparted
my knoppix CD is (apparrently) unreadable (it is pretty old and batterred)
server install gives me the same kernel panic

DSL is the only thing I have that boots in it at all, and it only has cfdisk for partitioning, so a resize is out.

I'm thinking I'll have to go with DSL --- if not that it'll have to be (eeeeewwww) win95 I suppose

btw in the help section on the Ubuntu CD it says 24 MB ram is the minimum

one Ram issue might be that bank 1 is EDO and bank 2 isnt, but the 4 sticks combined give me the most memory total of any of the 72 pin SIMMs I have. (anybody want some?)
I'd appreciate any more suggestions. It will be at least 24 hours before I touch that machine again.

---


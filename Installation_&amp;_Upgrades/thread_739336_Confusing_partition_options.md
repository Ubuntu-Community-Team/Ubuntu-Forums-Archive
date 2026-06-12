---
title: "Confusing partition options"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by beatme101 on 2008-03-29
I'm installing Ubuntu for the first time (first time on a real computer as opposed to virtual, at least), encountering several problems along the way, two of which I've worked around <rant>(screen went blank for about 10 minutes while loading, it fixed itself, then there were problems with the resolution only being 640x480 yet the install window is about 4x that big, a thread here revealed I can hold the alt key and drag the window around (I guess only one other person in the entire world tried to install Ubuntu before (edit: Live CD needs better defaults. Having an option to chjange it that WORKs would be nice, the change resolution window doesn't give any options when you click on "640x480" and you can't type in that field, I don't understand why it's clickable))).....</rant>

Anyway, my problem now: Since I am installing alongside an existing Fat32 partition (I am playing with Windows 98 too), I want to keep that how it is. It is 32 GB. The hard drive is 80 GB. I do not know what option to pick to use up the remaining unpartitioned space for Ubuntu. The first option doesn't seem precise enough, I could either pick too little or too much way too easily. The second option is obviously not what I want because I want to KEEP the other partition. The third option seems most likely but I do not know if that includes the free space that exists in the Fat32 partition.

I would pick Manual but I do not know if I will have the option to go "back" to this choice if I discover Manual does not suit my needs.

EDIT: Ubuntu 7.10

---

### Post by Pumalite on 2008-03-29
Choose 'Manual' and if you cannot find the unallocated space; get back. Make 2 'New partitions in that unallocated space:
Most of it (less 1000 MB) at the beginning, mount point '/'
1 GB at the end for /swap
Then press 'Forward'

---

### Post by beatme101 on 2008-03-29
Thanks, that helped. Manual was the ideal option for me. Seems to be installing now, hopefully with no further troubles..

---


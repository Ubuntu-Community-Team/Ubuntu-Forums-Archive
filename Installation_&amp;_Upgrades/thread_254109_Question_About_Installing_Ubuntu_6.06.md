---
title: "Question About Installing Ubuntu 6.06"
date: 2006-09-09
forum: Installation &amp; Upgrades
---

### Post by DarknessKing on 2006-09-09
Umm I know that this is probably been answered, and I have read into it but I just want to make SURE before I do anything I might regret.

I am currently running Windows XP and I just recieved bu Ubuntu 6.06 CD today and I want to install it on my hard drive. However, I don't want to lose any data when I install Ubuntu, so I chose "Use the largest continuous free space". But an error comres up saying "Failed to Partition the selected disk", but it continues on to the next screen.

I just want to know if that means I can still install ubuntu without losing any of my other data, or if it is going to erase everything like normal. I really appreciate the help!

---

### Post by taurus on 2006-09-09
I recommand you boot into your XP first and defrag the heck out of your harddrive.  Run it about three times to make sure.  Then, boot the LiveCD and use gparted to resize your harddrive, creating space for Dapper...

---

### Post by aysiu on 2006-09-09
The only way to be 100% sure you don't lose data is to **back it up**.

If you want to be 99% sure, though, defragment (as taurus advises rightly) and resize. The auto use of continuous free space may have issues (I'm not sure), so you may want to manually resize partitions (gives you a bit more control).

For more details, go here: [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---


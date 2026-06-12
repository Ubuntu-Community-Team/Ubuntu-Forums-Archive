---
title: "[SOLVED] How to partition the right way??"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by doubledouce on 2007-11-25
Hi!

I'm messing around with linux for the first time and I've successfully installed ubuntu.

First I reformated my two harddrives using Gparted and then I defined my own partitions during the install. I was told I should make the swap-partition 1 GB (I've got 2 gigs of RAM), the / -partition 10 gigs and use the rest of the space in /home. But that means that the space allocated for /home is on two different hd's. I got a message saying something about the same something on two headers (I can't quite remember) so I named the space on my main HD for /home and the space on the other HD for /home1.

Is this the right thing to do? Or should I somehow have named the space on both harddrives for /home?? Or are the names irrelevant?

This first install will be a test run and then I'll reformat again when I got the hang of this. I like to keep my computer as "clean" as possible. :)

---

### Post by jken146 on 2007-11-25
I would suggest putting / at the beginning of your first drive, swap at the end of it and /home in the remaining space in between.  Then format your 2nd drive (give it a label if you wish - whatever you like, 'storage' for example) as one big partition and crate a link to it somewhere in /home.

edit: I read your post carefully and I see that's what you did!  You should see home1 mounted though.

---

### Post by doubledouce on 2007-11-25
By mounted do you mean link it to the /home partition? I don't know how to do that. 

It's a bit confusing going from being a skilled computer dude in windows to being a noob again. :rolleyes:

---

### Post by jken146 on 2007-11-25
By mounted I mean the OS will find it and sorta load it up for access (sorry I don't know how mounting works).  It should appear on your desktop as an icon.  

Creating a link was just a suggestion of mine so that it looks like one home folder with another folder in it.  What I meant was /home/<user>/<link-to-/media/2nd-drive> would exist within /home/<user> .  This is just a matter of creating a link to another file (simple enough in a file browser, don't worry).

Hope this helps and I didn't confuse you!

Don't worry about feeling like a noob again.  Knowledge will come with time (and man pages :))

---

### Post by doubledouce on 2007-11-26
Thanks for the help! :)

---


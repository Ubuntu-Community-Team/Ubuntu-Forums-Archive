---
title: "new installation, may have blown it..."
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by willt528 on 2010-02-03
i hope I am posting this in the right place, if not, please feel free to send me somewhere else....

I am new to Ubuntu and new to tinkering with computers.  I happened to meet a guy who gave me a disk (9.10 release) and said "try this! It's great!" Naturally I thought he was nuts.  

But I held on to the disk, and as fate would have it, my brother was buying a new laptop, so I said "hey give me your old one" and I figured I would fiddle around with Ubuntu a bit, since lets face it, windows is, well, windows.

Admittedly, his old laptop was in bad shape...bogged down by who knows what.  My plan was to totally zap windows and go full bore with Ubuntu, see how I liked it and make a decision regarding the rest of my computers based on my experience here.  In my zest to install Ubuntu, i must have glossed over the option that asked me if I wanted to use the entire disk.

To make a long story short, the problem I am having is that it appears that windows is still there, taking up about 33G of a 40G hard drive.  Ubuntu seems to be occupying about 5G, with 3.3G used. I would like to know how the best way to go about getting rid of windows and reclaiming that space for my own use....?  Any suggestions would be greatly appreciated. 

By all appearances, Ubuntu is great, just like the guy said....I wish I would have gotten his name.

---

### Post by nothingspecial on 2010-02-04
The easiest way would be to install it again and choose use entire disk at the partitioning stage - job done.

If however you have configured Ubuntu to your liking and can`t be bothered to do it all again then -

Boot up the live cd and choose system > administration > partition editor (or gparted or whatever they call it these days).

Identify which partition is ubuntu and which is windows (ubuntu will be ext3 or ext4).

Delete the windows partition and then grow the ubuntu partition into the free space.

Make back ups first just incase you make a mistake.

---

### Post by willt528 on 2010-02-04
worked perfectly, thanks again for your help....

---


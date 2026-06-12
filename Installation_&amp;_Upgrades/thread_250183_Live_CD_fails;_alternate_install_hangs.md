---
title: "Live CD fails; alternate install hangs"
date: 2006-09-03
forum: Installation &amp; Upgrades
---

### Post by ManifestDestiny on 2006-09-03
I know that's kind of a vague title, but it's got to be better than 'installation problems.' =p

Anyway, it's exactly that. I'm trying to install Ubuntu on an old HP Pavillion I have. I got a new 250GB hard drive for it and hooked that up, clean and un-formatted. I also got some new memory for it (256 MB, bringing it up to ~320ish). I tested the memory with the install of Windows ME on the old drive before I put the new drive in to make sure that worked. Yeah, it came with Windows ME. :rolleyes: 

Anyway, another thing that I think is worth noting about the machine, (before I get to the installation), is that the BIOS doesn't support 48-bit addressing (drives larger than 137 GB). More later.



Getting to the actual install... I tried the Live (desktop) CD first. 'Start or Install Ubuntu,' it came up with some loading messages, and then all hell broke loose. I got a bunch of SQUASHFS errors, zlibsomething, couldn't read from page. It eventually boiled down to a terminal, but I couldn't do anything from there. I tried a few times, and sometimes it didn't even get that far -- I got a repeating message of 'bash: /dev/null: permission denied.'

So I tried the alternate install.

I got further this time, picked my language, keyboard layout, etc. I got to the partitioner and spent a few hours looking up information about that, since I really didn't know beforehand. I set up all four of my primary partitions - one for /boot, one for the swap, a large one (135 GB) mounted to /, and 111 GB not mounted to anything (free space). I had tried a couple of other configurations, but this was the one I settled on, because I figured I should still be able to access the free space later, and I was worried about having any single primary partition larger than 137 GB, because of the old BIOS.

Now, I've tried the alternate install about 10 times now -- I really want this thing to work. The first few times, it got past the partitioning, and I even got to setting up a user account, but then I got some 'corrupt file' errors when it was unpacking stuff. ("Installing base files.") I thought it might be the CD, so I burned it again, as slow as I could (8x). Did a CD check, too, everything came up OK. Still no luck.

I burned a total of 3 alternate CDs; no luck on any of them. Some of them die at random points, before they get to partitioning, during, or after, during the 'base install' part. I've never gotten farther than that. (Also, to be clear, 'die' means that sometimes it just hangs indefinitely, and sometimes I get messages popping up over the install bars and wrapping around the screen. Stuff like "*** glibc detected *** free: invalid pointer 0x[hexnumber].")


I spent all of yesterday trying to get this dang thing to install and I'm not about to give up now. =P If anyone has any suggestions, I'm more than willing to try them out. Thank you very much for reading all this, and thanks in advance for your replies.

---

### Post by ManifestDestiny on 2006-09-09
Nobody? Sigh...

I tried again today, and I think I have a better idea of what's wrong, but don't know how to fix it. I did a 'check CD for integrity' and got errors, but at different points each time -- sometimes it would come up with one file as having an error, but other times it would read it and keep on going. What? That would make me think it's a CD error, but I got the same errors on a different computer, though it's the same model.

Am I just screwed? ;_; Is there any way to install Ubuntu from a USB, maybe?

---

### Post by Original Brownster on 2006-09-10
Hi,
It could be the memory that's the problem, I'm not sure how you tested it with the windows me install so either run a memory test and / or pull the new memory. Did the new memory have the same CAS latency and speed?

One other thought though worth discounting, how old is the cd reader? Maybe worth cleaning the lens or pulling it and swapping out with the writer you used which I assume is on another pc.

---


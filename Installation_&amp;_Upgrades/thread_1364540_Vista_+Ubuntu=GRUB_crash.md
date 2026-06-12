---
title: "Vista +Ubuntu=GRUB crash"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by TheFSD on 2009-12-26
Okay, I decided to try Ubuntu. I've managed multiple OSs before, so I cleared some space, made a nice 40Gb chunk of unallocated space. I installed Ubuntu 9.10 with no problems. After noticing that I didn't have a quick and easy way to share my media between the 2 OSs (about an hour later), I decided to switch back to Vista, make another partition, and just use that to store media do I just have to mount that drive rather than surfing for my files.
 
Now, whenever I startup the machine, I get the "GRUB loading.
error: unknown filesystem>
grub rescue>"
 
I tried everything I could find from google, just getting "command ### not recognized". I went to reinstall Ubuntu, thinking it just got messed up, and saw that there were NO partitions shown during install. So I quit, which brought me to the demo. I went to drive manager, and my partitions were shown, but my UBUNTU partition was registering in gigabits rather than gigabytes, giving some ungodly huge number. I couldn't do anything to change the partitions (delete or relabel or anything). I kept getting "Partition Not Found" errors. However, I could mount the Windows and Media partitions, and run files from them.
 
I have zero experience with Linux, and was hoping to just get my feet wet. What have I messed up and how can I fix it?

---

### Post by TheFSD on 2009-12-26
And now it's saying
"GRUB loading.
error> no such partition
grub rescue>"

---

### Post by phillw on 2009-12-26
Hi, recovering Grub on a Win dual boot system is covered here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You'll be on grub2 if you have a new install of 9.10.
If you had 9.04 and upgraded, you'll most likely still be on grub legacy.

Either way, that link will get you up and running.

Regards,

Phill.

---

### Post by TheFSD on 2009-12-26
Thanks for the response, but I keep getting "command 'sudo' not valid". Every command I find in various tutorials gets the same treatment.

---

### Post by TheFSD on 2009-12-26
I just found out what I was doing wrong from that tutorial. To fix my Boot Record on the Windows end, I never deselected my OS from the repair list. Thanks for that link, I'd never have thought of that. So, now I can just wipe the old Linux partitions and startover. I wonder what broke everything though?

---

### Post by phillw on 2009-12-26
> **TheFSD said:**
> I just found out what I was doing wrong from that tutorial. To fix my Boot Record on the Windows end, I never deselected my OS from the repair list. Thanks for that link, I'd never have thought of that. So, now I can just wipe the old Linux partitions and startover. I wonder what broke everything though?

There is a possible 'gotcha' .... Some manufacturers and software will over-write the MBR (Your Master Boot Record) when Win is launched.
You will know soon enough, as your Grub will 'die' when you boot into Win. For once, it's not actually Win's fault (Rarely do I say that !!) So you will not be able to boot after you have run Win.

If that happens to you, post back & I'll point you to the threads dealing with that problem.

Regards,

Phill.

---

### Post by abhibharti on 2009-12-26
Good to see, it is solved. :)

---

### Post by TheFSD on 2009-12-26
> **phillw said:**
> There is a possible 'gotcha' .... Some manufacturers and software will over-write the MBR (Your Master Boot Record) when Win is launched.
You will know soon enough, as your Grub will 'die' when you boot into Win. For once, it's not actually Win's fault (Rarely do I say that !!) So you will not be able to boot after you have run Win.

If that happens to you, post back & I'll point you to the threads dealing with that problem.

Regards,

Phill.
I see. It was probably the software I used to make my partitions. I'm using the Acronis suite. I've been using it since the old Win2k days and never had a problem. I guess the new version isn't as smart as the previous ones (prettier though). I'll keep this in mind. I have wiped the old Linux partition using the Windows Vista utility, so I'll just reinstall it there. My Media drive is still in working order, so I shouldn't have to touch the Disk Director any more. Thanks for the heads up, Phill. Lifesaver.

---


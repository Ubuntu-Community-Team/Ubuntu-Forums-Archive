---
title: "Ubuntu 8.04.1 Installation problems"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by hermit_crab on 2008-10-16
Hi

I have a HP Comapaq nc6000 laptop, 512mb ram and i'm trying to install Ubuntu onto XP so it can dual boot however I'm having a few troubles trying to install and can't find much help from previous threads.

Basically when i'm trying to install, it gets up to stage 4 of 7, starting up the partitioner.  it gets up to 46% sometimes 53% and says scanning disks, but never gets any further.

also, an error message comes up saying there is a problem with /var/log/syslog and whether to carry on or not, however i'm not sure what to do with that.

can anyone help? i'm very new at this ](*,)

thanks
hermit

---

### Post by mikewhatever on 2008-10-16
What's the exact error message text?
Are you installing inside the XP partition or on a separate partition?
Have you defragged XP?
How much free space is there on the disk?

Sorry for all the questions.

---

### Post by hermit_crab on 2008-10-16
> **mikewhatever said:**
> What's the exact error message text?
Are you installing inside the XP partition or on a separate partition?
Have you defragged XP?
How much free space is there on the disk?

Sorry for all the questions.

That's ok
I'm installing inside the XP partition i think and I did defrag it but that was about a month ago.  There's about 15GB free on my hard drive and the exact message reads:

Partman failed with exit code 10.  Further information may be found in /var/log/syslog.  Do you want to try running this step again before continuing?  If you do not, your installation may fail entirely or may be broken

---

### Post by mikewhatever on 2008-10-16
I am not an expert, especially when installing in Windows, but a google search led to the following thread: [http://ubuntuforums.org/showthread.php?t=765958](http://ubuntuforums.org/showthread.php?t=765958)

I'd advise several things:
1. Cleaning the disk of unnecessary junk (CCleaner).
2. Checking for errors.
3. Defragmenting.

---


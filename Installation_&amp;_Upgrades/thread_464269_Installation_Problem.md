---
title: "Installation Problem"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by splinta on 2007-06-04
Hey people.

I am now a happy user of ubuntu since had problem with my wireless a year ago which made me resort come back to windows. This new ubuntu (7.04) is perfect, i love it.....

anyway, my problem is that im trying to install a program (frostwire) which i downloaded from the net. it opens fine and when im trying to install the program a error comes up saying "Only one software management tool is allowed to run at the same time". but im not running no update manager, aptitude or synaptic.

so how to do i sort out this problem?

---

### Post by wpshooter on 2007-06-04
I would complete shutdown the computer and then restart it and then try to run your installation from the downloaded file.  I believe that that should take care of the problem.  If not then you have some program that has been left open that needs to be closed.

Good luck.

---

### Post by sgtbob on 2007-06-04
I just acquired the 7.04 CD and in trying to install, I get the same error each time I try the installation.  Specific error at install:

[B]/bin/sh: can't access TTY; job contol turned off
(initfamfs) [147.625560] ata 2.01: failed to set xfermode (err_mask=ox4)[/B]

If I leave the installation alone, more numbers appear on the screen but essentially with the same response. 

Currenlty running Ubuntu 6.06 with good success, but this 7.04 was a problem on my Download and I even acquired a disc via snail mail and get the same error.

 Any suggestions appreciated on how to get 7.04 installed on this dual boot system?

---

### Post by splinta on 2007-06-04
Thanks for suggestion, wpshooter. :)

I have already tried it and it still dont seem to work. After that i thought it might be something wrong with the installation file itself so i got the limewire DEB and it still comes up with the same error.

I have also went through System Monitor and it doesnt show any of these programs running in the processes tab.

---

### Post by splinta on 2007-06-04
Ok. I have found a solution to this problem.

The problem was during installation my laptop decided to turn itself off, so it must off messed up something.

I had to "sudo dpkg --configure -a" to solve this problem

but now, im hit with a new problem. Everytime i want to install or update something it says

[B]E: The package frostwire needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.[/B]

How would I get rid of this?

---


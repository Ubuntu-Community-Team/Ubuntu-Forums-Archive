---
title: "sudoers permission denied problem fixed"
date: 2008-07-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by aikishugyo on 2008-07-29
Hello all, for the last two weeks I had had trouble not only booting into X, but also using sudo, so I could not even work from the command line. Diagnosing the problem (mistakenly, as it turns out) as a sudo or PAM issue, I looked at all threads (as well as Google hits) and checked all file permissions, regenerated files, purged and reinstalled all sudo and PAM-related stuff, check the /etc permissions. To no avail.

Finally, today, looking through *all* the recent threads for Intrepid I noticed the following: [running file-roller as root destroys permissions on / ]("http://http://ubuntuforums.org/showthread.php?t=870600")

Here it is stated that the / (root) permissions might have been changed, even though I did not run file-roller or nautilus (at least knowingly). Indeed, that was the case, / was set to 700!!!! Changing to 755 made it all work perfectly again. 

Also that the latest nvidia 177 driver works (no more need for the binary from nVidia) is a great pleasure, thanks all.

Working on the x86_64 system is great, and I really do not mind switching between Intrepid and the Debian unstable on my other partitions occasionally (heck, even Windows Vista SP1 is installed on a trial basis to test stuff!).

---

### Post by Gina on 2008-07-30
Yes, things are certainly getting better :) I think 8.10 will be another great advance in Ubuntu.  With the recent improvements in wireless and graphics drivers, Ubuntu has at last got to the stage where we can recommend it to less knowledgeable Windows users.  I've managed several successful converts lately :)

---


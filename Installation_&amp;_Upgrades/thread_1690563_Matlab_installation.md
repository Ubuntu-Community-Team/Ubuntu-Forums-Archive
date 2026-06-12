---
title: "Matlab installation"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by kripssmart on 2011-02-18
I installed Matlab in Ubuntu 10.10. I was able to get it running and I saw the initializing screen. However it showed me an error with OpenGL 

"warning : could not query OpenGL"

and it freezes there. I tried many things to get over with it and it didn't work. 

Anyone been through this before?

thanks.

---

### Post by olgis on 2011-02-21
Hi 
Which Matlab version are you running!? 
I have similar problem on Ubuntu 10.04 with Matlab 7.
All started with 2 warning messages
"warning : could not query OpenGL
warning : OpenGL appears to be installed incorrectly" 
Then I followed instruction posted [here]("http://ubuntuforums.org/showthread.php?t=447359&highlight=Matlab%3A+OpenGL") changing links to OpenGL source. I end up having the same problem as you do now... 

Try to run **System Monitor** (System>Administration>System Monitor) for me Matlab Waiting channel is **futex_wait_queue_me** or some times it is [B] poll_schedule_timeout
[/B]Do you have the same?

---

### Post by olgis on 2011-02-21
Today I reinstalled Matlab (changed Matlab 7.04 to Matlab 7.11) following [Ubuntu documentatio]("https://help.ubuntu.com/community/MATLAB")n everything works. No any more warning messages and Matlab works smooth and nicely.

Cheers, o.

---


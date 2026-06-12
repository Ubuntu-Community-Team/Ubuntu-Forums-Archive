---
title: "problem installing ubuntu 7.10 on fujitsu amilo pro"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by i_gabr_2008 on 2008-01-05
hello
i have a fujitsu amilo pro 3515 laptop and tried to install ubuntu 7.10 but i failed during the boot 
from live cd it says failed to allocate memory resource to device 
and goes with blank screen and i cant start the installation .
and if i connected my laptop to an external monitor it boots and begins the installation .
once i disconnect the external monitor and restart it give me the black screen .

does anone know a solution to this problem 

thanks in advance

---

### Post by i_gabr_2008 on 2008-01-05
finally i solved the problem and succeded to install ubuntu 7.10 on my laptop .
and i am writing this reply now runing it .
i connected the external monitor till instalation finish and i compiled the openchrome 
driver as in this tutorial [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)
until i finished then disconnwhen i hit ected it  and it worked fine
 
i compiled also the drm but  glxinfo | grep render  it says 
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect


and during the compilation there were no erors 

so how can i enable desktop effects and direct rendering ?

thanks in advance

---


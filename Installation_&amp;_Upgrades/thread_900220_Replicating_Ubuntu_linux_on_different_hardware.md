---
title: "Replicating Ubuntu linux on different hardware"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by simonek on 2008-08-25
Replicating Ubuntu linux on different hardware

In my project, 18 LAMP based web application is to be hosted in 18 locations on Ubuntu based Desktop servers. These 18 locations are independent and without internet connection.

For this I have done the following:

1. I Have installed Ubuntu 8.04 server on a PC (say,A) which has internet connection.
2. Since I wanted desktop also on the same machine, I installed ubuntu 8.04 desktop on PC A with ubuntu desktop 8.04 using 'apt-get'.
3. I installed some more packages with apt-get using internet on PC A.
4. I have loaded my LAMP based application also on to this PC A.
5. Using APTonCD, I have made copy of all the packages in the PC A.


Now I want to install all the applications (server, desktop, other applications) to 18 PCs where there is no internet connection.

For this I have loaded Ubuntu server on one of the new PC, say B.

Now, how can I load all the packages from the APTonCD to this PC B.
since desktop is not loaded to this PC, it does not have APTonCD package installed.
Once this is successful, I can do the same in all 18 machines.
Kindly help me to do this.

Thanks is advance
Simon Ambat

---


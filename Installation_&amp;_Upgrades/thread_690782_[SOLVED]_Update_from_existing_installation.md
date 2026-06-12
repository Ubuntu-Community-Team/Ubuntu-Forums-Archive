---
title: "[SOLVED] Update from existing installation"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by stewiehnz on 2008-02-07
Is it possible to update a installation from another installation, (now to explain)

I have virtual system set up on a 7.10 server and running several different configurations of the server on virtual machines (through virtualbox).  Instead of all of the machines downloading and updating the same updates for each of the machines, can the virtual machines download the installs from the host machine saving bandwidth.  

Of course if the packages are not on the host then they would need to download the required updates from the net.

Any thoughts would be good.

---

### Post by Partyboi2 on 2008-02-07
maybe something like [apt-cacher]("http://ubuntuforums.org/showthread.php?t=564301") could work for you.

---

### Post by stewiehnz on 2008-02-17
:)Thanks for that.:)

I have setup apt-cacher and things are running sweet as.  The host acts as the updater and the VM's in there different configurations (Ubuntu Desktop, UbuntuStudio, Servers) connect nicely and get the updates.

Even used it to solves issue's with VirtualBox and Virtual Ubuntu Servers.

PS will write HOW TO on process of VirtualBox and Virtual Servers

---

### Post by meindian523 on 2008-02-17
Please mark the thread as solved.

---


---
title: "[SOLVED] New install of 7.10 will not update."
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by stevet73 on 2008-02-18
A new i386 desktop version of 7.10 will not update. Update manager says system is up to date but Fire Fox is at 2.0.0.6 Other users systems updated Fire Fox and other Ubuntu 7.10 items.
Thank you for any help.

---

### Post by Pumalite on 2008-02-18
Post output of:
sudo apt-get update

---

### Post by stevet73 on 2008-02-18
I did run the command, but the update manager says there are no updates. 
I guess I do not fully understand the usage of this command.
sudo apt-get update
Is the any way to get the network manager to "animate" and show if traffic is going in or out?


I did some digging and found some strange settings in Fire Fox
Under Preferences->Update Fire Fox is grayed out and unelectable.
Using about:config
app.update.channel locked false
app.update.enabled locked false
both are in italics.
My links are entered as [http://\\www.somesite.com](http://\\www.somesite.com)
Where is the "\\" coming from?
I downloaded the distro direct from ubuntu.
Very confused.
Thanks again.

---

### Post by Partyboi2 on 2008-02-18
Check software sources (System>Admin>Software Sources) On the first tab make sure all are ticked except source code. Then click on the 3rd tab (updates) and make sure all boxes are ticked as well. Then close and try in a terminal (applications>accessories>terminal)
```
sudo apt-get upgrade
``` this will list the packages that can be upgraded. Hopefully you will see firefox listed to be upgraded

---

### Post by stevet73 on 2008-02-19
I will check those things out. This install was done direct from the 7.10 .iso image. Another computer was running 7.04 and upgraded to 7.10 and continues to upgade via the Internet. Has anyone else experienced this problem with the direct 7.10 install? Why would the 7.10 .iso have the older vesion of Fire Fox 2.0.0.6?
Thank you.

---

### Post by banelos on 2008-02-19
I think 2.0.0.6 was the version of Firefox out when 7.10 got released..
Just go into "System->Admin->Software Updates" as said and check it all on the first tab and do an update again.

Why Ubuntu doesn't have a notice letting know that the newest repositories are not checked when you update with none of them checked is beyond me. Not that intuitive to beginners.

---

### Post by Pumalite on 2008-02-19
You can install the latest Firefox. Download from Firefox site to Dessktop. Then, at the Terminal:

cd ~/Desktop
tar xvzf firefox-2.0.0.12.tar.gz
cd firefox
./firefox

Make sure Firefox is closed when you do this.

---

### Post by stevet73 on 2008-02-19
Thank you all!!
Going to system -->administration --> software sources and the update tab, I found all four update items unchecked. Checking Security and Recommended Updates offered 187 updates including Firefox's 2.0.0.12. I am not sure why this .iso distro came with those unchecked. 7.04 updated without having to manually intervene. Maybe it is a control and security thing, but I wish it was documented better. The update issue is resolved.
The "\\" issue was my mistake. - Resolved.
Is there an "animated" indicator of data transmissions available for the panels?
An icon "animation" like Systems Internals' Process Explorer for Windows would be nice too.
Thank you all again.

---


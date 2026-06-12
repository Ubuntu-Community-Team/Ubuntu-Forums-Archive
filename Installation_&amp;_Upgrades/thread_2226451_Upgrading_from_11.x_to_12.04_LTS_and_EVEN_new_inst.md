---
title: "Upgrading from 11.x to 12.04 LTS and EVEN new install fails with &quot;cannot read linux h"
date: 2014-05-27
forum: Installation &amp; Upgrades
---

### Post by jan-gebauer on 2014-05-27
Dear all,

let me shortly intrduce myself as I'm new in this forum. I'm in academia and teaching.
I have to quickly update our old linux 11.x system to "still"s supported version of Ubuntu.
12.04 LTS is prefered as 14.04 ist still to fresh to be supported by all the specialised scientific software.

So it's 20 computers to update...

I tried a simple update via Updatemanager, I tried sudo apt-get upgrade and a update via LIVE-USB. All to the same effect. I get a broken grub stating:
Error:Cannot read the linux header
Error: you need to load the kernel first

I'm not an expert in GRUB so I choose "delete Ubuntu and reinstall", but even this didn't not alter the problem.
I tried to use "Boot repair disk" with no success.
I cannot format the whole system, as there is an active Windows partition which is needed by my colleagues...

Any tipps how I could solve the problem for the affected machines (3 so far) and proceed in the most effective way for the others(meaning less hands-on-time per machine?)

Here is the Bootinfo paste:
[http://paste.ubuntu.com/7529292/](http://paste.ubuntu.com/7529292/)

thanks for any ideas/hints/tipps and solutions.
Jan

---

### Post by ubfan1 on 2014-05-27
linux headers???? Seems like some driver  recompile is failing.  Try booting in recovery mode to see if that works.  The boot-repair info indicates the 12.04.4 install happened (on the machine you ran it on).  What hardware (video, wireless, etc.) do you have?

---

### Post by jan-gebauer on 2014-05-28
Can't boot in recovery it's the same problem. Can also not isntall 14.04, same problem. The hardware specs I have to check. It's not wireless though and a liveCD works without problems...EDITH: and of course: Thanks for the reply!

---

### Post by jan-gebauer on 2014-05-28
Update: When I delete the whole extenden partition for Ubuntu and reinstall 12.04 it works. However, I do not have any mouse support (PS/2) in the installed version (in contrast to the LiveCD)

---

### Post by ubfan1 on 2014-05-28
Take a look at [http://ubuntuforums.org/showthread.php?t=2178803](http://ubuntuforums.org/showthread.php?t=2178803) to see some diagnostic things to run.  Maybe open a new thread for the ps2 mouse.

---

### Post by jan-gebauer on 2014-05-28
Thanks, I probably will.
Would be still great to get an solution for the original "upgrade" problem, as there are 10 more computer to upgrade.
I guess from my little experiment, it should have something to do with the partitions...
The old system had 3 partitions in an extended partition (Swap, System, Data) the new Ubuntu seems to use only two partitions.
Could the error be there?

---

### Post by ubfan1 on 2014-05-28
More likely the problem is related to the obsolete nature of the 11.x system.  I see a similar issue over on askubuntu starting from 13.10 (no solutions there yet, but check [http://askubuntu.com/questions/473585/how-to-solve-unmet-linux-headers-dependencies](http://askubuntu.com/questions/473585/how-to-solve-unmet-linux-headers-dependencies)

---

### Post by ubfan1 on 2014-05-29
I have seen some other problems regarding this.  Taking a look at my upgraded 14.04 system, I see many obsolete packages, including kernel packages. Take a look at [http://askubuntu.com/questions/473996/how-do-i-remove-obsolete-packages-after-upgrading-to-14-04](http://askubuntu.com/questions/473996/how-do-i-remove-obsolete-packages-after-upgrading-to-14-04)  
and [http://askubuntu.com/questions/286947/obsolete-packages-vs-orphaned-packages](http://askubuntu.com/questions/286947/obsolete-packages-vs-orphaned-packages)
You will need to install deborphan and aptitude, but they might help out.

---


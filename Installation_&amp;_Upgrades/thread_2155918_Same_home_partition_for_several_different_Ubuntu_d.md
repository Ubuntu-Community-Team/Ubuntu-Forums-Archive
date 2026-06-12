---
title: "Same /home partition for several different Ubuntu distros?"
date: 2013-06-19
forum: Installation &amp; Upgrades
---

### Post by Connelley on 2013-06-19
Is it OK (safe) to use the same /home partition when installing another Ubuntu distro?   Say using /home of 12.04 when installing 13.04.

---

### Post by oldfred on 2013-06-19
If you are upgrading yes. But if you are dual booting and continuing to dual boot you may eventually run into issues. Applications are designed to upgrade so all the software may add new settings in the new version. But then the old version may have problems. 
Generally best to not share.

If multi-booting you can create shared data partitions.
       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

### Post by Connelley on 2013-06-20
Thanks, oldfred.    I'll cease and desist!!

---

### Post by sanderj on 2013-06-20
> **Connelley said:**
> Is it OK (safe) to use the same /home partition when installing another Ubuntu distro?   Say using /home of 12.04 when installing 13.04.

I always do that, without problems. Oh, wait, one problem: Chrome can complain a profile was created by a newer version.

---


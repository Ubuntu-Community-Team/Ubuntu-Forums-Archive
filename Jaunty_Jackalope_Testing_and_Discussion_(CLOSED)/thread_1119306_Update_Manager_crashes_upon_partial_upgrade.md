---
title: "Update Manager crashes upon partial upgrade"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by trot2millah on 2009-04-07
I was running a partial upgrade just now, and the little Distribution Upgrade client has crashed multiple times after checking the cache and fetching file packages.  It appears to crash after it has downloaded all of the needed package files, but I am not sure why.  The only relevant message I might have is:
```
ubuntu /USR/SBIN/CRON[9263]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
```

But, I am not sure if that is out of the ordinary at all.  Any help?

---

### Post by trot2millah on 2009-04-07
OK I ran it again with terminal and here is the problem I ran into (I think it has something to do with python):
```
ERROR:root:not handled expection:
Traceback (most recent call last):

  File "/usr/bin/update-manager", line 100, in <module>
    controler.doPartialUpgrade()

  File "/usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeController.py", line 1590, in doPartialUpgrade
    if not self.doDistUpgrade():

  File "/usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeController.py", line 965, in doDistUpgrade
    self.enableApport()

  File "/usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeController.py", line 959, in enableApport
    shutil.copy("etc-default-apport","/etc/default/apport")

  File "/usr/lib/python2.6/shutil.py", line 88, in copy
    copyfile(src, dst)

  File "/usr/lib/python2.6/shutil.py", line 52, in copyfile
    fsrc = open(src, 'rb')

IOError: [Errno 2] No such file or directory: 'etc-default-apport'

ERROR:root:failed to import apport python module, can't report bug: No module named python_hook
none

```

---

### Post by Languid Heap on 2009-04-07
I had the same problem. I resolved the problem by opening Synaptic and manually marking for removal the offending program (libopal3.4.2). As soon as I did that, Synaptic seemingly picked up where the Partial Upgrader utility had left off and automatically marked the upgrade packages.

No ideas about the crashing partial upgrader though... That was the first time I've encountered that tool.

---

### Post by trot2millah on 2009-04-08
> **Languid Heap said:**
> I had the same problem. I resolved the problem by opening Synaptic and manually marking for removal the offending program (libopal3.4.2). As soon as I did that, Synaptic seemingly picked up where the Partial Upgrader utility had left off and automatically marked the upgrade packages.

No ideas about the crashing partial upgrader though... That was the first time I've encountered that tool.

Removing libopal manually solved the problem, thanks a lot for the help!

---

### Post by nanonils on 2009-04-09
Just so I can follow you guys here and learn something: how did you figure out that libopal3.4.2 is the problem? Anyways, I found this threat googling for "ubuntu jaunty parital upgrade crash" and thank you, your solution worked for me, too!

---

### Post by zika on 2009-04-10
while we are at this subject: should I remove libindicate0 since I have libindicate1 installed ... ?

---

### Post by Languid Heap on 2009-04-10
Nanonils, my process was that I had tried to run the Partial Upgrade several times. It crashed each time, so I decided to see if I could use Synaptic to manually upgrade the packages listed in the Partial Upgrade utility. The first package listed in the utility was libopal3.4.2 and fortunately, the first thing I tried worked.

Glad it worked for everyone else too!

---

### Post by ZombiekE on 2009-04-18
In my case it was crashing and I couldn't get to install many packages. So I went to synaptic as it's been said in this thread and just marked all updates and updated. Then I reloaded to see if there were any new packages and updated again. Now I can open the update manager and everything works fine.

---


---
title: "Problem with update manager"
date: 2015-08-04
forum: Installation &amp; Upgrades
---

### Post by majid9 on 2015-08-04
i had a problem when i run the update manager on my ubuntu 12.04 lts and i thook this screenshot.
[IMG]http://ubuntuforums.org/asset.php?fid=259997&uid=1994813&d=1438670146[/IMG]
 then i tried to fllow the instructions that appear on the screen but there is a problem like this.
[IMG]http://ubuntuforums.org/asset.php?fid=259998&uid=1994813&d=1438670157[/IMG]

konan@konanserver:~$ sudo apt-get install -f
[sudo] password for konan: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
 please can help me?

---

### Post by dino99 on 2015-08-04
you seems using more than one updating process at once, which is not allowed

---

### Post by majid9 on 2015-08-04
> **dino99 said:**
> you seems using more than one updating process at once, which is not allowed

i try to open Ubuntu Software Center to see whether or not there  activity is in process and there's one activity who does not progress  finished then i try to cancel but the process is long, so what should i  do?

---

### Post by dino99 on 2015-08-04
you can kill that zombie process from system-monitor (install it if not yet done)

---

### Post by majid9 on 2015-08-04
> **dino99 said:**
> you can kill that zombie process from system-monitor (install it if not yet done)

ok i've tried it, then i try to do an update with this code:

```
sudo apt-get update
```

and at the very bottom there is this message :

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

---

### Post by ian-weisser on 2015-08-04
Yes, that's expected when the package manager did not complete.
Run the suggested command with 'sudo', let it finish, then see if Software Center works.

---

### Post by majid9 on 2015-08-04
Yeah, now my ubuntu can update, thanks all

---


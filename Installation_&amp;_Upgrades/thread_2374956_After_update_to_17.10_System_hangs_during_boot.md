---
title: "After update to 17.10 System hangs during boot"
date: 2017-10-20
forum: Installation &amp; Upgrades
---

### Post by igouy on 2017-10-20
After in place update from 17.04 desktop (Intel Q6600, NVidia GeForce 8600 GT, MS Win dual-boot), system hangs during boot


```
[FAILED] Failed to start AppArmor initialization
... 
[OK] Started GNOME Display Manager.collect and submit kernel crash signatures.... as shutdown....

```


???

---

### Post by igouy on 2017-10-22
So far I've managed to find a problem with missing NVidia packages, which led me to a networking problem seemingly caused by some resolvconf name-server mis-configuration. 

I've managed to fix the resolvconf problem enough to load the missing Nvidia packages -- but now I'm stuck at:

```
[ OK ] Started GNOME Display Manager.
[ OK ] Started Hostname Service.
```

---

### Post by dino99 on 2017-10-23
if you are login with wayland (ubuntu default) then it probably dislike your nvidia driver

---

### Post by strixtux on 2017-10-23
Did the same upgrade. Mine hangs, too. Unless I unplug all USB devices. Then it runs up fine.
Funny.

---

### Post by stuart-roebuck on 2017-11-23
Having the same problem here, "[FAILED] Failed to start AppArmor initialization." booting up today.  I think there was a kernel update yesterday before I shut down.

My laptop is an Nvidia Optimus and I was NOT running wayland, but, regardless, the wayland option comes at the login prompt and this failure happens before I get to the login.

My case fitted the problem described here: [https://askubuntu.com/questions/973765/apparmor-initialization-failed-in-ubuntu-17-10](https://askubuntu.com/questions/973765/apparmor-initialization-failed-in-ubuntu-17-10)

I applied the "sudo apt install apparmor-easyprof-ubuntu" sulution presented and then restarted.

After the first restart I didn't get to the login but the apparmor issue had been resolved.

After the second restart everything worked fine.

---


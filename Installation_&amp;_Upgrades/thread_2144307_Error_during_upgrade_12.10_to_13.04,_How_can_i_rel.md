---
title: "Error during upgrade 12.10 to 13.04, How can i relaunch the upgrade?"
date: 2013-05-11
forum: Installation &amp; Upgrades
---

### Post by TulioTesar on 2013-05-11
Hi

Today i have upgrade Ubuntu from 12.10 to 13.04 and i forgot the phpmyadmin pass. I wrote a wrong password and the upgrade was stopped while the system was updating.

I rebooted the system and i can access it but, i don't know if the upgrading finished or not.

I have launch the command:

do-release-upgrade

And get a message: "No new version available"

Thanks in advance

---

### Post by Hekabe on 2013-05-11
Try
```
cat /proc/version
```
If it says quantal near the end, you're in 12.10, if it says raring, congratulations, you installed 13.04.

---

### Post by TulioTesar on 2013-05-12
Hi, 

I relaunched de upgrade process to:

do-release-upgrade -d

but (this is a bad week) i don't know, but the PC rebooted itself and now ubuntu doesn't run. :(

Could you tell me any thread for check the boot system???

Thanks in advance for your help.

---

### Post by TulioTesar on 2013-05-12
Well,

If you launch:

do-release-upgrade -d

You will install a development version. This is a bad week. (7 days ago the problems began)

Now, at least i have a fully update unstable version of ubuntu, i don't know how i will back to stable version.

The next step, make a backup of /home/ and then, who knows... 

Thank you very much!!!!

---

### Post by matt_symes on 2013-05-12
Hi

You may have wanted to try, in this order

```
sudo apt-get update
```

```
sudo apt-get install -f
```

and if required...

```
sudo dpkg-reconfigure -phigh -a
```

That may have fixed your system for you.

I know it's after the fact, however it may help you, and others, in the future.

Kind regards

---


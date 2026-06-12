---
title: "Lubuntu 18.10 Login loop in VMware"
date: 2018-10-19
forum: Installation &amp; Upgrades
---

### Post by muj02 on 2018-10-19
I installed Lubuntu 18.10 on a VM with a Mac host using Vmware Fusion 10. I choose the no login option, but after I reboot, I get a log-in loop. I tried Ctrl+Alt+F1 to drop to a terminal, but it does not seem to work in a VM. Any assistance would be appreciated.

---

### Post by muj02 on 2018-10-23
I have reinstalled Lubuntu 18.10 in a new VM on the same host, and the same issue happens after hard reboot.

---

### Post by muj02 on 2018-10-25
I have a snapshot of the VM earlier. I restored it and tried:

```
chown username:username on .Xauthority
```

That did not work. I tried:

```
mv .Xauthority .Xauthority.bak 
```

That did not work.

Other website suggested reinstalling lightdm, however Lubuntu 18.10 does not use lightdm.

Any suggestions?

---

### Post by muj02 on 2018-10-30
I solved the issue. I had edited /etc/environment and included 

```
PATH=$PATH:/opt/java/jre/bin
``` 

that doesn't work on start up so instead I just did this:

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/opt/java/jre/bin"
```

That seemed to fix it.

---

### Post by muj02 on 2018-10-30
Also Ctrl+Alt+F3 does not work on a VM in MAC to drop to the terminal you need to do Ctrl+Alt+FN+F3.

Thanks to these websites for help:

[https://unix.stackexchange.com/questions/299147/setting-variables-in-etc-environment-not-having-an-affect-but-setting-them-in-c](https://unix.stackexchange.com/questions/299147/setting-variables-in-etc-environment-not-having-an-affect-but-setting-them-in-c)

[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1758512](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1758512)

---


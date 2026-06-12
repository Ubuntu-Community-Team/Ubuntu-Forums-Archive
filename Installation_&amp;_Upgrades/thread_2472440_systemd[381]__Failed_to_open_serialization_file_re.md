---
title: "systemd[381] : Failed to open serialization file: read only file system"
date: 2022-02-27
forum: Installation &amp; Upgrades
---

### Post by Krischu on 2022-02-27
ubuntu 18.04 LTS 32 bit

After doing an apt-get update, apt-get upgrade and posibly ap-get full-upgrade, my system doesn't boot anymore.


```
systemd[381] : Failed to open serialization file: read only file system
systemd[1]: (sd-executor) failed with exit status 1
```

Searching a bit I found it might be a snapd issue. Someone says he downgraded snapd using apt-get.
But for doing this I have  boot into at least some kind of rescue system (single user or so).

I have the following options:

Choosing the first recovery mode option results in the same error message and the system isn't getting over it.

Any help appreciated. Thanks.

EDIT: another idea: I can mount the system disk when being in the rescue mode of the hoster. Assuming snapd being the culprit, could I edit some system service configuration file to disable snapd temporarily?
EDIT: solved it. Mounted and chrooted the target disk from the rescue OS. Did the apt-get downgrade of snapd from there ```
sudo apt-get install snapd=2.32.5+18.04
```
System was booting again.

---

### Post by Krischu on 2022-02-27
Bottom line:

how can I exclude snapd from being upgraded when having to do an

apt-get full-upgrade ?

---

### Post by Tadaen_Sylvermane on 2022-02-27
[https://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package](https://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package)

Of the methods suggested there I'd stick with the apt-mark hold / unhold.

---

### Post by Krischu on 2022-02-27
Thanks. What would be then exactly the <package-name>? 

snapd
snapd-2.32.5
snapd-2.32.5+18.04

none of the above ?

---

### Post by Tadaen_Sylvermane on 2022-02-28
For the most part anytime I've messed with apt over the last several years I can't recall any time i had to specify any version numbers other than kernels. 

```
apt-mark hold snapd
```

Should work. Run the command then do an apt upgrade and see what it says. It should tell you that X package is being held I think.

---


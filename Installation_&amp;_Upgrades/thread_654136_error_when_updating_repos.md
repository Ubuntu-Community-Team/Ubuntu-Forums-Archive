---
title: "error when updating repos"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by ricolinux on 2007-12-30
I try installing vmware server using sypnatic but I run into a problem with the update for the repos  wit the following error
GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
I run apt-get update several times and I keep coming back to the same error, my UBUNTU GUTSY install works fine, except for that minor error.
I use vmware server in my XP laptop to show UBUNTU to prospective clients and I'd like to use my UBUNTU box to try other OS/XP in virtual enviroments, I don't like dual booting this box is for UBUNTU exclusively IS my Learning/Experimenting  system.
So what am I doing wrong?

---

### Post by taurus on 2007-12-30
Applications -> Accessories -> Terminal
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update
```

---

### Post by ricolinux on 2008-01-01
> **taurus said:**
> Applications -> Accessories -> Terminal
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update
```

Thanks a bunch  I'try again to install vmware server 
now that my repos are apdated

---

### Post by ricolinux on 2008-01-01
Now that  I updated all my repo list 
I Still can get synaptic to install vmware server It says I have a previous 
installation but when I try the uninstall my system say no such directory.
How can I get a clean uninstall so I can do a clean install.
Also I tried to install XEN  and now my headers show the original header/kernel  plus a copy of the XEN header/kernel
I tried the apt-get remove  but couldn't find it.
Any help l with those little problems I'l realy appreciated .
IF NOTHING ELSE I am getting very handy with the terminal
Thanks
:)

---


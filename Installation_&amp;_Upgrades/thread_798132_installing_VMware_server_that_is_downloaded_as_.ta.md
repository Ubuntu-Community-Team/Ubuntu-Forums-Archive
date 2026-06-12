---
title: "installing VMware server that is downloaded as .tar.gz"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by mitchelljj on 2008-05-17
Hi,

How do I install VMware server that is downloaded as .tar.gz.  It automatically is opened within the archive manager and within the root directory is a file called vmware-install.pl which I presume is the file that does the installation.  How do I call this file within the terminal window so that the installation is done?

Thanks,

John

---

### Post by empthollow on 2008-05-17
you should be able to run it like a script:
```
./vmware-install.pl
```
you will probably have to use sudo for that program though.
```
sudo ./vmware-install.pl
```
if that doesn't work try
```
sudo sh vmware-install.pl
```
if you get a permissions error about executing type the following and try the above again:
```
chmod +x vmware-install.pl
```

Just on a side note though, virtualbox is a great program that runs any x86 os and it's in the repositories.  You might want to check it out first as it is much easier to install and will not break with kernel updates.

---

### Post by Nopposan on 2008-06-26
Well, I wish I read about virtualbox before.  My vmware server won't work with the new kernel so I'm stuck with the old kernel after going through some trouble to update with the new kernel.

O.K., I think the bottom line is that I need to know what to do to use vmware on the new kernel.  Do I need to reinstall?  Will reinstalling vmware rewrite  the data on my old vmware allocation?

Alternatively, is there a way to get all of the important files that are on my old vmware Windows XP installation to a virtualbox Windows XP installation?  I'm willing to try virtualbox if it will allow me to avoid this problem in the future.

Thanks.

---

### Post by GSMD on 2008-06-26
Under a default install all your VMs are stored under */var/lib/vmware/Virtual Machines/* so that's what you should keep in a safe place when reinstalling vmware server. I've just upgraded 1.0.5 to 1.0.6 on my Gutsy box w/o probs uninstalling the former and installing the latter. The VMs stayed there. Just got to open them manually under the new install.

---


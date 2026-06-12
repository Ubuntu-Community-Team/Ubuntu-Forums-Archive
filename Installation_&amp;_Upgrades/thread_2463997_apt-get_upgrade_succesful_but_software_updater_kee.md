---
title: "apt-get upgrade succesful but software updater keeps insisting I upgrade"
date: 2021-06-22
forum: Installation &amp; Upgrades
---

### Post by bulgin on 2021-06-22
Hello.

New to Ubuntu 20.04

After running apt-get update and then upgrade the only odd message I receive is:
```

The following packages have been kept back:   linux-generic-hwe-20.04 linux-headers-generic-hwe-20.04 linux-image-generic-hwe-20.04
```

Then, GUI software updater keeps popping up asking me to install all the files in the attached screenshot.

1) Is this safe?
2) Why does software updater conflict with the success messages of apt-get update/upgrade?  Or is it trying to tell me I still need to do something about linux-generic-hwe-20.04 linux-headers-generic-hwe-20.04 in it's own cute way?



Thank you.

---

### Post by deadflowr on 2021-06-22
Post what the apt update/upgrade commands show.

---

### Post by MAFoElffen on 2021-06-22
And a screenshot posted as an attachment of the Software Updater popup.

---

### Post by rsteinmetz70112 on 2021-06-22
It is certainly safe to run ```
sudo apt update
``` again to see if everything has been installed. I often do it after an upgrade just to check if everything that should be installed was. 
The screenshot indicates a lot of packages still need to be installed but sometimes the GUI shows the old updates if you use a command line to update. I prefer the command line.

You then might try```
 sudo apt full-upgrade
``` and see if everything then updates. If you get a new kernel you generally want to run ```
sudo apt autoclean
``` after the upgrade.

If you are then showing packages held back you can try ```
sudo apt install -f
```

apt is a newer command than apt-get and combines the functions of a couple of older commands.  I now prefer it.

---

### Post by ajgreeny on 2021-06-22
After a new kernel installation the command you might want to run is probably 
***sudo apt autoremove***
to uninstall all but the two most recent kernels.

***sudo apt autoclean***
only removes the downloaded packages from cache; it does not remove unneeded kernels.

---

### Post by deadflowr on 2021-06-22
Oh, I missed this tidbit
> After running apt-get update and then upgrade
That's it.
apt-get upgrade does not install new packages, such as the updated kernels.
You need to run apt-get with the dist-upgrade command in order to do that.

The newer apt commands can install newer packages like kernels without needing to add dist- or other options.
Post #4 shows a few apt commands, which run much the same as apt-get does.
For a full list look at apt's man page
```
man apt
```

---

### Post by GhX6GZMB on 2021-06-22
Ithink it's a conflict between your GUI "update reminder" and the kernel versions (I've turned the thing off, to be honest).

I suspect your installation is using a 5.4.0-xx kernel, which is fine. I use it myself.
But the GUI update reminder wants you to install 5.8.0-xx instead.
Three options:
upgrade the kernel
ignore the message
disable the upgrade reminder

type uname -a in a terminal to see your current kernel version.

BTW, I always use apt update and apt upgrade followed by apt autoremove
No problems doing that.

---


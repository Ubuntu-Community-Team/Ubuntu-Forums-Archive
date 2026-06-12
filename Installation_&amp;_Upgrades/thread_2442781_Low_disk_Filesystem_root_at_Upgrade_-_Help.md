---
title: "Low disk Filesystem root at Upgrade - Help"
date: 2020-05-07
forum: Installation &amp; Upgrades
---

### Post by ro7ca on 2020-05-07
Hi,
I am new to Ubuntu, but I was able to have a dual boot (window + ubuntu) on X1 Carbon. Few days ago, I wanted to upgrade to the new OS - Fosa, but I couldn't complete the installation because of low disk space. I removed some unused files but I am still getting the error. Can anyone help me? Here is a screenshot

---

### Post by ActionParsnip on 2020-05-07
If you start with:
```

sudo apt-get clean
sudo apt-get --purge autoremove
sudo dpkg -P `dpkg -l | grep ^rc | awk {'print $2'}`

```

Then you can remove old kernels. If you can give the output of:
```

uname -a; dpkg -l | grep linux-image

```

We can get old kernels pulled off the system and free up some space.

---

### Post by Impavidus on 2020-05-07
Your root partition is almost full. It's 45GB and there's less than 1GB free space, which is not enough for temporary storage of all packages needed for the upgrade. Removing some old kernels and cache may help, but I don't expect it will clear that much space. The OS should only take about a third of that space, so most can be gained from cleaning up your documents or media files. Unless you suffer from overflowing log files. Can you investigate which files or directories take most space?

BTW, instead of posting a screenshot of your terminal, it's easier if you just copy-paste the output from the terminal to the forum. After all, it's just text. But don't forget to use code tags.

---

### Post by ro7ca on 2020-05-07
> **Impavidus said:**
> Your root partition is almost full. It's 45GB and there's less than 1GB free space, which is not enough for temporary storage of all packages needed for the upgrade. Removing some old kernels and cache may help, but I don't expect it will clear that much space. The OS should only take about a third of that space, so most can be gained from cleaning up your documents or media files. Unless you suffer from overflowing log files. Can you investigate which files or directories take most space?

BTW, instead of posting a screenshot of your terminal, it's easier if you just copy-paste the output from the terminal to the forum. After all, it's just text. But don't forget to use code tags.

Thank you; I will remove some files and then follow the steps above to  see if that helps. Is it possible to maybe re-partition again?

---

### Post by ro7ca on 2020-05-07
```

Linux youssoufj-ThinkPad-X1-Carbon-6th 5.3.0-46-generic #38~18.04.1-Ubuntu SMP Tue Mar 31 04:17:56 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
ii  linux-image-5.0.0-36-generic               5.0.0-36.39~18.04.1                              amd64        Signed kernel image generic
ii  linux-image-5.3.0-40-generic               5.3.0-40.32~18.04.1                              amd64        Signed kernel image generic
ii  linux-image-5.3.0-46-generic               5.3.0-46.38~18.04.1                              amd64        Signed kernel image generic
ii  linux-image-generic-hwe-18.04              5.3.0.46.102                                     amd64        Generic Linux kernel image


```

Hi, thank you for your help; Here is above the output

---

### Post by ro7ca on 2020-05-07
> **ActionParsnip said:**
> If you start with:
```

sudo apt-get clean
sudo apt-get --purge autoremove
sudo dpkg -P `dpkg -l | grep ^rc | awk {'print $2'}`

```

Then you can remove old kernels. If you can give the output of:
```

uname -a; dpkg -l | grep linux-image

```

We can get old kernels pulled off the system and free up some space.

Here it is; thank you

```

Linux youssoufj-ThinkPad-X1-Carbon-6th 5.3.0-46-generic #38~18.04.1-Ubuntu SMP Tue Mar 31 04:17:56 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
ii  linux-image-5.0.0-36-generic               5.0.0-36.39~18.04.1                              amd64        Signed kernel image generic
ii  linux-image-5.3.0-40-generic               5.3.0-40.32~18.04.1                              amd64        Signed kernel image generic
ii  linux-image-5.3.0-46-generic               5.3.0-46.38~18.04.1                              amd64        Signed kernel image generic
ii  linux-image-generic-hwe-18.04              5.3.0.46.102                                     amd64        Generic Linux kernel image



```

---

### Post by ActionParsnip on 2020-05-08
sudo apt-get --purge remove linux-image-5.0.0-36-generic linux-image-5.0.0-40-generic
sudo apt-get --purge autoremove

---

### Post by Holger_Gehrke on 2020-05-08
Another thing that should free up a GB or two is to remove the older revisions of snap packages that are kept as backups in case a new version of a package does not work as intended. Do 'snap list -all' to get a list of all installed snaps including the older revisions. In that list the old files should have a note in the last column calling them 'deactivated' or 'inactive' or something to that effect. You can remove those by running 'snap remove --revision n x' (x being the name of the package and n the revision number of a deactivated version from the list).

Going through your screenshot I find that these are redundant and can be removed. There might be more ...

[TABLE="class: grid, width: 500"]
[TR]
[TD]**Package**
[/TD]
[TD][B]Revision
[/B][/TD]
[/TR]
[TR]
[TD]gnome-logs[/TD]
[TD]81[/TD]
[/TR]
[TR]
[TD]krita[/TD]
[TD]54
[/TD]
[/TR]
[TR]
[TD]gnome-calculator[/TD]
[TD]544[/TD]
[/TR]
[TR]
[TD]pycharm-community[/TD]
[TD]188[/TD]
[/TR]
[TR]
[TD]skype[/TD]
[TD]118[/TD]
[/TR]
[TR]
[TD]eclipse[/TD]
[TD]40[/TD]
[/TR]
[TR]
[TD]core[/TD]
[TD]8935[/TD]
[/TR]
[TR]
[TD]core18[/TD]
[TD]1668[/TD]
[/TR]
[TR]
[TD]gnome-3-28-1804[/TD]
[TD]110[/TD]
[/TR]
[TR]
[TD]gnome-system-monitor[/TD]
[TD]127[/TD]
[/TR]
[TR]
[TD]gnome-characters[/TD]
[TD]399[/TD]
[/TR]
[TR]
[TD]gtk-common-themes[/TD]
[TD]1474[/TD]
[/TR]
[/TABLE]

Holger

---


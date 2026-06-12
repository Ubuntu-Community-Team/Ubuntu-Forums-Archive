---
title: "updates filling hard drive?"
date: 2012-10-27
forum: Installation &amp; Upgrades
---

### Post by bubblefish on 2012-10-27
Will update manager eventually fill up my hard drive? What happens after update manager downloads megabytes of files and installs them?

---

### Post by FrankT-Qc on 2012-10-27
Nah.

Three things happen : 

First, the update itself will replace the files on your computer and not just cumullate all the verions. Sometimes, this adds a little space, sometimes, it's actually smaller.

Second : The updating process involves "packages". Your package manager keeps a cache of what you download. This does take a little room, but old packages eventually get flushed. There is also a size limit. 
If you look at the file /etc/apt.conf.d/20archive you'll see a parameter called "APT::Archives::MaxSize" you can set that to how big you allow your cache to grow.

Third : There is one exception : The kernel packages (their name usually start with "linux-") don't get flushed so that you can revert to old versions should the new ones not work. Even if these updates don'happen very often, it does, indeed, accumulate over time. If, like me, you have a very small boot partition, you might want, every once in a while, go and uninstall the very old versions. 

WARNING : Do not uninstall the kernel you are currently running !!! (I'm pretty sure most package tools are going to warn you if you do so, but still, better safe than sorry). If you want to know what you are running, open a command line and type "uname -a"

have fun !

---

### Post by mailc on 2012-10-27
[FONT=Liberation Serif, Times New Roman]there is a way to purge old kernels:
[/FONT]
[FONT=Liberation Serif, Times New Roman]
[/FONT]
[FONT=Liberation Serif, Times New Roman]Kernel old purge , dry run :[/FONT]
[FONT=Liberation Serif, Times New Roman]  dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get --dry-run remove[/FONT]
[FONT=Liberation Serif, Times New Roman]
[/FONT]
 [FONT=Liberation Serif, Times New Roman]Actual remove Old Kernel:[/FONT]
[FONT=Liberation Serif, Times New Roman] dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge[/FONT]


[FONT=Liberation Serif, Times New Roman]Of course one can use the Synaptic for same thing.
[/FONT]


[FONT=Liberation Serif, Times New Roman]Please wait for confirmations from more established  users before actually trying it out .
[/FONT]

---

### Post by bubblefish on 2012-11-08
Thanks for the lucid, to-the-point replies. Ubuntu 12.04 is a great OS, and the automatic updates seem to be keeping it that way.

---

### Post by Wim Sturkenboom on 2012-11-08
You can also clean the apt-get cache
```

sudo apt-get clean

```
On system with smaller hard disks (e.g. netbooks with 8GB SSD), this is advisable.

---


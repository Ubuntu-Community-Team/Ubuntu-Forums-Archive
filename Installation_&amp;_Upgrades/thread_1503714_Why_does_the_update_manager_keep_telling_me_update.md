---
title: "Why does the update manager keep telling me updates are available?"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by cfogelberg on 2010-06-07
Apt-get and Update Manager seem to be out of sync, and I can't shut the Update Manager up! If anyone can help me with this I'd really appreciate it :)

My situation is as follows: I use apt-get from the terminal to update and install applications on my computer. When I run this it tells me:

```
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```

I.e. there are no updates to install. However, the Update Manager seems to be run automatically from time to time, and it pops up and tells me that there are a whole bunch of updates to install:

[IMG]http://img694.imageshack.us/img694/3556/screenshotupdatemanager.png[/IMG]

I guess that UM is telling me about updates I already have installed. How do I synchronise apt-get and UM, or get UM to shut up?

Thanks!
Christo

---

### Post by roger_1960 on 2010-06-07
Hi

Have you clicked the "check" button in the GUI ?  I thought that this synchronised the system with the current state of updates.

---

### Post by cfogelberg on 2010-06-07
I will try that when I get home, but it seems to me that it's going to be something I'd have to keep doing, which seems a bit silly/repetitive... Is there any way to get it to do that synchronisation every time it starts up? In fact, if the button works as you suggest why isn't it doing that anyway? Does the check button just compare what's in the repositories with what UM thinks is installed?

---

### Post by efflandt on 2010-06-07
I just use regular updates and kernel 2.6.32-22 has reinstalled at least several times.  But I don't know if it is actually the same, or if they recompiled the same kernel with different options or modules due to issues people have had.

When I have installed other standard programs from the command line using apt-get, they do show up in Synaptic as installed.  But I have not done updates from command line.

---

### Post by cfogelberg on 2010-06-08
Well, I have gone to the settings thing and set it to bug me as infrequently as possible (fortnight), but still don't understand why it isn't possible to sync it with apt-get :/

---

### Post by wilee-nilee on 2010-06-08
I think it's synced I had what looked like reinstalls of a kernel last week. I also was having troubles with the server set to server for the united states, without picking, so I used the other button and let it find the quickest ping and this fixed this problem.

---

### Post by John Bean on 2010-06-08
You seem to have "locked" the version of the kernel packages, as apt-get was telling you. You can use the --ignore-hold flag of apt-get to temporarily override this, or use dpkg to change the selection settings of the package(s) concerned, or select them in synaptic and use the "Package" menu to achieve the same thing.

---


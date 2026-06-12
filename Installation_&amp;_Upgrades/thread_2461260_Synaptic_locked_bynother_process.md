---
title: "Synaptic locked bynother process"
date: 2021-04-27
forum: Installation &amp; Upgrades
---

### Post by jpaulb on 2021-04-27
Trying to install graphic card drivers with synaptic Repositories additional drivers  when I do I get a warning 
```
Error while applying changes
pk-client-client-error-quark:E: Could not get lock /varlib/dpkg/lock-frontend it is held by process 2638 (synaptic) 
E: unable to acquire the dpkg frontend lock(/varlib/dpkg/lock-frontend)

```

---

### Post by Xian on 2021-04-27
As a bypass close down Synaptic and instead open the Software Updater application.

Click on Settings and then go to your Additional Drivers tab.

---

### Post by jpaulb on 2021-04-28
I did a couple reboots same issue.
I have a launcher on the desktop for software-properties, tried that and the warning went away.
/usr/bin/software-properties-gtk --open-tab=4

There was a warning that the nVidia drivers could not be installed; but after another reboot they are in operation. :confused:

solve until the next time ;) or until Ububtustudio 24.04 is available.

---


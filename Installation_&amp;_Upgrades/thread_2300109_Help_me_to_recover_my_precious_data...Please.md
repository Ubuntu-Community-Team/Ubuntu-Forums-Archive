---
title: "Help me to recover my precious data...Please"
date: 2015-10-23
forum: Installation &amp; Upgrades
---

### Post by pulkit3 on 2015-10-23
I recently Installed Ubuntu on my windows 7 Laptop and used the replace option during installation.
Now all my partitions are gone and there is a single drive of 320GB. All data is gone too.
I referred following thread but I an not sure about the solution to the problem given there [http://ubuntuforums.org/showthread.php?t=1879640](http://ubuntuforums.org/showthread.php?t=1879640)


How to recover all the data back.
Is there any free method?

Someone please help me.
I need that data desperately.

Someone please give me the contact information of rohyt in the above link.

---

### Post by tgalati4 on 2015-10-23
Welcome to the forums.  That is unfortunate.  "Replace" means delete all data on the disk and install Ubuntu.

Proceed carefully.  There is a chance of recovery as long as you don't make the situation worse.  Get yourself an external USB drive of 500 GB or greater to receive the data.  

Some reading:  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Do this from another computer or in a Live Session.  Boot your computer with a LiveUSB stick and open a terminal:

```
sudo apt-get install testdisk
testdisk
```

Don't reboot, because you are running in RAM and you will have to reinstall *testdisk* if you do.

---

### Post by QIII on 2015-10-23
There is some hope, but only some.

To improve your chances, turn the machine of and use a different machine to wait for help.

The more you use that machine, the less likely a positive outcome.  Using the machine will write over more and more of your data.

---


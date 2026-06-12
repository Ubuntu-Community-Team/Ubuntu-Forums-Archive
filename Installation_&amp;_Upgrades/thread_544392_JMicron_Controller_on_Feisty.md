---
title: "JMicron Controller on Feisty"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by rennen01 on 2007-09-06
Finally upgraded my daily workstation to Feisty.  I was having that JMicron issue that several people are having.  It is still really slow on bootup.

Had to uninstall almost everything in Edgy before I upgraded, including Automatix and nvidia drivers.

---

### Post by rennen01 on 2007-09-25
If anyone else is having the slow boot up issues due to JMicron, the solution for me was to compile a brand new kernel.  I am now at 2.6.22.7.  Everything works again.

If you are not comfortable doing that, I suggest you use the  [**_*kernelcheck script*_**](http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel+thread).

That is an automated script that downloads, compiles, and installs the latest kernel for you.

Also you may have to reconfigure xserver after  you restart the computer
```
dpkg-reconfigure xserver-xorg
```

Hope this helps.

---

### Post by master_kernel on 2007-09-26
> **rennen01 said:**
> If anyone else is having the slow boot up issues due to JMicron, the solution for me was to compile a brand new kernel.  I am now at 2.6.22.7.  Everything works again.

If you are not comfortable doing that, I suggest you use the  [**_*kernelcheck script*_**](http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel+thread).

That is an automated script that downloads, compiles, and installs the latest kernel for you.

Also you may have to reconfigure xserver after  you restart the computer
```
dpkg-reconfigure xserver-xorg
```

Hope this helps.
The current forum support thread for KernelCheck can be found here:[http://ubuntuforums.org/showthread.php?t=556726](http://ubuntuforums.org/showthread.php?t=556726)

I will soon add the dpkg-reconfigure option to KernelCheck.

master_kernel, author of KernelCheck

---

### Post by rennen01 on 2007-09-26
That would be useful mater_kernel.

Since there are so many problems with the JMicron Controller, I hope the people that are having these problems read this.  Since I installed the new kernel, my bootup time is now around 30 seconds.  :)

---

### Post by master_kernel on 2007-09-27
Glad it worked!

I'll include it in the next release.

---


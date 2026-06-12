---
title: "unable to write in windows hard drive partitions"
date: 2019-05-11
forum: Installation &amp; Upgrades
---

### Post by rogers9798 on 2019-05-11
After recent package update in Ubuntu 18.04, I am unable to write in my windows partition.

---

### Post by oldfred on 2019-05-11
Are you sure it was not an update in Windows?
Windows fast start up sets hibernation flag which prevents the Linux NTFS driver from mounting NTFS partitions in default read/write mode. You may be able to manually mount in read only mode.
Windows will turn fast start back on with updates, even if you had it off before.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by rogers9798 on 2019-05-19
I solved it. It was due to unproper shutting down of windows 10.
I did a full shutdown and my problem solved.

---

### Post by rogers9798 on 2019-05-19
Thanks for the help btw.

---

### Post by oldos2er on 2019-05-20
Would you please mark your thread 'Solved' under Thread Tools at the top of the page? Thanks.

---


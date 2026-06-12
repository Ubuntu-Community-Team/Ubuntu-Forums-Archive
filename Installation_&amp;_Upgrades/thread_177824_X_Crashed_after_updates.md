---
title: "X Crashed after updates"
date: 2006-05-16
forum: Installation &amp; Upgrades
---

### Post by thirdmusketeer on 2006-05-16
Hi Guys

I did some updates, and after reboot my X doesn't start and gives me fatal error 104. In the past I would normally reinstall things but this time I am determined to find out how to solve this problem.

It says to check /var/log/Xorg.0.log

unfortunately I don't know what to check there. Could any of you experts help me debug the crash.


Thanks

---

### Post by bluevoodoo1 on 2006-05-16
sudo gedit /var/log/Xorg.0.log

Look for lines with (EE) as those are errors. You could also post that file here if you're looking for more help.

---

### Post by thirdmusketeer on 2006-05-16
Thanks, I am running the OS in VMware, but that shouldn't have been an issue because all day long it was working perfectly, making me happier by the minute.

Anyway it seems that there are very few EE , but I don't know how to remove them. Instead of pasting the error, the following link contains the log file.

[http://vlsi.colorado.edu/~sohail/Xorg.0.txt](http://vlsi.colorado.edu/~sohail/Xorg.0.txt)

---

### Post by thirdmusketeer on 2006-05-17
Hi guys,

It seems that after the update the module kbd and mouse have been replaced with some other modules, and the following link suggests to update the xorg.conf with the new modules, what are the new modules and how do I do that.

[http://www.linuxforums.org/forum/linux-desktop-x-windows/28670-x-wont-start-failed-initialize-core-devices.html](http://www.linuxforums.org/forum/linux-desktop-x-windows/28670-x-wont-start-failed-initialize-core-devices.html)

Thanks

---


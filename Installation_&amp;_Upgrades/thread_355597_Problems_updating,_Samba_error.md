---
title: "Problems updating, Samba error"
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by ruialexbarbosa on 2007-02-07
I tried to do some updates but I got the following error: Error: Brokencount»0

Through Synaptics found out that it's SAMBA, but it won't let me uninstall... I tried through the terminal and all I got was this:

Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  samba
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
Need to get 0B of archives.
After unpacking 7250kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 92274 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing samba (--remove):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)


Can you please help?

Thanks

---

### Post by ruialexbarbosa on 2007-02-08
Please???

---

### Post by ruialexbarbosa on 2007-02-09
bump... Please again...?

---

### Post by dannyboy79 on 2007-02-09
why did you answer 'y' when it asked you if you wanted to remove samba? do you want to remove it? if you do, than I would delete the dangling symlink by doing sudo rm /etc/rc2.d/S91samba. after I checked my /etc/rc2.d/ folder I don't have any S91samba simlink. I only have an S20samba and that's it. so I am guessing you just need to delete that bad symlink and then try to remove samba again and it should remove it. then reinstall it if you want.

---

### Post by ruialexbarbosa on 2007-02-09
Thanks, that got rid of it... Why did I get in trouble? Why does this happen?

Regards

---

### Post by dannyboy79 on 2007-02-09
i can't tell you why a bad symlink would have been created. r you sure you didn't create it some how on accident? i don't have a S91samba on either of my machines.

---


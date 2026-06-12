---
title: "Rsync errorafter Rsync upgrade on 7.10"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by alxlabs on 2008-05-19
An error shown below happens after updating rsync to ver. rsync_2.6.9-5ubuntu1.1_i386.deb. Following appears after any installation using apt-get or "Add/Remove" from the main menu. Any ideas?(Ubuntu: 7.10)

```

Setting up rsync (2.6.9-5ubuntu1.1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing rsync (--configure):
 subprocess post-installation script returned error exit status 1
Setting up gwget (0.99-0ubuntu1) ...

Errors were encountered while processing:
 rsync
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by alxlabs on 2008-05-20
OK, Figured it out myself.

For those who will get trapped into same thing...

Problem was that I've added some debian repositories to my /etc/apt/sources.list which triggered debian version of sysv-rc installed

How to check:

run "sudo apt-cache policy sysv-rc"
If you see something like in the first couple of lines
```

sysv-rc:
Installed: 2.86.ds1-38

```

ie version name without "ubuntu" at the end (2.86.ds1-38 instead of 2.86.ds1-14.1ubuntu31) then you've hit same problem.

How to resolve:

1. run "sudo vi /etc/apt/sources.list" and remove all non-ubuntu repositories.
2. Go to /var/cache/apt/archives and delete all the files - these are  files downloaded by package manager from the repositories, who knows what  else was downloaded from the wrong ones.
3. Make sure that yoou did not pickup debian's rsync as well - remove and install rsync - run "sudo apt-get remove rsync" and then "sudo apt-get install rsync", ignore rsync error message at the end.
4. run "sudo synaptic", then navigate to "sysv-rc", select it, then go to "package" menu, click on "force version", select ubuntu version, smth.like 2.86.ds1-14.1ubuntu31 then click on "force version", then click "Apply" (big green checkmark button under the menu line :) ). Problem should be solved after that.

---


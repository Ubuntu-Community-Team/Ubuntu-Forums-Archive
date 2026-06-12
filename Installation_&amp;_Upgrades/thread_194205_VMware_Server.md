---
title: "VMware Server"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by gharz on 2006-06-11
i'm trying to install vmware server and followed the instructions based on this thread

[http://www.ubuntuforums.org/showthread.php?t=183209]("http://www.ubuntuforums.org/showthread.php?t=183209")

but i'm getting an error which was not addressed by the thread... though were posts which states the same problem as mine but the solution was not posted or even mentioned how to.

```
sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.
```

before following the thread, i installed vmware-player from synaptic. eventually, after reading the procedures from the thread, i completely remove vmware-player from synaptic as well. uncompressed the .tar.gz file from vmware and did the formal installation. unfortunately, the problem shows up.

how can i complete remove the previous installation? how do i install vmware server?

need help.

i'm currently running Ubuntu 6.06 Dapper
'uname -r' is 2.6.15-23-386.

i've also downloaded all depencies for vmware (ie. build essentials, gcc-3.4, xinet & linux-headers.)

---

### Post by judgekaster on 2006-06-11
try to remove the directory /etc/vmware or make a backup

```

sudo mv /etc/vmware /etc/vmware-bak

```

---

### Post by Fabiano Shark on 2006-06-15
Look if it can help 
[http://www.4newbies.com.br/arts_view.php?id=75](http://www.4newbies.com.br/arts_view.php?id=75)

---

### Post by soongwoo on 2006-06-15
I've installed VMware as you do.
And the kernel is upgraded to 2.6.15-23-386. So I'm looking for
the proper solution to run VMware under new kernel.

Do you mean that
 - install new linux header "apt-get install linux-headers-`uname -r`"
 - and run "/usr/bin/vmware-config.pl"

Am I right?

soongwoo

---

### Post by bluevoodoo1 on 2006-06-15
[QUOTE=judgekaster]try to remove the directory /etc/vmware or make a backup

```

sudo mv /etc/vmware /etc/vmware-bak

```[/QUOTE]

I had the same issue. Removing the /etc/vmware directory solved it.


[QUOTE=soongwoo]I've installed VMware as you do.
And the kernel is upgraded to 2.6.15-23-386. So I'm looking for
the proper solution to run VMware under new kernel.

Do you mean that
 - install new linux header "apt-get install linux-headers-`uname -r`"
 - and run "/usr/bin/vmware-config.pl"

Am I right?

soongwoo[/QUOTE]

See if this helps. [http://ubuntuforums.org/showthread.php?t=197215](http://ubuntuforums.org/showthread.php?t=197215)

---


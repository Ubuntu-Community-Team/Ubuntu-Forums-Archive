---
title: "help with vmware!"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by hsalgado on 2007-01-29
Hi, I finally installed vmware and I could install winxp and even share files... but when I restarted the system I could not run vmware!

This is what I got:  

[I]  vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.
[/I]

When I run the command I obtain:
[I]
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Server
[/I]

Is there any way I can reconfigure vmware without losing my previous winxp installation?

Thanks for any help!

---

### Post by mizar001 on 2007-01-29
I think you can't lose your xp guest installation. You must only configure vmware for the host machine ('ubuntu' i presume).

Have you installed xp as a real phisical partition or a vmx file ?

If you are unable to stop vmware, kill the service, and do the suggested reconfigure. Hence restart vmware.

---

### Post by hsalgado on 2007-01-30
Thanks a lot for your help.  I had to delete the vmplayer files and reinstall vmware.  Now it works (very slowly though).  I didn't lose the installation of winxp in the vmx file when I reinstalled vmware.    Thanks a lot for your help once more time.

---

### Post by mizar001 on 2007-02-01
I appreciate the vmware speed when having at least 1 gb of ram. Of course if you have a quad core processor and 4/8 gb ram, you'll appreciate better the comfort to have virtual machines running every time.

Very strange, my oracle teacher has a mobile pc and it runs several v. machines at the same time, 5 or 6. I don't know what can be it's configuation, but it's amazing.

---


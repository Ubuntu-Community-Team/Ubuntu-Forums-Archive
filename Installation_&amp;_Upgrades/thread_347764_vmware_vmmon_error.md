---
title: "vmware vmmon error"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by CameronCalver on 2007-01-27
Hello i tryed to install vmware player from source and from the the repos but i keep getting this error
```
hat is the location of the directory of C header files that match your running 
kernel? [/lib/modules/2.6.17-10-386/build/include] 

Extracting the sources of the vmmon module.

tar: /usr/lib/vmware-player/modules/source/vmmon.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
Unable to untar the "/usr/lib/vmware-player/modules/source/vmmon.tar" file in 
the "/tmp/vmware-config1" directory.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and 
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

cameron@ubuntu:~$ 

```

---

### Post by dreamwall on 2007-02-10
Maybe [this]("http://blog.gnu-designs.com/2006/08/07/fix-vmware-vmw_have_epoll-error-message-with-current-distributions/") will help you.

---


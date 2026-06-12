---
title: "nvidia-detector forces dpkg to abort"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by michael37 on 2009-03-13
...while trying to upgrade kernel.

FYI: I don't have Nvidia card.
```

Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.28-8-generic                                                              
 *  fglrx (8.543)...                                                                                                               fglrx (8.543): Already installed on this kernel.
                                                                                                                            [ OK ]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 2, in <module>
    import NvidiaDetector
ImportError: No module named NvidiaDetector
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.28-8-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.28-8-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.28-8-generic; however:
  Package linux-headers-2.6.28-8-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
were encountered while processing:
 linux-image-2.6.28-8-generic
 linux-restricted-modules-2.6.28-8-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
 linux-image
 linux-headers-2.6.28-8-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by michael37 on 2009-03-14
Not very helpful.  
[https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/331675](https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/331675)

---


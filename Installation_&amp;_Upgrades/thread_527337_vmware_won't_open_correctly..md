---
title: "vmware won't open correctly."
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by ntaylor0909 on 2007-08-16
I am having an issue where Vmware server won't start unless I run it as Sudo. When I run it as my usual user it opens in the task bar and then closes. Here is the output I get when I run it in terminal:

/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
Unable to alloc client: Cannot open file "/home/nathan/.vmware/preferences": Permission denied.



VMware Server Error:
VMware Server unrecoverable error: (vmui)
Unable to alloc client: Cannot open file "/home/nathan/.vmware/preferences": Permission denied.

A log file is available in "/tmp/vmware-nathan/ui-7523.log".  Please request support and include the contents of the log file.  
To collect files to submit to VMware support, run vm-support.
We will respond on the basis of your support entitlement.



A little background would be that I installed the 2.6.22 kernel to get my wireless card(Intel 4965)  working. It worked, but vmware stopped working on the new kernel and so did my sound, so I am booting into the 2.6.20 kernel again, but I am getting this issue. Any help would be appreciated.

---

### Post by ntaylor0909 on 2007-08-20
Well, I figured it out for myself. I am a bit of a nood, so it took me a while, but I figured out that all I had to do was give myself permissions to the file. I ran chown, and It am back in business. Thanks anyways.

---


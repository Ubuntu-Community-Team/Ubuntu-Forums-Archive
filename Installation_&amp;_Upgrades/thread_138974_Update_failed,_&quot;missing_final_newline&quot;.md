---
title: "Update failed, &quot;missing final newline&quot;"
date: 2006-03-02
forum: Installation &amp; Upgrades
---

### Post by heri on 2006-03-02
(Sorry, I make new thread here)

I had a notification on the applet (the red circle) an update of ubuntu-docs is available: The Ubuntu Quick Guide version 5.10-6.3

When I proceed with install the update, it was failed showing this message:

E: /var/cache/apt/archives/ubuntu-docs_5.10-6.3_all.deb: files list file for package `gcc-4.0' is missing final newline

Tried to reload synaptic, but update still failed.

Another update came up, and when I tried, the same error remains.
 
Pls help.

---

### Post by Xian on 2006-03-02
Remove that local cache of package and try the upgrade again.

$ sudo rm -f /var/cache/apt/archives/ubuntu-docs_5.10-6.3_all.deb

---

### Post by heri on 2006-03-03
Thanks for the prompt reply.

I've removed the local cache, unfortunately it's still not working. Tried from synaptic also not working.

Is there anything to do with 'gcc-4.0' as shown in the error message ?

All the best.

---

### Post by Xian on 2006-03-03
Read this [THREAD](http://ubuntuforums.org/showthread.php?t=12737) and see if it helps.

---

### Post by heri on 2006-03-03
Thank's, 
The workaround works for that particular update.

Tried to install gweled from Synaptic, it failed again with the similar error message:

E: /var/cache/apt/archives/gweled_0.6-2_i386.deb: files list file for package `gcc-4.0' is missing final newline

Tried to reinstall gcc-4.0, and still not working.

Should I remove all the files in /var/lib/dpkg/info ?

---


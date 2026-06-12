---
title: "Netbeans cause synaptic problem"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by sfed on 2007-06-24
I'm aware of that issue and I remember that I have solved it on my desktop pc somehow but I don't remember how.Anyway, when I try to open synaptic I get this error message

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

When I'm running from terminal ```
 sudo dpkg --configure -a
``` i get this message

```
Setting up netbeans5.5 (5.5-0.59) ...

This package is an installer package, it does not actually contain the
NetBeans IDE.  You will need to go download the IDE from:

From the NetBeans IDE 5.5 Download page:
http://www.netbeans.info/downloads/all.php?b_id=2323 

Select the English(en) tgz Download Archive Distribution 82.8 MB
http://www.netbeans.info/downloads/start.php?f_id=13710&lang_id=1

and place the file in /tmp (with root.root ownership) now.


[Press RETURN to try again, 'no' + RETURN to abort] 


```

I downloaded the file ,place it in /tmp (without root.root ownership) but nothing happened.

It all started when I tried to download NetBeans from automatix when suddenly it gave me an md5 error and won't continue installation.

---

### Post by sfed on 2007-06-24
Ok I type "no" at terminal  and I was able to remove netbeans from synaptic.But now I have another problem.When I load azureus it shutdowns immediately.I uninstall jdk and azureus reinstall  both of them but nothing happened

---


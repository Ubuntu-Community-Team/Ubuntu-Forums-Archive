---
title: "Cannot open Synaptic"
date: 2005-10-26
forum: Installation &amp; Upgrades
---

### Post by sargonx on 2005-10-26
Well, I was trying to install java manually while I installed some software from synaptic. When my manual installation at the console required shutting down synaptic, I did it and carried on. The java installation didn't work, I should probably try harder, but that's not the point. Some minutes later, I tried to reopen synaptic and it wouldn't open. So, I restart Ubuntu twice, even shutting off the computer, and it won't open either. When I run sudo synaptic in the console, after typing the password, I get "Segmentation fault", and that just is it.

Any suggestions? I'm a bit despaired at the prospect of being unable to use synaptic anymore.

---

### Post by Xian on 2005-10-26
Review /var/log/dpkg.log to see what you have installed or removed recently that might impact the performance of Synaptic. If you find any suspicious culprits undo those actions. You could also purge Synaptic (and deps) and then do a reinstall to see if that might help.

$ sudo apt-get remove --purge synaptic

---

### Post by sargonx on 2005-10-28
Thanks for the help. I reviewed the dpkg.log, no suspicious content. I uninstalled and reinstalled synaptic with apt-get, purging dependencies and even deleting the synaptic package from /var/cache/apt so that apt would download it again. Yet, it won't start. Anyway, thanks xian for the help! Any radical suggestions?

Seems I will soon be learning to use apt-get : ).

---

### Post by sargonx on 2005-10-29
After upgrading some software (including some libraries) it worked again. Ubuntu really works : ).

---

### Post by Xian on 2005-10-29
Sorry, but I lose my place sometimes. :)

If this happens again with an application use apt to retrieve any missing deps that might have "gone missing". This can happen for a variety of reasons and is a sure way to make certain there are no missing libs.

```
$ sudo apt-get build-dep packagename
```

---


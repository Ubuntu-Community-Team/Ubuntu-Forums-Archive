---
title: "Upgrade - update unresolved dependencies problem"
date: 2012-11-28
forum: Installation &amp; Upgrades
---

### Post by rabidmachine9 on 2012-11-28
Hello, I am having problems with updating - upgrading my system (Ubuntu 12.04)
My assumption is that an upgrade wasn't completed successfully and now some important packages are missing.

Among them mount and some others.
I'm afraid the computer might not be able to mount next time I try to boot.

Any help will be extremely appreciated...

This is the output of an sudo apt-get upgrade command(and no apt-get install -f  won't solve the problem):
```
dm@dm-GA-990XA-UD3:/var/lib/apt$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initscripts : Depends: mount (>= 2.11x-1)
               Depends: mountall (>= 2.28)
               Recommends: psmisc but it is not installed
               Recommends: e2fsprogs but it is not installed
 upstart : Depends: mountall
           Depends: ifupdown (>= 0.6.10ubuntu5)
E: Unmet dependencies. Try using -f.
```

---


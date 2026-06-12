---
title: "Upgrading to Ubuntu 10"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by mmistroni on 2010-06-06
Hello all, 
 i am trying to upgrade to Ubuntu 10, but when i start the process i keep on getting the following error
```

An unresolvable problem occurred while calculating the upgrade:
The package 'skype-common' is marked for removal but it is in the removal blacklist.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

```


could anyone help?

w/kindest regards
 marco

---

### Post by bweinel on 2010-06-06
Just a thought here.. but have you tried starting up your system, going to a terminal windows, and then removing skype-common with 'sudo apt-get remove skype-common' before trying the install? I would think that might do the trick.

cheers Bill

---

### Post by mmistroni on 2010-06-06
Hello Bill
 yes, after a while i followed what you said and it worked..

thanks and regards
 marco

---

### Post by bweinel on 2010-06-06
Good deal Marco. I'm glad to hear that got it solved.

cheers Bill

---


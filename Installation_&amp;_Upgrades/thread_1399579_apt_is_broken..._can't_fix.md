---
title: "apt is broken... can't fix"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by N9CQS on 2010-02-05
I am running Ubuntu 8.04.2 desktop.  64 bit. 

I am trying to install a mail server system.  In trying to install dovecot, I messed it up, and now apt-get won't remove it, and it won't install it.  It is stuck.  Neither will synaptic fix it.  

I've tried a variety of things that I found on the web, including getting into the apt files and adding things like "exit 0" and "set -e".  I have repeatedly used apt-get, aptitude and synaptic to try to both uninstall and reinstall the things.  I want to install the following:

dovecot-common
dovecot-imapd
dovecot-pop3d

Any help would be appreciated.  Thanks.
Jeff

---

### Post by Barriehie on 2010-02-05
Have you tried:
```

sudo dpkg --force-remove-reinstreq dovecot-common dovecot-imapd dovecot-pop3d

```

Barrie

---

### Post by mushwars on 2010-02-06
had the same problem.

[http://ubuntuforums.org/showthread.php?t=1394636](http://ubuntuforums.org/showthread.php?t=1394636)

here is the solution.

[https://answers.launchpad.net/ubuntu/+question/14619](https://answers.launchpad.net/ubuntu/+question/14619)

(scroll down the answer is at the bottom, you will have to nano a file in your apt dir.)

---

### Post by N9CQS on 2010-02-06
Thank you so very much!  I was able to get Dovecot off, then reinstalled it.  

As one contributor to that thread you quoted said, I searched the net forever trying to find this solution.  I'm going to have to record this somewhere.  

Thanks again.

---

### Post by mushwars on 2010-02-06
I am happy to help if you could, mark this thread as resolved.

---


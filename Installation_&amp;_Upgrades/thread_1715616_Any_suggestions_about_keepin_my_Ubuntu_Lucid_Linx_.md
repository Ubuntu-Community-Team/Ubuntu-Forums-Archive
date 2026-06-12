---
title: "Any suggestions about keepin my Ubuntu Lucid Linx Clean?"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by ColombianBootloader on 2011-03-27
Hello everyone.

Well, I would like to know if I can find or somebody can point me on the right direction info about getting rid of old updates on Ubuntu system. I would like to know how can I do some maintenance to my ubuntu installation (Lucid Linx) I have found the following info: Is that enough?

[http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07](http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07)

I have 20GB of hard disk for my system, and I can not increase this size (the rest of the Hard Disk is shared with Windows XP and I can not get rid of XP, it is not my pc!! :( ), so I really need to keep my system clean, any suggestion besides the ones given on the web site? any help is more than welcome

cheers:D

---

### Post by wangsuda on 2011-03-27
well, there are some codes you can run to keep things clean:
```
sudo apt-get clean
``` and ```
sudo apt-get autoremove
``` should do the trick. These two codes should remove old and unused files and such. You can also remove old kernels (check out this thread: [http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)) To remove broken packages, use ```
sudo apt-get -f install
```

---

### Post by reqqq on 2011-03-27
or you can install bleachbit

---

### Post by wangsuda on 2011-03-27
^Yes, there is that. Please stay away from "Computer Janitor." That gem can lead to more problems than it's worth.

---

### Post by galacticaboy on 2011-03-27
I agree with the last person, stay away from Computer Janitor unless you know what you are doing, sometimes it will delete stuff that you want. Here is what I do, First I open a terminal and type sudo apt-get clean && sudo apt-get autoremove Then I install Ubuntu Tweak ([http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)) Then open it. When it is open at the left hand side click on Package Cleaner. Click the Unlock button, enter your password, then click on each one of the options and check all, do not click on Purge PPA's unless you know what you are doing though. 

Hope this helps, if you need any help, let me know!

---

### Post by Dutch70 on 2011-03-27
> **reqqq said:**
> or you can install bleachbit

+1 

```
sudo apt-get install bleachbit
```

---


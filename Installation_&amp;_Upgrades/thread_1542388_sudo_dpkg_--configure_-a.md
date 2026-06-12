---
title: "sudo dpkg --configure -a"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by crazyrufio on 2010-07-30
I get the following error after I tried upgrading from 9.10 to 10.04 and the computer freezing during the upgrade. I have tried running the synaptic and update manager and I get the following:

"[B] E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. " 

and when I run "sudo dpkg --configure -a" I get the following error message. 

"dpkg: parse error, in file '/var/lib/dpkg/updates/0057' near line 23 package 'kbd': EOF after field name `'"

I have also tried cd /var/lib/dpkg/updates and then rm 0057 but it says that is write proof and cannot be deleted. 

Any help would be appreciated with fixing this error to try to finish the upgrade, or somehow downgrading it back go to 9.10 so that 10.04 can be reinstalled. 

Thanks
[/B]

---

### Post by QIII on 2010-07-30
I wouldn't remove the file.  You don't know what further problems you  might cause.  Use rm with extreme caution.  Once you use rm, it is gone.  You might mv to a different file name (say  "xxxx.bak") so that you can restore it later, but I wouldn't even do that.

Can you open the file in gedit and C&P line 23?

---

### Post by mac9416 on 2010-07-30
First of all, welcome to Ubuntu Forums, crazyrufio!

Looking at [another thread]("http://ubuntuforums.org/showthread.php?t=385886"), you should be able to remove /var/lib/dpkg/updates/0057 and fix the problem. Try this:

```
$ sudo mv /var/lib/dpkg/updates/0057 ~/dpkg_updates_0057  # Back it up, just in case.
$ sudo dpkg-reconfigure -a
$ sudo apt-get update
```

And you should be good to go! Now, I'm assuming you didn't use sudo when attempting to delete the troublesome file. If you were, I'm not sure how to get rid of the sucker.

Hope that helps!

---

### Post by crazyrufio on 2010-07-30
thanks mac9416 that worked and it's all fixed now.

---


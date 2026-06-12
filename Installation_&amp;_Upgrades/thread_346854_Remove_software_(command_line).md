---
title: "Remove software (command line)"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by podollb on 2007-01-26
Is there an easy way to "remove" many things at once? I have been playing around with a extra server we have (that is located remotely) and I installed numerous webservers and various other things for testing purposes and I want to wipe it out and start again. I don't want to have to reinstall Ubuntu on the machine (although that is pretty easy if I were at the physical location). But the "apt-get remove <package_name>" would be to tedious and it also fails on a few of the packages (due to changes I made or conflicts that arose in my testing). Hence, I just want to deinstall everything (besides ssh). Is there a way to do this? Or at least come close to this?

---

### Post by dbott67 on 2007-01-26
You can include multiple packages on one line, if you desire:

```
sudo apt-get remove <package_name1> <package_name2> <package_name3>
```

This thread gives a few ways to list currently installed packages, which you could then use to create a list of the ones to remove:
[http://www.ubuntuforums.org/showthread.php?t=285037&highlight=package+list](http://www.ubuntuforums.org/showthread.php?t=285037&highlight=package+list)

-Dave

---


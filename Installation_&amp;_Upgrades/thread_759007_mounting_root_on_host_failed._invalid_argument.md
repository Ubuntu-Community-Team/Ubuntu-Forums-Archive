---
title: "mounting root on host failed. invalid argument"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by thedoorguy on 2008-04-18
I'm running 7.1 installed via wubi and encountered problem after install of something like 215 recommended updates.  There is an alert message just prior to dropping to shell when I boot in recover mode that says  /host/ubuntu/disk/host.root does not exit.  

It appears to me that the problem is that the install does not properly identify the host because the host.root file does exit in windows c:\ubuntu\disk\host.root.    windows C:\ being the host within which ubuntu is installed.    

Can anyone point me to a bug fix or tell me how to fix it?

Thanks.... thedoorguy

Additional information. the problem occrures in ubuntu 8.04, kernel 2.6.24-16-generic... 8.04 kernel 2-6-15- generic works fine.

---

### Post by Happy_Man on 2008-04-19
It's interesting that 16 doesn't work, whereas 15 does. If you don't need any of the new features in the 16 kernel, I recommend using the 15 kernel instead. From what I can tell, 15 to 16 isn't very much of a major upgrade, so you shouldn't be missing out on much.

Also, I've noticed that a lot of people on the forum and in real life are complaining that Wubi doesn't work out quite as well as a straightforward guided install. Personally, I don't like Wubi because it seems too convoluted a method. So if you continue to experience problems, try going back into Windows, uninstalling Wubi, and using the normal, partition the hard drive way of installing. There's a much better chance it'll work.

---

### Post by thedoorguy on 2008-04-19
> **Happy_Man said:**
> It's interesting that 16 doesn't work, whereas 15 does. If you don't need any of the new features in the 16 kernel, I recommend using the 15 kernel instead. From what I can tell, 15 to 16 isn't very much of a major upgrade, so you shouldn't be missing out on much.

Also, I've noticed that a lot of people on the forum and in real life are complaining that Wubi doesn't work out quite as well as a straightforward guided install. Personally, I don't like Wubi because it seems too convoluted a method. So if you continue to experience problems, try going back into Windows, uninstalling Wubi, and using the normal, partition the hard drive way of installing. There's a much better chance it'll work.

From response some of my other thread re other problem......others also wonder if wubi might be the real source of  my problems.  I have decided I am going to uninstall and do what you call normal, partion the hard drive way or reinstalling.

Thank you much for responding to my thread.

thedoorguy aka Richard

---


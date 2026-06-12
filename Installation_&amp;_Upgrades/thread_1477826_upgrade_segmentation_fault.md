---
title: "upgrade segmentation fault"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by complience on 2010-05-09
After installing Karmic 32bit I was getting problems related to my graphic card "ati HD2600xt" and its drivers.

Fresh installed Lucid 32bit in the hope it would fix them but it did not.

Purged the fglrx drivers and installed the radeon drivers by running the steps shown here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

But now im getting segmentation errors whenever i try to upgrade my packages and the GUI update manager just crashes.

If i run 'sudo apt-get upgrade' it returns
reading package list... Done
segmentation faulty tree... 50%

I have tried clearing my apt-get cache, it does not resolve the issue. 

Ive tried upgrading my packages using aptitude and it finds an error, see the pastebin

'sudo aptitude upgrade'

A package failed to install.  Trying to recover:
dpkg: parse error, in file '/var/lib/dpkg/available' near line 16847 package 'libm17n-0':
 missing version

[http://paste.ubuntu.com/430450/](http://paste.ubuntu.com/430450/)

Ubuntu Lucid - 32bit

---

### Post by complience on 2010-05-12
could it be a memory error?

shooting in the dark

---

### Post by amightyo on 2010-05-24
It's definitely a memory error. The question is how can we rectifier it without having to go back to the previous release. With 9.10 whenever I run my OpenGL and ODE programs, I had no problem. Worked fine now it's all Segmentation Fault. If the problem was with my program, I would have since traced it to fix. But it's an issue with the kernel and I so wish I know which lib is creating the conflict. Would be glad to find a solution. Cheers!!!

---


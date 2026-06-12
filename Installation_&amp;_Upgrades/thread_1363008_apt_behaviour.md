---
title: "apt behaviour"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by blueprats on 2009-12-23
Hi
I have installed ubuntu 9.10. I am a java programmer, so I installed java from the suns official site. I installed java in ubuntu manually and not with apt or aptitude package manager. Now, the problem is that, I need some of the software's which run on java example jedit, atunes etc. But when I try to install jedit from terminal through the following command
```
apt-get install jedit
```It says that you have to install java (as a dependency). But java is already installed. And I run java programs on the same operating system and they run without giving any problem. Now, I want to know why apt is not indexing java which is already installed. I have given the java path and classpath in the ~/.bashrc file of both root and user. Is there any file in linux where I have to mention that I have installed a software (java) and please index it. This behaviour of  apt is out of my scope, I hope you guys are going to help me.

---

### Post by oakgrove on 2009-12-23
I hate it when people answer me like this but, in this situation what you are talking about is just asking for nothing but problems.  The programs in the repositories are really designed to be self-consistent to a very large degree.  Many are custom patched, etc.  Ideally, if you want to run any java programs like jedit but you don't want to install their dependencies, just get jedit from its developer website.

Best thing to do is if you want to install jedit from the repos, just let it pull in its java dependencies then just make sure your path is set up like you said so you can use the custom java you downloaded from Sun and everybody is happy.

---

### Post by blueprats on 2009-12-24
Hey
Thanks for your reply. I will download jedit from their official site and I think, I can also run it. But the thing I want to know is where the apt looks for the installed packages, if I am not wrong there must be some file for it. Any one knows about this. Any help will be highly appreciated. Thanks in advance.

---


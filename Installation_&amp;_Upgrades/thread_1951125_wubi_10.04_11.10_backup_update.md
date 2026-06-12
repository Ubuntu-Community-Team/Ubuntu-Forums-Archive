---
title: "wubi 10.04 11.10 backup update"
date: 2012-04-02
forum: Installation &amp; Upgrades
---

### Post by dieter-erich on 2012-04-02
Hi, I installed wubi 11.10 on a Win7 laptop automatically from the net. Because of a number of issues I wanted to rather go back to wubi 10.04 (my applications have worked before on other PCs without problems by using this version).

I thus renamed the directory 'ubuntu' to 'ubuntu_11.10' and installed ubuntu 10.04 by launching the corresponding wubi.exe (from [http://releases.ubuntu.com/10.04.4/](http://releases.ubuntu.com/10.04.4/)). 

BTW: The downloaded iso did not work, neither was it possible to change the parameters e.g. instead of 17 GB use 30 GB). Finally I managed to install it with the default parameters. 

I then wanted to check something in ubuntu 11.10:

I renamed the directory 'ubuntu' to 'ubuntu_10.04', I renamed 'ubuntu_11.10' to 'ubuntu' and rebooted.

[B]I only got into GRUB but no further

[/B]Working on another machine under XP I never had problems changing from one wubi installation to another in this way. What is wrong?

Is it possible to have two wubi installations on the same PC?

I noticed that the wubi.exe files are of different size depending on what version (10.04 or 11.10) they are associated with. Do they make different changes to the Windows system?


Thanks, D-E

---

### Post by bcbc on 2012-04-02
Copy the wubildr file from \ubuntu\winboot\ to C:\ whenever you switch. It's actually a good idea to backup the one in C:\ and keep it with the associated release, as they can be updated when running grub updates as well. i.e. copy c:\wubildr to \ubuntu prior to switching, and copy it back afterwards.

---


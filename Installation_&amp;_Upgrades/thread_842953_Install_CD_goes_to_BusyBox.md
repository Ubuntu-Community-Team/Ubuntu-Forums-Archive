---
title: "Install CD goes to BusyBox"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by ppatin on 2008-06-27
I just downloaded the i386 version of 8.04, popped the CD in my drive and restarted the computer. I got to the first menu screen, selected the install option, and then the installer began to load. After a while it just dumped me to the BusyBox shell. There was no error message or anything like that, just the command prompt. I've tried booting from the LiveCD and I get the same result. Any ideas? I fooled around with Ubuntu a couple of years ago, but haven't had any Linux experience since then.

---

### Post by Aearenda on 2008-06-27
It could be caused by all sorts of things - but here is one common solution to try:

1. Start the CD and select your language.

2. Press F6 to show the kernel parameters.

3. Move the cursor to the end after ' -- ' 

4. Add 'all_generic_ide' after a space (without the quote marks)

5. Press enter to startup.

If this works you will probably have to do it for the installed system too. See [http://ubuntuforums.org/showpost.php?p=4799028&postcount=15](http://ubuntuforums.org/showpost.php?p=4799028&postcount=15) for how to do that. 

If it doesn't work, then we'll have to think of something else - so please post details of your system (brand, model, CPU, sata or ide, etc).

---

### Post by ppatin on 2008-06-27
Awesome, your suggestion appears to have worked. Thanks for the assistance.

---


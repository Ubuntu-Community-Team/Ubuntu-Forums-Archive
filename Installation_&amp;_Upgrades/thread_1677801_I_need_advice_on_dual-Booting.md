---
title: "I need advice on dual-Booting"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2011-01-29
I have been using windows/ubuntu dual-booting for while, I install windows first.
Now I want to change to install ubuntu first, then install them in separeted partition.
As you know there is always something wrong with windows, then I have reinstall them bough linux and windows.
question.
If they are installed in seperated partition can I reinstall windows without reinstalling ubuntu ?

---

### Post by ronnielsen1 on 2011-01-29
> I have been using windows/ubuntu dual-booting for while, I install windows first.
Now I want to change to install ubuntu first, then install them in separeted partition.
As you know there is always something wrong with windows, then I have reinstall them bough linux and windows.
question.
If they are installed in seperated partition can I reinstall windows without reinstalling ubuntu ? 	

Is what you have now a wubi installation? I take it that there is a problem with your windows? I'm not sure what exactly you're trying to do.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by ronnielsen1 on 2011-01-29
> If they are installed in seperated partition can I reinstall windows without reinstalling ubuntu ? 	

Ok, I think I got it. Yes, just don't overwrite the partition that you have Ubuntu installed on. Then you will have to reinstall grub2

[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

---

### Post by irv on 2011-01-29
> **hoboy said:**
> I have been using windows/ubuntu dual-booting for while, I install windows first.
Now I want to change to install ubuntu first, then install them in separeted partition.
As you know there is always something wrong with windows, then I have reinstall them bough linux and windows.
question.
If they are installed in seperated partition can I reinstall windows without reinstalling ubuntu ?
Let me see if I can answer  this. Looking at the end of your post, if you reinstall windows without reinstalling ubuntu windows will take over the MBR and ubuntu will not boot (no grub). You must have windows installed first then ubuntu can be installed and in it's own partition.

If you just let windows install and take the whole HD that's OK, because when you go to install ubuntu it will take an partition what it needs to install and leave windows intact.

---

### Post by ronnielsen1 on 2011-01-29
> If you just let windows install and take the whole HD that's OK, because  when you go to install ubuntu it will take an partition what it needs  to install and leave windows intact.

A little smarter, isn't it? The last win7 install I did downloaded files from the net while it was installing but forgot how to use the net card after it installed. I couldn't believe it.

---

### Post by hoboy on 2011-01-29
Thanks guys.

---


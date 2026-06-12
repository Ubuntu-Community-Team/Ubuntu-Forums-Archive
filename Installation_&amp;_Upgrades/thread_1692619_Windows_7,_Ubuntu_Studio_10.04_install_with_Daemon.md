---
title: "Windows 7, Ubuntu Studio 10.04 install with Daemon tools."
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by whosurdaddy8907 on 2011-02-21
I am having problems installing and subsequently booting Ubuntu studio 10.04 on my dual core amd-64 bit toshiba laptop. I have windows 7, with Daemon Tools lite, to creat a virtual drive to boot ubuntu from. The only problem is the installation is not working. I do not know how to program in the least, so most of the forums I have been to say to code things, and I am just learning how to program. Anyway my question is; is there an installer I can download to auto-install Ubuntu? and where do i have to have it in relation to my ISO file with Ubuntu on it?

---

### Post by gufide on 2011-02-21
You can't boot your computer from a virtual drive. You can install wubi from executing wubi.exe, the autorun in the cd,this will install ubuntu inside your win7. Or you can choose to get in the cd and double click on usb-creator.exe to make your computer booting from your usb key like a cd (make sure your usb ports are on top of boot priority of your computer). Then, you will able to make a complete install. If you want to have the choice to boot with ubuntu or windows 7, you must don't click on take entire disk (it will format all your disk to replace win7 by ubuntu)

wubi will provide more the feeling of an "auto-installer". I think it's the best solution for you

---

### Post by whosurdaddy8907 on 2011-02-21
how do i change boot priority?

---


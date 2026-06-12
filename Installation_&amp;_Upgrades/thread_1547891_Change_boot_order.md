---
title: "Change boot order"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by bilkay on 2010-08-07
I installed u-10.04 on an HP laptop via Windows 7 install.

When the computer boots, I get a boot menu with Windows and ubuntu as options (Windows the default). If I select ubuntu, I get another menu (grub) which finally leads to ubuntu.

I'd like to change the first menu so that ubuntu is the default. It's not the end of the world if I can't do it but it would make life easier.

Thanks in advance.

---

### Post by cj.surrusco on 2010-08-07
You are using the Windows bootloader, it seems. You would be able to edit that (and set a default) using a Windows program called [EasyBCD]("http://neosmart.net/dl.php?id=1"). I haven't used it in a while since I have gotten rid of all of my Windows installs, but it should do the trick.

---

### Post by navaneethan on 2010-08-07
you can change the option at **menu.lst** inside grub in your lucid :-)

---

### Post by krishnandu.sarkar on 2010-08-07
Simplest method would be : Boot into Windows > Win + R(Or alternatively :  Start>Run) > Type msconfig > Goto Boot tab > Select the OS and click Set as Default which you want to make default.

I suggest this as you are using Windows Bootloader. Otherwise you may edit GRUB(as suggested by others) if you want it as your bootloader.

---

### Post by sheriff_009 on 2010-08-07
Hey,

Can anyone of you tell me the path for menu.lst ?

Also if you have a little description handy on "how to?" , kindly share the same.

Thanks in advance
Shariff ( a newbie)

---

### Post by oldfred on 2010-08-07
If you are running 10.04 your only have menu.lst if you upgraded from before 9.10 and kept grub legacy. 

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

The OP has to have wubi if he is booting windows first. Unless he has a special setup from BCDedit.

bilkay
If you are to the point of using Ubuntu a lot you need to start thinking about a full install.
From the designer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

HOWTO: migrate wubi install to partition by bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by bilkay on 2010-08-13
It's done in Windows:

Computer -> System properties (upper menu bar) -> Advanced system settings -> Startup and recovery ("Advanced" tab) -> Settings

The default OS as well as the timeout can be selected.

---


---
title: "Ubuntu and Vista dual boot!!!"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by glore2002 on 2007-04-11
Hello!
Last week I had Win XP and Ubuntu installed on the same hard disk and working OK. This week I installed Win Vista Home Premium instead of XP. After that, I boot with Ubuntu Live CD and ran Grub to restore my dual boot. After that, my nightmare began! 

When starting the computer, Grub showed up the options but when choosing Vista, black screen and nothing happened. So, reinstalling Grub doesn't work with Win Vista.

Then, I re-installed Vista. Now, my computer starts with Win Vista but I can't get into Ubuntu. Is there a working way to be able to choose between Vista and Ubuntu when starting my computer without having to reinstall both OS?

There are many posts about things related to this subject but they are very confusing (at least for me) and by following one of them is how I lost the possibility to dual boot again.

So, in conclusion, I have Vista and Ubuntu already installed on my HD. Now, I can only start Vista and want to be able to start any of them.

Thanks in advance for your help,
G. Lorenzo.-

---

### Post by Hinko on 2007-04-11
try booting it with a live-cd and then restore or rewrite grub.

---

### Post by zvacet on 2007-04-11
[http://ubuntuforums.org/showthread.php?t=358183&highlight=grub]("http://ubuntuforums.org/showthread.php?t=358183&highlight=grub")

---

### Post by glore2002 on 2007-04-11
> **Hinko said:**
> try booting it with a live-cd and then restore or rewrite grub.

This is what I did and it doesn't work. Vista uses MBR in a different way. So, when you overwrite MBR with Grub, Vista can't start again.

---

### Post by glore2002 on 2007-04-11
> **zvacet said:**
> [http://ubuntuforums.org/showthread.php?t=358183&highlight=grub]("http://ubuntuforums.org/showthread.php?t=358183&highlight=grub")


This How To is for XP. Vista installs in a different way. Thanks for your help.

---

### Post by seamus7 on 2007-04-16
I had Edgy and XP dual booting from one hard disc using Grub. Worked perfectly.

I upgraded to Vista but chose the fresh install ... then I reinstalled the Edgy file system (/) though since my /home is on its own partition that wasn't touched. Grub, as before with XP, installed to the MBR and automatically discovered Vista.. i can't recall but it may have listed Vista as XP ... if so I just edited the title field in /boot/grub/menu.lst

anyways, i had no problems ... i'm on a dell e1505 laptop by the way

---

### Post by lvella on 2007-07-25
I had the same problem. I could solve it by installing Windows Vista on one partition, then changing the boot flag out of that partition using gparted, putting the boot flag in the Linux partition. After that, I reinstalled GRUB with the following entry in menu.lst file:

title           Micro$oft Windowze Bad-Vista
rootnoverify    (hd0,2)
makeactive
chainloader +1

In my case, Windowze was installed on /dev/hda3, thats why (hd0,2). If it is installed in /dev/hda1, the right parameter is (hd0,0).

Now I have another problem. I am not sure about the circumstances that caused such behavior, but the first time I booted Vista from GRUB, it seemed to overwrite MBR with Windowze boot loader, wiping out GRUB again.

---

### Post by MQMike on 2007-07-25
I happen to believe that GRUB will pretty much work about approximately the same with Vista as with XP, more or less, with possible tweaks or considerations.
That unclear comment aside, check out the following, which might provide some organization to the various possibilities:

***   The definitive dual-booting guide: Linux, Vista and XP step-by-step
[http://apcmag.com/dualboot](http://apcmag.com/dualboot)

---


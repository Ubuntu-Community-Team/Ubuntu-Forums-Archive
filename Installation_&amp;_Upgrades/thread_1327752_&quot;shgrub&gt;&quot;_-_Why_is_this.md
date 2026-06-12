---
title: "&quot;sh:grub&gt;&quot; - Why is this?"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by k64 on 2009-11-15
Hello, my name is Kenny Strawn. I've been a member of the [PC World Forums]('http://forums.pcworld.com/index.php?/user/179102-kstrawn/') for quite some time, and was over there when I could have been here. I came back here (Yes, came BACK, because I've had an account here for longer) and have something to say about Wubi in Windows Vista. It seems like I did everything right. I ran the Wubi installer, rebooted my computer, let the installation complete, and rebooted again. When I selected Ubuntu in the Windows Boot Menu for the second time, I got the "sh:grub>" prompt, and have to type commands to boot. I booted back into Vista, and browsed the C:\Ubuntu\Disks\Boot\Grub" folder, only to find it empty. Wubi had erased my GRUB! Is there any way I can recover GRUB so that I may have a working Windows Ubuntu Installation?

---

### Post by k64 on 2009-11-15
Please help me here.

-Kenny

---

### Post by kennethtb on 2009-11-16
Hi, Do not hold your breath wating for an answer on this subject - I posted twice yet received no answer - I guess there is no simple solution at this time? - did find some other posts relating to this subject but it was out of my level of skill (grub commands) - So what I did was to reboot my computer with the Ubuntu boot disc installed and select the first option which says something like" option changes nothing on your computer" and the problem was solved!

---

### Post by lovemylady on 2009-11-16
Well I got the same problem..

But instead of ubuntu I used to use "Kubuntu" (but here wheres the difference xD)

Yea and by me it didnt work either.. I get this shice sh:grub screen too..
then I uninstaled kubuntu installed "ubuntu" well the same :/

---

### Post by TheHimself on 2009-11-16
It seems to me that you've not really installed ubuntu as a n OS. Is C: Vista's partition? Then ubuntu files must not be there. Did installation program prompt you for partitioning your HDD?

Most importantly, what do you want: a dual boot machine or just running Ubuntu inside Windows?

---

### Post by kgas on 2009-11-16
you have been dropped to grub shell because it could not locate the kernel image for further loading and continue the boot process. Have a read on [Boot with Grub](http://www.linuxjournal.com/node/4622/print) and try to solve your issue. Good luck

---

### Post by k64 on 2009-11-17
> **kgas said:**
> you have been dropped to grub shell because it could not locate the kernel image for further loading and continue the boot process. Have a read on [Boot with Grub](http://www.linuxjournal.com/node/4622/print) and try to solve your issue. Good luck

I also know that there was no Menu.1st file when I installed Wubi. That's what I want to recover. I browsed the "C:\ubuntu\disks\boot\grub\" folder via Windows Explorer only to find nothing in it.

---

### Post by lovemylady on 2009-11-19
[I]Well I got 2 Partitions..
C = Vista D= Empty
and i installed ubuntu inside windows with "wubi" on the second empty partition (D)..


@ to k64 yea .. i installed ubuntu again now and yea i will try to not update grub or something similar since i'll get any serious answer how to fix it ;)[/I]

---

### Post by mmlinx on 2009-11-27
Got the same problem after an update in Ubuntu 9.10 
This is strange.. I always install Ubuntu beside Windows but i haven't had this luxury on my cdrom less notebook. So i tried Wubi. Now after three months i do an update in Ubuntu and im screwed. not so impressed with Wubi anymore.  

No wubildr                       it shows this for a split second before going to sh:grub>

Who can tell me what files i need to recover to c:\ubuntu\disks\grub (if that is the answer..)
and how to do this with the grub command line or in Win xp?

What i allready tried: 

chkdsk /r in XP command prompt. This is the only answer the wubi faq talks about...
This did not work for me.

also tried hitting insert after selecting Ubuntu.... nothing.

After hitting tab in grub i get some options reader.rescue seems interesting.
Who can help me out here ? 

Reinstalling Wubi doenst seem like an option to me. Than things seem to Windoisch for me. 
Getting blue screen of death? just reinstall Windows and the problem goes away... ](*,)

edit: Just booted in XP. this is how the folders look like. 
c:\ubuntu\disks\boot\grub\ (empty)
c:\wubildr.mbr
c:\wubildr (file)
c:\ubuntu\disks\swap.disk and root.disk
c:\ubuntu\disks\winboot (contains wubildr (file), wubildr.cfg and wubildr.mbr)

---

### Post by k64 on 2009-11-27
In case you're wondering, here's a link to my profile on the PC World Forums: [http://forums.pcworld.com/index.php?/user/179102-kstrawn/](http://forums.pcworld.com/index.php?/user/179102-kstrawn/)

I want to let you know that I first reinstalled Wubi and it worked fine, but then I decided to install Ubuntu 9.10 full throttle and wipe out Windows (again). That's because I wanted to build Chrome OS for my Acer Aspire One AOA110-1545.

---

### Post by lovemylady on 2009-11-27
[COLOR=Magenta]Well lately i will just wait and see so far everything works perfect and i will update grub in a year or so LOL aslong as it works fine why should I.. last time i only had problems ^^[/COLOR]

---

### Post by kevin.krenz on 2010-03-13
> **mmlinx said:**
> Got the same problem after an update in Ubuntu 9.10 
This is strange.. I always install Ubuntu beside Windows but i haven't had this luxury on my cdrom less notebook. So i tried Wubi. Now after three months i do an update in Ubuntu and im screwed. not so impressed with Wubi anymore.  

No wubildr                       it shows this for a split second before going to sh:grub>

Who can tell me what files i need to recover to c:\ubuntu\disks\grub (if that is the answer..)
and how to do this with the grub command line or in Win xp?

What i allready tried: 

chkdsk /r in XP command prompt. This is the only answer the wubi faq talks about...
This did not work for me.

also tried hitting insert after selecting Ubuntu.... nothing.

After hitting tab in grub i get some options reader.rescue seems interesting.
Who can help me out here ? 

Reinstalling Wubi doenst seem like an option to me. Than things seem to Windoisch for me. 
Getting blue screen of death? just reinstall Windows and the problem goes away... ](*,)

edit: Just booted in XP. this is how the folders look like. 
c:\ubuntu\disks\boot\grub\ (empty)
c:\wubildr.mbr
c:\wubildr (file)
c:\ubuntu\disks\swap.disk and root.disk
c:\ubuntu\disks\winboot (contains wubildr (file), wubildr.cfg and wubildr.mbr)

Anyone have any ideas on this one? This (exact) same thing is happening to my fiancee's computer and I'm trying to figure out how to fix it.

---


---
title: "GRUB Error 17"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by ibgeorgeb on 2008-03-07
My Toshiba M205-S10 Table Laptop is displaying "GRUB Loading stage1.5.  GRUB loading, please wait... Error 17"

It's been showing this for two days now. I formatted the HDD using the XP recovery CD that came with my laptop. I even tried to reinstalling Ubuntu Ver. 6.06. 

The XP seems to reinstall and goes through the entire process and about 8 minutes later I get the error message (Error 17).

I've read and and attempted to correct the problem reading the threads on the forums on this site but being a noobe I'm lost trying to understand all of the terms used as well as concept explanations (sudo, root, etc).

Question 1: Is my M205 laptop a brick?
Question 2: Is there an easy fix to resurrect my laptop to factory XP settings using my XP recovery disk?
Question 3: Should I just buy an Asus Eee or Cloudbook to play with Linux?

Thank you for any assistance.

George2b

---

### Post by miansaab on 2008-03-07
1. Put in your Win XP cd and boot from it.
2. Run the Recovery Console.
3. Select the Windows partition (usually 1).
4. type cd c:\
5. then type fixmbr

Doing this will write a new Master Boot Record on your hard drive and Windows should run normally. However, if you also have Ubuntu installed then you will NOT be able to access it.

Hopefully this should work. All the best.

---

### Post by ibgeorgeb on 2008-03-07
miansaab: I've been working on your fix the last 35 mins or so and it's still handing at the GRUB Loading Stage1.5. -- but wait! It's not showing an **Error 22** instead of error 17. Which means what? This must be some sort of progress.

Thank you for your help.

---

### Post by ibgeorgeb on 2008-03-07
Anyone: I'm now in the Ubuntu desktop. I wasn't able to get there before. I can now access the terminal and I've tried entering $sudo grub; followed by, find /boot/grub/stage1."

I got an "error 27 unrecognized command." I least Ubuntu is showing signs of life.

I even see the "Install" icon on the desktop. Should I try for another install? I ask myself.

I appreciate any assistance. george2B

---

### Post by antoz on 2008-03-07
Not sure if this will help your problem but it gives a lot of information about grub and i have use Hermman's instructions before to reinstall grub with the live CD after a Windows reinstall
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by ibgeorgeb on 2008-03-08
Thank you Antoz and miansaab. This is the sick M205 that wouldn't boot. I'm okay now and I'm working fine as you can see. GeorgeB did re-install ubuntu from the desktop and the install knocked some sense into me and now I've become a solid Ubuntu machine -- all 49 Gb of me. Thank you all for your interest and support. Ain't life beautiful?  :)

ISSUE RESOLVED

---


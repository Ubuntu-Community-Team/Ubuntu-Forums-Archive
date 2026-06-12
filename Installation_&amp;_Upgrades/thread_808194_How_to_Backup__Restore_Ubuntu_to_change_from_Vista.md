---
title: "How to Backup / Restore Ubuntu to change from Vista to XP"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by cforput on 2008-05-26
I have a laptop that came with Vista. I have installed gusty on it an everything is working OK. This newbie has learned a lot but has a long way to go.

I can't get rid of windows until a viable alternative to MS Streets and Trips is available. I have looked at what is available and nothing is even close to what I need (desktop with no internet connection). Anyway, I digress.....

I want to change from Vista to XP but don't want to start all over again with Ubuntu. Is there a way to do a backup, switch from Vista to XP and then restore my complete Ubuntu config so I don't have to go back through the hours and hours it has taken me to get Ubuntu to work for me?

---

### Post by tamoneya on 2008-05-26
you should do two things: 
1. Backup /home.  This will store all of your configurations and personal settings as well as all of your personal files.

2.  Use remastersys.  This will allow you to make a custom Ubuntu CD that has all the packages and programs that you have installed.  This way you dont have to go through installing them one by one again.

---

### Post by cforput on 2008-05-27
OK, so I am really new to Ubuntu / Linux. Is there are "backup" command or do I just copy it to some place safe? 

Would these be the correct steps?
1. Copy /home to a safe place
2. Run remastersys to create a custom Ubuntu CD
3. Trash Vista
4. Install XP
5. Reinstall Ubuntu wiht remastersys
6. Copy /home back to new Ubuntu install?

what if remastersys doesn't fit onto a single CD (I have no idea what this does but I do know I have installed a LOT of programs so not sure they will all fit on a single CD)

Any and All help would be greatly appreciated.

---

### Post by zvacet on 2008-05-28
If I understand you correctly you are doual booting Vista/Ubuntu.Now you want to replace Vista with XP.Boot your XP install CD and with it delete Vista partition (if that is possible with Vista.I don´t know because I never use it but it should be that way.).On that partition install XP.That will erase your grub so you will have to reinstall it.Do it like [this.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

---


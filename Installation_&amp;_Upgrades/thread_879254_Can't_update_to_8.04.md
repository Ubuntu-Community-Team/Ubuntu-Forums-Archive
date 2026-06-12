---
title: "Can't update to 8.04"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by Stoodle on 2008-08-03
No matter what, I can't update to 8.04. When I tried, the first time, it said something about not being able to download everything. So I tried again and it downloaded everything it needed. After doing some installs, it just stopped installing. I tried to restart and it froze after trying to kill processes or something. I had to do a hard shutdown. When I did that and brought it back up, the splash window is at a huge resolution so all I see is "Ubu" with the logo. I can log in still, but then nothing shows up after I do. I went to command line and tried sudo apt-get upgrade and sudo apt-get update but it didn't work. I'm missing something. It'll shutdown but I can't complete the upgrade or fix it. Help me.

I did dpkg --configure -a but it hangs up at 

generating locales...
   en_AU.UTF-8

Oh yeah. Last, it freezes when I shutdown with ctrl-alt-del.

---

### Post by dileepm on 2008-08-04
> **Stoodle said:**
> No matter what, I can't update to 8.04. When I tried, the first time, it said something about not being able to download everything. So I tried again and it downloaded everything it needed. After doing some installs, it just stopped installing. I tried to restart and it froze after trying to kill processes or something. I had to do a hard shutdown. When I did that and brought it back up, the splash window is at a huge resolution so all I see is "Ubu" with the logo. I can log in still, but then nothing shows up after I do. I went to command line and tried sudo apt-get upgrade and sudo apt-get update but it didn't work. I'm missing something. It'll shutdown but I can't complete the upgrade or fix it. Help me.

I did dpkg --configure -a but it hangs up at 

generating locales...
   en_AU.UTF-8

Oh yeah. Last, it freezes when I shutdown with ctrl-alt-del.
Try apt-get install -f this may fix your broken dependencies if exist.

---

### Post by Stoodle on 2008-08-04
Well, what I did was put in a Xubuntu Alternate install CD and chose repair system. This allowed me to update that way. We I updated, there were some other errors. For example, I need to make my wacom tablet work again. Also, the login screen has a weird resolution that needs fixing.

---


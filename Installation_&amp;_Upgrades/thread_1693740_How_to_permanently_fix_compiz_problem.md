---
title: "How to permanently fix compiz problem"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by F8M on 2011-02-23
When boot-up in Ubuntu 10.04LTS and open my webpage, I can only see 1/4 of the page. The temporary fix that I have found is 'compiz --replace', BUT IS THERE A PERMANENT FIX ?
Below are the warnings I get after the temp. fix.
compiz --replace
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Couldn't find a perfect decorator match; trying all decorators
Starting gtk-window-decorator
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

What do they mean by 'an application bug'?
Any suggestions would be helpful, Thank you.

---

### Post by realzippy on 2011-02-23
...put *compiz --replace* in System/Settings/Startup Applications
to have a permanent fix.
No idea about the warning;anyway,it is just a warning.....

---

### Post by F8M on 2011-02-23
I cannot find System/Settings/Startup Applications. Under Systems, I have either Preference or Administration. The Startup Applications is found under Preference, but how do I know if this is the one.
I wait for your response.

---

### Post by IWantFroyo on 2011-02-23
You found the right one. System-preferences-startup.
Select add, put whatever you want for the name and comment, but put compiz --replace for the command.

---

### Post by F8M on 2011-02-24
When I put 'compiz --replace' for the command, it did not work. So I tried putting 'sudo compiz --replace' for the command, that didn't work neither.
Here's the error I got;

compiz --replace
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting gtk-window-decorator
compiz (core) - Warn: Exceeded max texture size

Launching fallback window manager
**
metacity:ERROR:core/prefs.c:2495:meta_prefs_get_workspace_name: assertion failed: (workspace_names[i] != NULL)
Aborted

Any suggestions would be helpful, thank you.

---

### Post by dino99 on 2011-02-24
the hard fix: 
open synaptic and remove/purge everything about compiz, then reinstall compiz

the soft way: sudo dpkg-reconfigure compiz

you can try also: compiz --replace & (without sudo)

---

### Post by realzippy on 2011-02-24
*"The temporary fix that I have found is 'compiz --replace'..."*

Thought this had worked ?

---

### Post by F8M on 2011-02-24
When you type in 'compiz --replace', this is a temporary fix - I mean, this fixes the compiz until you need to boot up your system. I am looking for a permanent FIX.
This is what I did. 
I uninstalled all related compiz software in the Synaptic Pkg Manager and then rebooted to install all software in the Update Manager from the Ubuntu main server. After rebooting again, I still had the compiz problem, so I installed all Compiz software in the Synaptic pkg Manager by selecting all the Ubuntu Symbol(or prefered) software related to Compiz.
So after rebooting again, I still had the problem - NO PERMANENT FIX. I wonder if the problem I have is with one of my driver(just a thought).
Any other suggestions would be helpful, thank you.

---

### Post by realzippy on 2011-02-24
If
compiz --replace
fixes your compiz temporarely,it "has" to work in  Startup Applications..

Typo?

[http://www.google.com/imgres?imgurl=http://1.bp.blogspot.com/_NXe-USYSZmU/TJZPb9hR0cI/AAAAAAAADag/HmwPzggGDho/s400/Screenshot-Add%2BStartup%2BProgram.png&imgrefurl=http://mapopa.blogspot.com/2010/09/compiz-08x-on-debian-sid.html&usg=__W_BbVZ-CqBQZL1N7aRXciA5I8_g=&h=154&w=347&sz=9&hl=de&start=0&zoom=1&tbnid=09MjZUflPQyLXM:&tbnh=88&tbnw=199&ei=Np5mTYCcKcrusgbK_YziDA&prev=/images%3Fq%3Dcompiz%2Bstartup%2Bapplications%26um%3D1%26hl%3Dde%26client%3Dubuntu%26sa%3DN%26channel%3Dfs%26biw%3D1360%26bih%3D542%26tbs%3Disch:1&um=1&itbs=1&iact=hc&vpx=553&vpy=260&dur=276&hovh=88&hovw=199&tx=126&ty=62&oei=Np5mTYCcKcrusgbK_YziDA&page=1&ndsp=19&ved=1t:429,r:9,s:0](http://www.google.com/imgres?imgurl=http://1.bp.blogspot.com/_NXe-USYSZmU/TJZPb9hR0cI/AAAAAAAADag/HmwPzggGDho/s400/Screenshot-Add%2BStartup%2BProgram.png&imgrefurl=http://mapopa.blogspot.com/2010/09/compiz-08x-on-debian-sid.html&usg=__W_BbVZ-CqBQZL1N7aRXciA5I8_g=&h=154&w=347&sz=9&hl=de&start=0&zoom=1&tbnid=09MjZUflPQyLXM:&tbnh=88&tbnw=199&ei=Np5mTYCcKcrusgbK_YziDA&prev=/images%3Fq%3Dcompiz%2Bstartup%2Bapplications%26um%3D1%26hl%3Dde%26client%3Dubuntu%26sa%3DN%26channel%3Dfs%26biw%3D1360%26bih%3D542%26tbs%3Disch:1&um=1&itbs=1&iact=hc&vpx=553&vpy=260&dur=276&hovh=88&hovw=199&tx=126&ty=62&oei=Np5mTYCcKcrusgbK_YziDA&page=1&ndsp=19&ved=1t:429,r:9,s:0)

---

### Post by F8M on 2011-02-24
I tried putting compiz --replace in Startup Applications again, but again it did not work. And yes, I did check the typo.
Any other suggestions.

---

### Post by realzippy on 2011-02-25
You could [add a new user]("https://help.ubuntu.com/community/AddUsersHowto") for testing.
If the new account is fine,you know it is a config problem in your user's account,otherwise problem is system-wide....

---

### Post by F8M on 2011-03-02
After being away from the computer for a couple of days and then turning it on to download new system updates, I rebooted the computer with all the compiz problems resolved. A big thank you to everybody that helped.
CLAUDE

---


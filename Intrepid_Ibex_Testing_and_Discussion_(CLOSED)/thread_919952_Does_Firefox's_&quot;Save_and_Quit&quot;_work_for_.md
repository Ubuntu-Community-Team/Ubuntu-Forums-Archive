---
title: "Does Firefox's &quot;Save and Quit&quot; work for anyone?"
date: 2008-09-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2008-09-14
If you close Firefox when multiple tabs are open, it gives you a choice to save the tabs so that when you open Firefox again later it's supposed to restore those tabs.

I've tried Firefox's Save And Quit option on Windows XP, Ubuntu Hardy, and Ubuntu Intrepid, and it's not worked on any OS or computer I've tried it on, both 32-bit and 64-bit. (I'm posting this here because I'm using Intrepid currently).

Every now and then (about one in every ten times or so) Firefox will surprise me and load up all the tabs I saved.

Here's the funny part. If I open up a terminal and type "killall firefox", the next time Firefox opens, it will restore all my tabs 100% of the time. In fact, this is the ONLY way I can do it, by just killing the process.

Do any of you have this same problem? (Speaking in terms of Intrepid, of course, but feel free to share your thoughts regardless, I'm curious if it's just me).

---

### Post by mikeize on 2008-09-14
Same for me.  Neither on XP or Hardy does this work...  unless I kill the process in the task-manager!  Be nice if the included features would work.

-mike

---

### Post by Gourgi on 2008-09-14
i use an extension which has its own session manager and works great 
here it is [http://tmp.garyr.net/forum/viewtopic.php?t=9178](http://tmp.garyr.net/forum/viewtopic.php?t=9178)
maybe this helps you solve your problem.

---

### Post by howefield on 2008-09-14
Have you set Firefox to clear all data at exit, history, ect ect ?

I just tried it and get the same result as you.

---

### Post by howefield on 2008-09-14
Just set mine not to clear data on exit, and tabs restored perfectly.

---

### Post by jlacroix on 2008-09-14
> **howefield said:**
> Have you set Firefox to clear all data at exit, history, ect ect ?

I just tried it and get the same result as you.

I do! I don't like Firefox to keep a history of pages at all, I just don't need that function.

> **howefield said:**
> Just set mine not to clear data on exit, and tabs restored perfectly.

I might try that, but I'd prefer to have both ways, no history, but remember what is necessary to restore tabs, etc. Can that be done?

---

### Post by BwackNinja on 2008-09-14
edit -> preferences -> privacy and uncheck all that you don't like

---

### Post by howefield on 2008-09-14
> **jlacroix said:**
> I do! I don't like Firefox to keep a history of pages at all, I just don't need that function.



I might try that, but I'd prefer to have both ways, no history, but remember what is necessary to restore tabs, etc. Can that be done?

Don't think you can do that, there is no half way house, you destroy all the history or none at all. So unfortunately you have to choose, either restored tabs or no tracks.

Life is so unfair ;)

---

### Post by Oldsoldier2003 on 2008-09-14
> **jlacroix said:**
> If you close Firefox when multiple tabs are open, it gives you a choice to save the tabs so that when you open Firefox again later it's supposed to restore those tabs.

I've tried Firefox's Save And Quit option on Windows XP, Ubuntu Hardy, and Ubuntu Intrepid, and it's not worked on any OS or computer I've tried it on, both 32-bit and 64-bit. (I'm posting this here because I'm using Intrepid currently).

Every now and then (about one in every ten times or so) Firefox will surprise me and load up all the tabs I saved.

Here's the funny part. If I open up a terminal and type "killall firefox", the next time Firefox opens, it will restore all my tabs 100% of the time. In fact, this is the ONLY way I can do it, by just killing the process.

Do any of you have this same problem? (Speaking in terms of Intrepid, of course, but feel free to share your thoughts regardless, I'm curious if it's just me).

Works fine for me in Hardy and Intrepid, I've never experienced a problem with it. As mentioned above if you make FF clear your browsing history then it *can't* restore your tabs.

---

### Post by jlacroix on 2008-09-14
Makes sense. I'll try it a little bit more tonight and see what happens. :)

---


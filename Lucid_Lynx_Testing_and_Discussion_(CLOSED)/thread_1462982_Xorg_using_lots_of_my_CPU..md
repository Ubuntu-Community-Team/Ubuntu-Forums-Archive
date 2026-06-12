---
title: "Xorg using lots of my CPU."
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Owen.C93 on 2010-04-26
For the past week or so Xorg ends up using 90% of my cpu, it doesn't happen straight after boot but can happen in 15 mins or 2 hours. I can't seem to track it down to any application.

I would be grateful if anyone can help, my laptop is starting to burn my leg :L

---

### Post by conradin on 2010-04-26
Not sure right off the bat. Can we get some hardware specs?
What OS do you have? What is your graphics controller? What is your chip-set?
How fast is your cpu? etc... 

perhaps try the vesa driver.

---

### Post by Owen.C93 on 2010-04-26
> **conradin said:**
> Not sure right off the bat. Can we get some hardware specs?
What OS do you have? What is your graphics controller? What is your chip-set?
How fast is your cpu? etc... 

perhaps try the vesa driver.
Nvidia 4600gs

Core 2 duo

10.04

Nouveau driver (rather not try nvidi if I can help it)

---

### Post by dalonso on 2010-04-26
Could it be related to this:

[http://ubuntuforums.org/showthread.php?t=1459417](http://ubuntuforums.org/showthread.php?t=1459417)

Have you "apt-get upgrade" recently? The fixes should be available if the system is updated to the last RC.

---

### Post by Owen.C93 on 2010-04-26
Fully up to date. I am really stuck trying to figure out what driver I'm using. I'm not using the two nvidia's in hardware drivers, and as far as I can tell I'm using nouveau.

Is there anyway to check what I'm using?

---

### Post by nanog on 2010-04-26
[http://ubuntuforums.org/showthread.php?t=1459417](http://ubuntuforums.org/showthread.php?t=1459417)

That bug was only valid for people using compiz. So unless you are running nouveau off edgers its not relevant. I have had problems with 2.6.32-21 and high cpu usage under nouveau and am currently running 2.6.20 without incident. I will probably file a bug after release if the problem persists.

---

### Post by Owen.C93 on 2010-04-27
Ok thanks. It doesn't seem to be a problem yet. Is there anyway I can tell if it is using my graphics card?

---

### Post by Owen.C93 on 2010-04-27
So strange, sometimes closing my running apps stops the cpu hogging, while sometimes it doesn't.

---

### Post by asw24 on 2010-04-27
I have exactly the same concern. However I get the impression it is link to a webpage with java script that refreshes the page. So normal pages are find and the cpu start running 100% as soon as I have opened this specific page. Closing the page doesn't help; I need to close down my browser completely.
Same page cannot be openend in either Opera or Chrome. For 9.10 this was possible in all three browsers without the cpu moving to 100%. The only thing that never worked is the automatic refesh java should trigger.
System: ex58-ud3r motherboard; i7-920 cpu (so one of the 8 cpu's move to 100% rest remains normal). 64amd 10.04 rc version, 6 gb ram-ddr3-1333, videocard nvidea 8800gt

System monitor shows java at 96%,, yet reporting sleep. It also shows that =the process is linked to a browser plug-in. Hope this info helps.

---

### Post by Owen.C93 on 2010-04-27
Mine seems to be related to docky, when I close that it fixes the problem temporarily. I'll leave this unsovled for a little while though.

---


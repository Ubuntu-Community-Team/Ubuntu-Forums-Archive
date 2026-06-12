---
title: "Missing Ubuntu One in panel indicator applet and notifications in Lucid"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rod40cool on 2010-04-15
I'm running Lucid with U1 version 1.1.91-0ubuntu1 and I'm downloading Ubuntu updates daily to stay up-to-date however I've noticed that I'm missing a cloud icon in the panel indicator area applet.  U1 is syncing fine with anything I drop in the Ubuntu One folder and the U1 Preferences window shows I'm connected and sync has completed.

So I have 2 problems:
1. I get no notifications when syncing/completed
2. I have no panel applet to tell me if U1 is connected or even running. The only way I can find out is to run the U1 Preferences.

Attached screenshots of my panel indicator area and U1 Preferences window.

Can anyone assist?

---

### Post by hackb0y294 on 2010-04-15
I think if you right click the panel and click Add to Panel, there should be something like Ubuntu One notifier, or something, which should be what you're looking for.

---

### Post by joshuahoover on 2010-04-15
> **rod40cool said:**
> I'm running Lucid with U1 version 1.1.91-0ubuntu1 and I'm downloading Ubuntu updates daily to stay up-to-date however I've noticed that I'm missing a cloud icon in the panel indicator area applet.  U1 is syncing fine with anything I drop in the Ubuntu One folder and the U1 Preferences window shows I'm connected and sync has completed.

So I have 2 problems:
1. I get no notifications when syncing/completed
2. I have no panel applet to tell me if U1 is connected or even running. The only way I can find out is to run the U1 Preferences.

Attached screenshots of my panel indicator area and U1 Preferences window.

Can anyone assist?

We removed both from Lucid. In its place we're using the Ubuntu One Preferences and enhanced file emblems that display the status of syncing.

Thank you,

Joshua

---

### Post by rod40cool on 2010-04-17
> **joshuahoover said:**
> We removed both from Lucid. In its place we're using the Ubuntu One Preferences and enhanced file emblems that display the status of syncing.

Thank you,

Joshua

Thank you hackb0y294 however, there doesn't appear to be a Ubuntu One notifier when you adding to the panel. 

Thank you Joshua. That makes sense not having a panel applet any more, however I think having a d-bus notification would be useful feedback, particularly if you're syncing a large file(s) and want to know when it's completed so that you can - say shut down when it's done. :) 

PS. Sorry, should have posted this in Lucid testing.

---

### Post by hackb0y294 on 2010-04-17
No problem. Sorry I couldn't help more.

---

### Post by alindgr1 on 2010-04-19
> **joshuahoover said:**
> We removed both from Lucid. In its place we're using the Ubuntu One Preferences and enhanced file emblems that display the status of syncing.

Thank you,

Joshua
I see that it has been a few days, but I am just getting back to UbuntuOne after loading Lucid Beta on my computer.  I came here looking for the UbuntuOne icon, and I see that they have been removed and replaced with enhanced icons.  

I would submit that I believe the indicator applet icon was easier.  I may be wrong, but it seems that you would have to leave the Nautilus window open to see the enhanced icons.  Well, I did not always leave the window open to watch the icon.  Plus, if I go to a different computer that has been added to my UbuntuOne account, it should begin synching with out a Nautilus window open at all.  Therefore, the enhanced icons may never be seen at all.  

If I am wrong about any of this, I apologize for my misunderstanding.

---

### Post by Valombre on 2010-04-28
Hi,
i think an applet is totally necessary for a sync service like ubuntu one.

I used/tried a windows service like this and an applet was present to indicate the states of synchronization, a click on it even giving details of files/directories being sync ...

if you want an example take a look here  trial 15 days to see the applet/file syncing tool => [http://www.humyo.com/pages/en/online-file-storage](http://www.humyo.com/pages/en/online-file-storage) 
You need a windows machine to test it of course ....  

But me i want to use ubuntu one efficiently  on my ubuntu machine, one look on my notification zone and i know if my 2384 files and directories are synchronized  ;)

---

### Post by irPhunky on 2010-04-28
You don't need to use Windows with humyo - we offer WebDav support so you can happily mount it and just use rsync ;)

---


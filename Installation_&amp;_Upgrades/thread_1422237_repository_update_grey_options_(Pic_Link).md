---
title: "repository update grey options (Pic Link)"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by Elie-M on 2010-03-05
when I want to update my system I notice some grayed out packages in the repository..

u can know exactly what I'm talking abt with this pic:

[http://i156.photobucket.com/albums/t18/Mankind-195/Screenshot-1.png](http://i156.photobucket.com/albums/t18/Mankind-195/Screenshot-1.png)

I want to know why those are gray and un-selectable and how to fix/select them for update if any (I want to have better knowledge of how ubuntu/linux works).. and thanks

---

### Post by rcragun on 2010-03-05
I'm getting something similar and when I try to install the upgrades that are not greyed out, update manager hangs and says it can't complete the process.  I also just got a message saying the updates aren't from Ubuntu.  Is it possible I've been hacked???

---

### Post by ibuclaw on 2010-03-05
> **Elie-M said:**
> when I want to update my system I notice some grayed out packages in the repository..

u can know exactly what I'm talking abt with this pic:

[http://i156.photobucket.com/albums/t18/Mankind-195/Screenshot-1.png](http://i156.photobucket.com/albums/t18/Mankind-195/Screenshot-1.png)

I want to know why those are gray and un-selectable and how to fix/select them for update if any (I want to have better knowledge of how ubuntu/linux works).. and thanks

Generally they are updates of packages that can't be installed because your system does not have the required dependencies for those applications OR because of conflicts on your system.

If you've ever added a third party repository that isn't officially supported, then this would be the reason why.

Regards
Iain

---

### Post by ibuclaw on 2010-03-05
> **rcragun said:**
> I'm getting something similar and when I try to install the upgrades that are not greyed out, update manager hangs and says it can't complete the process.  I also just got a message saying the updates aren't from Ubuntu.  Is it possible I've been hacked???

If the update-manager hangs on you, this tends to mean that you've upgraded several of your system components (libraries) to an unsupported version. Check your sources list for any repositories that you may have added.

And no, your issue is not similar in the slightest. ;)

---

### Post by RedG on 2010-03-31
> **ibuclaw said:**
> Generally they are updates of packages that can't be installed because your system does not have the required dependencies for those applications OR because of conflicts on your system.

If you've ever added a third party repository that isn't officially supported, then this would be the reason why.

Regards
Iain

Is there a way to find out whats conflicting or what dependencies that is not met?
I have tried using synaptics and choose properties on the package with a gray exclamation mark, and looked for a clue, but none was given that I could see. 
I DO have third party repositorys...

---

### Post by Elie-M on 2010-05-17
it was solved by manually selecting the packages in synaptic and mark them to upgrade so they upgraded and problem gone

---


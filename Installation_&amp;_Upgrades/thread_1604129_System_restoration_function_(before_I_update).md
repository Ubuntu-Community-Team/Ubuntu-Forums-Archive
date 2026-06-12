---
title: "System restoration function? (before I update)"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by Moozillaaa on 2010-10-23
Is booting a previous kernel the best approach to this?

I've seen upgrades knock out wireless, and now I just solved a video ordeal...

Is there any sort or System Restoration?

---

### Post by Rubi1200 on 2010-10-23
There is no System Restore function in Ubuntu.

Booting into previous kernels can make a difference.

It is also very important to make regular backups of important data.

Sometimes, newer kernel version resolve problems, but it is always useful to have a fall-back option.

Hope this helps answer your question.

---

### Post by Herman on 2010-10-24
:) I'm pretty sure the Ubuntu developers could easily  make up a 'system  restore' function if they thought it would be a good  idea.

Did you know we can open synaptic package manager, (from the 'System', 'Administration' menu), and click 'File', 'History', for an chance to review all the packages we've ever added or removed our operating system?

That could be useful in the situation where you've lost some functionality, you might be able to see which package is was exactly that caused your problem.

If you can do that then there's a chance that you can use the search function in synaptic to find the package and remove it and re-install the earlier version.

It's also easy to use the 'lock version' function in synaptic, (if you really feel you need it). Just highlight the package you want to prevent from being upgraded automatically and click 'Package', 'Lock version'.
Probably just restricting the update of one package and its dependencies  would be not as bad as 'restoring' you entire system and presumably  avoiding all future updates and living in fear of progress. 
I think most Ubuntu users tend to be positive, forward-looking and optimistic.
Generally we all look forward to receiving the latest improvements to the software we use whenever we can, as well as important security updates.

If you're feeling competent enough, the best thing to do would be to investigate the problem yourself a little and file a bug report about it so developers will know about it and fix the problem properly. 
If you can do that you would be helping yourself and others who might have the same setup/hardware as you do, and you'd be helping the future of Ubuntu.  :)

Many Ubuntu users use programs like partimage or clonezilla or the dd  command to make backups of our entire systems, which we can use to  restore with if we really need to. :)

---

### Post by Moozillaaa on 2010-10-24
**WOW - A RESPONSE FROM ONE OF **[B]THE LINUX GURUS!!!

Saikee once, and how Herman - the checklist is finished

THAT'S LIKE TALKIN' TO THE PRESIDENT!!![/B]  



edit:
Never mind - that's an insult. Oops!

---

### Post by Herman on 2010-10-25
Hey thanks for your enthusiasm, I just another happy Ubuntu user though. I don't have any special status at all, other than having been around here for a long time. :)

Probably you already know, but if you're using synaptic package manager, another cool thing you can do easily is look up packages using the search function and  click on them and click 'properties' and then look through the tabs in  the 'properties' dialog to find out all about the package. 
You should be able to read what the package is supposed to do by reading the 'Description' tab, and that might help you track down which package(s) might have something to do with any problems you may have. :)

---


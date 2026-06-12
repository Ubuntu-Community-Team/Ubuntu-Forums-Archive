---
title: "Evolution Calendar problems?"
date: 2009-04-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by timzak on 2009-04-15
Anyone else have a problem with the Evolution calendars after the recent updates?

This morning I edited an event to add an alarm to it, but when I clicked "OK" to save the changes, Evolution greyed out and I had to force quit.  Now every time I launch Evo, it starts fine in the email reader, but when I switch over to the calendar, ALL of my calendar events are gone!  If I click on any of my calendar titles on the left pane, Evo greys out and I must force quit again.  Looks like all of my calendar events have been erased?  If anyone knows of a method to restore them, I'd appreciate it.

It won't take a lot to reimport/recreate them, and I know I'm taking my chances running the beta version.

Thanks.

---

### Post by olskar on 2009-04-15
Hm, I would almost not call it a beta anymore since the release candidate should get out tomorrow and that should be almost like the final version.. :/

Edit: Yes, some other people seems to think the same way [http://ubuntuforums.org/showthread.php?t=1126229](http://ubuntuforums.org/showthread.php?t=1126229)

---

### Post by timzak on 2009-04-15
Thanks, was just trying to head off the "don't complain, it's a beta" comments.  ;)

Update:  My calendar events are still there, as they are visible in the dropdown menu in the clock applet.  It's just when I try to access the fullblown calendar within Evo that Evo greys out.  Anyone have any ideas on how to fix this?  

Thanks.

---

### Post by jfernyhough on 2009-04-15
It seems to me that each update alternates between breaking and fixing the calendar in Evolution. It's really rather annoying. From what I've read I think it has something to do with keyring access, and the easiest/only way to get back to a working state is to reinitialise Evolution (i.e. run a gconf --recursive-unset /apps/evolution ). This cleans all settings and account details and lets Evolution set up keyring access again. The reason behind having to use gconf is that even though you delete a non-working calendar its configuration is still saved - and when Evo opens it tries to access the calendar it can't access, stalling or crashing.

---

### Post by timzak on 2009-04-15
> **jfernyhough said:**
> It seems to me that each update alternates between breaking and fixing the calendar in Evolution. It's really rather annoying. From what I've read I think it has something to do with keyring access, and the easiest/only way to get back to a working state is to reinitialise Evolution (i.e. run a gconf --recursive-unset /apps/evolution ). This cleans all settings and account details and lets Evolution set up keyring access again. The reason behind having to use gconf is that even though you delete a non-working calendar its configuration is still saved - and when Evo opens it tries to access the calendar it can't access, stalling or crashing.

Thanks for the reply.  So do I just type ```
gconf --recursive-unset /apps/evolution
``` in the terminal?  I'll give it a try at my next opportunity.

I'm not sure calendars are actually deleted, because I can see today's events in the mini calendar in the clock applet dropdown menu.  Can the events still display here if the calendars are deleted?

It appears that my calendar was working fine until I tried to edit an event.  I just tried to add an alarm to the event.  Prior to attempting this, it appeared to be working, but in the process of saving the change to this event, something happened to create the issues I'm experiencing.

---

### Post by timzak on 2009-04-15
Sorry for the double-post, can you explain how to run ```
gconf --recursive-unset /apps/evolution
```

I tried everything I could think of via terminal and running gconf-editor.  I tried googling "gconf --recursive-unset /apps/evolution" with no luck.

Thanks.

Edit:  found something finally, I need to type gconftool --recursive-unset /apps/evoltuion

Unfortunately, it didn't fix the problem.  Good thing I'm on IMAP as I didn't know that command would wipe out my emails.  But after setting my email back up, I clicked on the Calendar icon and Evolution promptly froze and greyed out again.  Something seems utterly hosed...:(

---

### Post by timzak on 2009-04-15
Hi, it appears there was a corrupt configuration file somewhere in .evolution/calendar.  I went through and deleted all of them (in the various subdirectories) and now the calendar works again.  I wish I had the time to troubleshoot better, but I needed to get back up and running.  Just have to reimport all my calendars now.

Thanks,
Tim

---

### Post by timzak on 2009-04-16
I've been able to duplicate this problem now.  Maybe it's a bug?

I created an event in the calendar.  Set it to recur every Wednesday.  Evolution by default sets the recurrence to 1 time, which is silly because this isn't a recurrence at all.  So I edited this setting and changed it to recur "forever".  I got a confirmation dialog saying "You are modifying a recurring event.  What would you like to modify?"  It gives the choices "This Instance Only" and "All Instances".  I select "All Instances" and press "OK".  Immediately Evolution greys out.  I've been waiting about 5 minutes now to give it a chance to resolve on its own.  Has anyone experienced, or can anyone test this to confirm it's not just my system?  I'm using a fully updated (as of 4/15/09) Jaunty 64-bit install.  Fortunately, I now know the fix, which I outlined in my previous post.

Thanks.

Edit:  learned more.  If you create the event properly the first time (ie, recurring "forever") then it creates the event properly.  However, if you create it for 1 recurrence, then later go back to modify the event, that's when it locks up.  Strange.  Is there anyone in particular I should report this to?

---

### Post by Taiebot65 on 2009-04-16
I had exactly similar problem yesterday if you fill a bug i ll confirm it. I was looking for some log or debug i did not find anything....

---

### Post by timzak on 2009-04-16
> **Taiebot65 said:**
> I had exactly similar problem yesterday if you fill a bug i ll confirm it. I was looking for some log or debug i did not find anything....

I don't think I've ever filled a bug report before.  Can you provide a url where I should do this?  I'll be happy to fill out the report.  Thanks for confirming this issue!

Okay, I figured it out, I think.  Here's a link to the bug report:
[https://bugs.launchpad.net/bugs/362318](https://bugs.launchpad.net/bugs/362318)

---

### Post by dizzen on 2009-04-18
Hi there, seem to have the same problem : no way to display the calendar items, altough they are there since they popup... Anybody any clue ??

---


---
title: "Gwibber Notifications"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jacobmh on 2010-03-23
I am running Lucid Lynx Beta 1, upgraded from Karmic. 

My old Gwibber displayed new items in the Facebook newsfeed through notify-osd, which I enjoyed. It no longer does this under Lucid, even with "display notifications" checked and "only display notifications for mentions" unchecked in the Gwibber preferences. How do I reenable this?

---

### Post by descendent87 on 2010-03-23
Strange, another problem with gwibber. [http://ubuntuforums.org/showthread.php?t=1436969](http://ubuntuforums.org/showthread.php?t=1436969)
Facebook notifications are woking fine for me.

---

### Post by jacobmh on 2010-03-23
Are you using the indicator applet or not? I've heard that there is a correlation between that and notify-osd working.

---

### Post by ElSlunko on 2010-03-23
You know it was working fine for me in 10.04 alpha, then stopped in beta, and just did the HUGE update today & the notifications are working again. Of course I'm plagued by the bug that doesn't allow gwibber to load because of a bad stream.

---

### Post by jacobmh on 2010-03-23
I did an update, there's nothing more listed to do. Gwibber still works fine for me. Notifications still do not.

---

### Post by ElSlunko on 2010-03-23
Is python-indicate installed?

---

### Post by jacobmh on 2010-03-23
Yep, and Gwibber still works after the big update, and I have python-indicate installed and everything. I don't know what's wrong, but I guess I'll just have to wait for it to be fixed by another update.

---

### Post by victor9098 on 2010-03-25
I have the same problem, I get no notifications from gwibber through notify

---

### Post by jacobmh on 2010-03-25
Yep, the only notification bubbles I even get are for volume control.

Gwibber doesn't even work for me now, it crashes while updating. I suspect this is because it is saving information from a previous version instead of deleting everything like it should.

On the whole, taking into account the now-crowded notification area, the GDM formatting issues, the sleep problems, the frequent crashes of couchdb, and some bizarre changes in memory protection, I think this is one of the most buggy betas I've ever tested, and I've been testing them since Edgy Eft.

---

### Post by victor9098 on 2010-03-25
In my case I seem to get notifications for most other applications, my music players seem to work just fine. Then again, firefox is not sending notifications either, and I have updated to the new notification app.

Gnome Do has ceased to work unless it is run via terminal.

While Gwibber without notifications is rather pointless, can just keep twitter open in a browser tab rather then having a separate process running. While mine does not crash, it does sometimes turns grey as it freezes during updates, but returns to normal after a few seconds.

---

### Post by victor9098 on 2010-03-25
OK... I think it may be working now. This is what I did.

Went into Synaptic and reinstalled the following:
gwibber
gwibber-themes
gwibber-service
python-indicate

After that I logged off. Logged back in. Started Gwibber via the indicator applet (I should check to see if it runs automatically after logging in), checked all the settings.

In 'options' I have checked 'start service at login' and 'display notifications'

I have already had a 2 tweets pop up in notification bubbles!

---

### Post by jacobmh on 2010-03-26
Can someone confirm success at getting notification bubbles with a Facebook account? The debug mode error I get looks like a parsing error, and if that's the case everybody should be having this problem with Facebook feeds.

---

### Post by victor9098 on 2010-03-27
> **jacobmh said:**
> Can someone confirm success at getting notification bubbles with a Facebook account? The debug mode error I get looks like a parsing error, and if that's the case everybody should be having this problem with Facebook feeds.

Yes, I can confirm that, my updated only come from Twitter

---

### Post by jacobmh on 2010-03-27
I have submitted a Gwibber bug about the Facebook issue [here]("https://bugs.launchpad.net/gwibber/+bug/549755")

---


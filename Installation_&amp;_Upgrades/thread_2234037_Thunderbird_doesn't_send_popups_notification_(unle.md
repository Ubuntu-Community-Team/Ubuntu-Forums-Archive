---
title: "Thunderbird doesn't send popups notification (unless minimized)"
date: 2014-07-12
forum: Installation &amp; Upgrades
---

### Post by dovah on 2014-07-12
Hello guys!

I have an issue with Thunderbird 24.6.0 on my Asus running Ubuntu 12.04LTS (gnome 3 desktop).
 Even though it's set up to send me popup alerts for incoming mails (see pictures below), it doesn't do its work unless the thunderbird window is minimized in the application panel. I neither receive popups for upcoming events in the calendar, which is somehow pointless (I'd better check my mail in a browser or rely on google calendar web-access). 
However, every lib seems installed to allow popups (as I checked for the needed installation packages on google). 

If you have any ideas of how I could fix this, please let me know.

[https://www.dropbox.com/s/g5irutdqvywqkyb/Screenshot%20from%202014-07-12%2010%3A33%3A10.png](https://www.dropbox.com/s/g5irutdqvywqkyb/Screenshot%20from%202014-07-12%2010%3A33%3A10.png)
[https://www.dropbox.com/s/r5jy3a2emoogqwe/Screenshot%20from%202014-07-12%2010%3A33%3A28.png](https://www.dropbox.com/s/r5jy3a2emoogqwe/Screenshot%20from%202014-07-12%2010%3A33%3A28.png)

---

### Post by TheFu on 2014-07-12
I hate the thunderbird popups - how did you get them to stop?!!!!!  Please explain!
I'm running lxde.

---

### Post by dovah on 2014-07-12
I have no idea, I just installed the thunderbird package from Synaptic, see link below for further informations. What version did you installed? 

[URL="https://www.dropbox.com/s/4g02pxxfi8gyw8r/Screenshot%20from%202014-07-12%2014%3A40%3A05.png"]https://www.dropbox.com/s/4g02pxxfi8gyw8r/Screenshot%20from%202014-07-12%2014%3A40%3A05.png
[/URL]

**EDIT**: take a look here for further information -->[http://superuser.com/questions/87367/how-to-disable-thunderbird-notification](http://superuser.com/questions/87367/how-to-disable-thunderbird-notification)

---

### Post by TheFu on 2014-07-12
I'm on the normal 12.04 Ubuntu (patched weekly) version with lightning to connect to my Zimbra Enterprise email/calendar server.  I think the main issue is Unity - for you.

The package here: thunderbird         1:24.6.0+build1-0ubuntu0.12.04.1        

Perhaps if I remove D-Bus that will stop all the popups?  Not a fan of popups here.  Too annoying and distracting when trying to get work done. It would be preferable if they were added to a queue that could be displayed when requested.

BTW, there's usually no need to ever post an image. System data can always be gotten in highly efficient text formats.

---

### Post by dovah on 2014-07-12
No, I'm on gnome, not unity. I tried installing the gnome add-on for Thunderbird, but nothing changed.

---

### Post by TheFu on 2014-07-12
well, to get the message popups, they claim 

Edit -> Preferences -> General -> "When new messages arrive:"
Unchecking the "Show an alert"-Box should do the trick.

But I have that unchecked and still see the damn popups - and you don't - and don't see them!  I'm guessing it is like the "close" button in elevators. ;) Not really connected to anything.

[https://superuser.com/questions/87367/how-to-disable-thunderbird-notification](https://superuser.com/questions/87367/how-to-disable-thunderbird-notification) says there is an about:config option to control this.

---


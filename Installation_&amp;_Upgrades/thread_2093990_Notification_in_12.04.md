---
title: "Notification in 12.04"
date: 2012-12-12
forum: Installation &amp; Upgrades
---

### Post by Ravenwolf on 2012-12-12
Hi Guys!

I just upgraded to 12.04 and immediately installed Gnome and uninstalled Unity.
Everything is fine by now with one exception: There is a notification in the top panel, that comes up when a new song starts in Amarok or the battery is low, or when I received an email.
It only goes away when I click it and I don't want that ^^
Is there a possibility to get rid of it?

Thanks, Ravenwolf


Screenshot: [https://www.dropbox.com/s/y3wvp6dh0kvtqfl/Screenshot%20from%202012-12-12%2015%3A36%3A58.png](https://www.dropbox.com/s/y3wvp6dh0kvtqfl/Screenshot%20from%202012-12-12%2015%3A36%3A58.png)

---

### Post by Frogs Hair on 2012-12-12
Hello and Welcome

If you have the dconf editor installed you could try changing the value to 0 under notify osd.

The package notify-osd can also be removed though I have never done it. ```
sudo apt-get remove notify-osd
```  
I don't think mail notification is connected to this package but it will remove the notification bubbles. I don't save passwords in Thunderbird so get no new mail notifications.

---

### Post by Ravenwolf on 2012-12-14
It's actually no On Screen Notification, but appears in the panel... :-/

---

### Post by Ravenwolf on 2012-12-22
So, I finally found out, that it is Rhythmbox, which provides these  notifications, but I can't find any preferences to make them not show up  any more... 
Any ideas? 

Thank you! :)

---

### Post by Frogs Hair on 2012-12-22
If it is the notification in the screen-shot , that is Notify OSD.

---

### Post by Ravenwolf on 2012-12-22
Thanks, FrogsHair! 

But it's not this one. It's this one: 
[https://www.dropbox.com/s/y3wvp6dh0kvtqfl/Screenshot%20from%202012-12-12%2015%3A36%3A58.png](https://www.dropbox.com/s/y3wvp6dh0kvtqfl/Screenshot%20from%202012-12-12%2015%3A36%3A58.png) 

Ravenwolf :)

---


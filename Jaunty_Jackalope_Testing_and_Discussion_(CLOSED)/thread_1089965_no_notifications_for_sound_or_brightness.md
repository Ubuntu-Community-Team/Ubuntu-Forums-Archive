---
title: "no notifications for sound or brightness"
date: 2009-03-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Whise on 2009-03-07
i upgraded to jaunty but i dont get notifications for sound or brightness on my laptop

---

### Post by amano on 2009-03-07
A bit of searching would have told you that you have to use the human icon theme currently for it. Thus I guess that you have switched to another icon theme?

---

### Post by Darkshade on 2009-03-07
```
sudo cp /usr/share/icons/Human/scalable/status/notification-* /usr/share/icons/gnome/scalable/status/ && killall -15 notify-osd
```

And voala - working notifications no matter what icons you use! :D

---

### Post by Whise on 2009-03-07
thanks.. sorry about that

---

### Post by forumache on 2009-03-08
Whise,

just remember to delete those files you copied when the proper fix will arrive.

---

### Post by David A Knight on 2009-03-08
> **Darkshade said:**
> ```
sudo cp /usr/share/icons/Human/scalable/status/notification-* /usr/share/icons/gnome/scalable/status/ && killall -15 notify-osd
```

And voala - working notifications no matter what icons you use! :D

Close, but no cigar.  This will only provide working notifications for icon themes that inherit from the gnome theme.  If you use the Tango icon set this doesn't work.  Replacing gnome with tango in the above command does though.

---

### Post by Darkshade on 2009-03-08
> **David A Knight said:**
> Close, but no cigar.  This will only provide working notifications for icon themes that inherit from the gnome theme.  If you use the Tango icon set this doesn't work.  Replacing gnome with tango in the above command does though.

Actually it does work (at least for me). When an icon is missing in the iconset that you're using it automatically picks it from the default gnome icons.

---

### Post by chrisccoulson on 2009-03-08
The correct fix is to actually do:

```
sudo mv /usr/share/notify_osd /usr/share/notify-osd
```

See [https://bugs.edge.launchpad.net/ubuntu/+source/notify-osd/+bug/338837]("https://bugs.edge.launchpad.net/ubuntu/+source/notify-osd/+bug/338837")

---

### Post by plun on 2009-03-08
(OT warning)

Hello whise !  Nice to see you again... :D

We had some trouble with screenlets during the python transition to ver 2.6.

What happended with your new project ?

Screenlets also probably needs some "love" from a skilled developer as you.

;)

---


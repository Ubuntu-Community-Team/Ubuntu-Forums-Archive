---
title: "Update Notification Icon"
date: 2010-04-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by benjamimgois on 2010-04-25
I know that Lucid Lynx is almost ready for release, but i would like to ask a question. Why the Update Notification Icon was removed from ubuntu some releases ago ? 

[IMG]http://www.watchingthenet.com/wp-content/uploads/image/ubuntu-update-notification7.gif[/IMG]

I think it's so dam usefull to receive an message telling that there are 79 updates avaiable. Somebody ??

---

### Post by ToxicBurn on 2010-04-25
wow i did not know it was removed i loved having that pop up when i had updates 

I also would like a answer on this ?

---

### Post by Merk42 on 2010-04-25
It was decided in either Jaunty or Karmic that instead of the small icon, the update manager itself would pop up.
I believe the reasoning was the small icon was too easily ignored so people often had out of date, and therefore less secure, systems.


So you are still notified of updates, just in a different way.

---

### Post by FuturePilot on 2010-04-25
```
gconftool-2 -s --type bool /apps/update-notifier/auto_launch false
```

Log out and back in.

---

### Post by benjamimgois on 2010-04-25
> **Merk42 said:**
> It was decided in either Jaunty or Karmic that instead of the small icon, the update manager itself would pop up.
I believe the reasoning was the small icon was too easily ignored so people often had out of date, and therefore less secure, systems.


So you are still notified of updates, just in a different way.

Thanks for the answer. Strange... The notification window never pop up for me. Maybe because i have the habit of frequently update the system. But i still thinking that an update icon or even a notification through notify-osd would be a nice thing.

---

### Post by benjamimgois on 2010-04-25
> **FuturePilot said:**
> ```
gconftool-2 -s --type bool /apps/update-notifier/auto_launch false
```

Log out and back in.

Ow, that was quick. Thanks dude, now my notification icon is back :)

---


---
title: "Grub2 not working"
date: 2010-01-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cecilpierce on 2010-01-07
what causes this:
"entering rescue mode...
 error: menu not initialized
 grub rescue> " ?
grub was working til i did todays up grade,
thanks

---

### Post by VMC on 2010-01-07
> **cecilpierce said:**
> what causes this:
"entering rescue mode...
 error: menu not initialized
 grub rescue> " ?
grub was working til i did todays up grade,
thanks

Need more info than that. You can play around with grub. Hit tab or type help. ls will work, so will geometry among others. fdisk and blkid output would be nice.

---

### Post by cecilpierce on 2010-01-07
I posted this in GRUB2 theming for lucid? but somehow it was moved here.
I have bean123 ppa with burg grub-pc for theming.
Yesterday it was working fine but after todays update
grub-install didn't work, it goes to "error: menu not initialized".
It also made some new scrips in /etc/grub.d
Thanks, Cecil

---

### Post by cariboo on 2010-01-07
I moved your post to a separate thread, because you didn't mention anything about grub theming, and It looked like you did an update and grub wouldn't start.

---

### Post by cecilpierce on 2010-01-07
Thanks for explaining that cariboo907, I couldn't figure that out! My apology, I'm getting brain dead in my old age.
Cecil

---

### Post by ranch hand on 2010-01-07
You need to list these little details.

Do this;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

ignoring file editing that you probably do not need to do.  This should get the original grub1.97 running again.  It may not be real purty for the few seconds you see it but it will work.

---

### Post by kansasnoob on 2010-01-07
I'd like to see the output of the Boot Info Script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

This sounds very much like some Wubi problems I've encountered in the past 2 or 3 days.

---


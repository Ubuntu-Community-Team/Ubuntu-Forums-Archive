---
title: "CheckGmail and notifications"
date: 2009-04-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by KhaaL on 2009-04-20
CheckGmail users, are you getting new email notifications in jaunty or is it just my install that's being goofy?

---

### Post by Triggerhapp on 2009-04-20
Working as expected here, unless you specifically mean "libnotify" :)

---

### Post by KhaaL on 2009-04-20
> **Triggerhapp said:**
> Working as expected here, unless you specifically mean "libnotify" :)

Exactly! I was speaking of the (non-intrusive) notification popups :P

---

### Post by Triggerhapp on 2009-04-20
the notifications are still the old red on white boxes, I believe this is because checkgmail was created without thought for the system notifications. I'm personally happy with it as it is.

---

### Post by KhaaL on 2009-04-20
hmmm okay, i'm not getting any notifications at all from CheckGmail, i thought it was because of the new libnotify. I'll have to look into it. thanks for the reponsone.

---

### Post by MacUntu on 2009-04-20
Some weeks ago I played around to get this working and replaced the popup call in the giant perl script with a simple call to "notify-send". I'm sure that's not *the* way to implement notifications but it worked. 

Unfortunately you cannot have detailed popups with hyperlinks so I ended up with using the original version - I don't want to have an application with two types of notification bubbles.

---

### Post by paradigm2 on 2009-04-20
> **MacUntu said:**
> Some weeks ago I played around to get this working and replaced the popup call in the giant perl script with a simple call to "notify-send". I'm sure that's not *the* way to implement notifications but it worked. 

Unfortunately you cannot have detailed popups with hyperlinks so I ended up with using the original version - I don't want to have an application with two types of notification bubbles.

I hope check gmail is left alone unless the same exact functionality is provided.  I like being able to click the title and se the message within the box, as well as the ability to mark a message or all messages read.  A passive notification box in my opinion would really take away from the program.

But if they used it for the new notification system only for initial notification (and the icon still changed, being clickable), I would see THAT as an improvement.

---


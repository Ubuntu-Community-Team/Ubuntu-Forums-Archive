---
title: "2 questions (pidgin, and updates)"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by joshuapbell on 2009-04-01
Okay so I have a fresh install of beta, and I have a couple of questions.

1. When I press the x on pidgin it completely closes. instead of going to the panel.

2. Also, shouldn't the update thing automatically come up and tell me when there are updates??

Also, just a gripe, I hope this isn't a permanent color scheme for the forums because it is giving me a headache...

any help would be appreciated thanks.

---

### Post by FuturePilot on 2009-04-01
> **joshuapbell said:**
> Okay so I have a fresh install of beta, and I have a couple of questions.

1. When I press the x on pidgin it completely closes. instead of going to the panel.

2. Also, shouldn't the update thing automatically come up and tell me when there are updates??

Also, just a gripe, I hope this isn't a permanent color scheme for the forums because it is giving me a headache...

any help would be appreciated thanks.

1.Do you have the Notification Applet on your panel? If you do it should be hidden there when you click the X. Don't quote me on that, I haven't used Pidgin in a while.

2. I've also been wondering about that. Every so often I check Update Manager and I see a bunch of updates when I didn't even have to click the Check button, yet it never notified me of these updates.

As for the forum color, check the date ;)

---

### Post by tom56 on 2009-04-01
> **joshuapbell said:**
> Okay so I have a fresh install of beta, and I have a couple of questions.

1. When I press the x on pidgin it completely closes. instead of going to the panel.

2. Also, shouldn't the update thing automatically come up and tell me when there are updates??

Also, just a gripe, I hope this isn't a permanent color scheme for the forums because it is giving me a headache...

any help would be appreciated thanks.

1. Click the envelope icon to minimise Pidgin to the tray.
2. You will be notified of updates every 7 days, or every 24hrs in the case of security updates.

---

### Post by FuturePilot on 2009-04-01
> **tom56 said:**
> 
2. You will be notified of updates every 7 days, or every 24hrs in the case of security updates.

What!? :-s Is there a reason for this change? It used to remind you ever 24 hours if updates were available regardless of priority. I liked that way better.

---

### Post by joshuapbell on 2009-04-01
> **tom56 said:**
> 1. Click the envelope icon to minimise Pidgin to the tray.
2. You will be notified of updates every 7 days, or every 24hrs in the case of security updates.

So no more pidgin icon in the tray?

---

### Post by DarkReaper79 on 2009-04-01
1. In pidgin, go to tools> preferances> and on interface tab make sure show sys tray icon is set to always. It works for me.

2. I think its a bug, I havent ha dit since I had alpha6

---

### Post by FuturePilot on 2009-04-01
Regarding #2

[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945]("https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945")

I don't like this new behavior :(

---

### Post by Polygon on 2009-04-02
I am confused...why did they change the way the update notifier worked if the system they want to use is not complete? They say they have some cool way of doing it, but its not finished so they are just having the update notifier pop up randomly. Bad move

also, the user should be notified about updates every day, not every week. Thats a terrible idea.

---

### Post by stoffe on 2009-04-02
> **FuturePilot said:**
> What!? :-s Is there a reason for this change? It used to remind you ever 24 hours if updates were available regardless of priority. I liked that way better.

During development/testing this is unconvenient and I've taken to updating manually every day instead. However, I think it makes sense in a stable system, where updates should be few, and so they can be lumped together and not pop up every day. Since most updates in normal use don't matter to me, it's probably ok. I do think that most people hanging out in this forum will disagree though, as it is people who actively wants the latest and greatest as soon as possible. But again, I think it makes sense for the user-type users who use the computer to get some work done. :)

---

### Post by FuturePilot on 2009-04-02
> **Polygon said:**
> 

also, the user should be notified about updates every day, not every week. Thats a terrible idea.

My exact thoughts. It's even more important to be notified frequently during development cycles. Even once it goes stable, once a week is still silly. Say I'm affected by $ANNOYING_BUG, and there's an update that fixes said bug. I'm supposed to wait a week before being notified that this fix is available even if it was available 5 days ago?

Anyways there is a way to get the old behavior back.

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```
log out and back in.

---


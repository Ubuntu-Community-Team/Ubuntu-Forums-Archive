---
title: "Lubuntu 18.04 not appars notification for news updates"
date: 2018-07-15
forum: Installation &amp; Upgrades
---

### Post by wonder2 on 2018-07-15
Hello.
Recently, I installed in my laptop a lubuntu 18.04.
In the first days, I have a notification with news updates for system (for example, firefox and other packets of system).
Since some day, now, I don't have any notification for new updates and I now that, I have new updates.
If run manually, appears the news updates and the option for update.
But, like indicate, since some day (and I don't made any change about this) I don't received the notifications of news updates.
And I don't know how search more for view possible issue...

Thanks and regards!

---

### Post by Xian on 2018-07-15
The update-manager probably got removed from your startup applications. 

Add the program back manually .... and should return to expected behavior.

How-To: [https://askubuntu.com/questions/159008/how-to-add-startup-applications-in-lubuntu](https://askubuntu.com/questions/159008/how-to-add-startup-applications-in-lubuntu)

---

### Post by wonder2 on 2018-07-16
Hello.
I review in 
[LIST=1]
[*]**"Preferences"** > **"Default applications for LXSession"**;
[*]In the opened window, in the option **"Autostart"**;
[/LIST]
[FONT=inherit]I have check "update notifier"

I add the "update-manager", and go to try.

Thanks.[/FONT]

---

### Post by Impavidus on 2018-07-16
Because of [phased updates](https://wiki.ubuntu.com/PhasedUpdates) the update manager doesn't always immediately notify you of the less important updates. Maybe there's no problem at all.

---

### Post by wonder2 on 2018-07-16
The problem is, after some days on I know that I have some updates for install, not appears or indicate that, I have news updates.

After the test of indicate Xian, appears a update notification of new updates and I view that, I have updates like Firefox, and others of the system.

Thanks.

---


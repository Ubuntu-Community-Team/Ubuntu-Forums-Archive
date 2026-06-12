---
title: "Ubuntu asks for my google password at login"
date: 2013-11-05
forum: Installation &amp; Upgrades
---

### Post by koma77 on 2013-11-05
After upgtrading to 13.10, as soon as I log in I get a anonymous-looking GUI form that requests me to enter my gmail password.

Even if I enter the correct password it will say that it failed, the only way to get rid of it is to click cancel. And then it will appear again at next boot.

How can I find out which application or service is doing this, and for what reason?

---

### Post by sanderj on 2013-11-05
Can you post a screendump / picture of the GUI asking for your gmail password?

---

### Post by koma77 on 2013-11-05
Sure; attached is a photo (!) of the GUI since the GUI itself is too modal to allow the dash to open or the PrintScreen button to take a screenshot.

---

### Post by sanderj on 2013-11-05
When I Google that "add this password to your keyring", I get "evolution" hits. So, do you use the mail program evolution on your system?

---

### Post by koma77 on 2013-11-05
I don't use evolution directly; I use thunderbird.

But I guess evolution has a backend running which keeps the calendar in the panel running. That would probably start up automatically on login...

Is there an easy way to see if that is indeed the problem?

---

### Post by sanderj on 2013-11-05
The last time I used a mail application was at least 8 years ago, so I have no experience with evolution of panel mail items.

I would search in that panel for the mail setting, and change the gmail.com part to 'doesnotexist.com' and then save. You will then automagically see if that was the hotspot.

---

### Post by koma77 on 2013-11-05
I mean, the calendar next to the clock in the gnome unity thingy is basically powered by an evolution backend if I understand this correctly, so that's what may be causing this then...

---

### Post by koma77 on 2013-11-05
Evolution is certainly involved: when I start evolution manually I get the exact same GUI popup.

---

### Post by grahammechanical on 2013-11-05
Perhaps Ubuntu 13.10 is trying to migrate the settings that you had in the earlier version of Ubuntu. Have you tried going into System Settings>Online Accounts. I see that there is already a place for Google, which includes Gmail, Google Docs, Google+, YouTube and Picasa. If you click on it you will get a request to authorise Ubuntu to access your Google account. It requires your email address and password. It is all to do with Online Notifications.

Regards.

---

### Post by koma77 on 2013-11-06
My google account in online accounts was OK. I even tried to remove it and add it back again with no success.

The strange thingis that when I enter my password it says that it is not correct. And nothing obvious is broken even if I click cancel so at this point is just annoying and makes me abit concerned about security: I don't want anonymous password requests popping up from nowhere...

---

### Post by sanderj on 2013-11-06
> **koma77 said:**
> My google account in online accounts was OK. I even tried to remove it and add it back again with no success.

The strange thingis that when I enter my password it says that it is not correct. And nothing obvious is broken even if I click cancel so at this point is just annoying and makes me abit concerned about security: I don't want anonymous password requests popping up from nowhere...

Then just remove google and gmail accounts from your settings in Ubuntu. My Ubuntu system never pops with a windows requesting my gmail password.

---


---
title: "Notifications - Skype and Google Mail?"
date: 2009-03-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Lorenz on 2009-03-17
I hope this doesn't count as spamming - I know there are many threads about the new notifications already. However, I feel that 2 topics really should be addressed. I have long used clients such as Thunderbird and Evolution, but recently I have completely switched to googlemail. I just see no reason anymore to use a seperate program for writing emails, putting tasks and appointments in my calendar (I use it offline too with gears) etc. 

The new notifications work like a charm, especially with qwibber and Facebook and Twitter. What I really miss, is that the notification system cooperates with Google Mail (or lets say webmail in general - couldn't it be set up with an authorised RSS feed?) and Skype! Any chance we will see this? Or is it not doable from a technical point of view? thanks for your opinions!

---

### Post by Polygon on 2009-03-17
the notifications can't come from a website, but if you use one of the many programs that put a gmail icon in your taskbar, im sure some if not all of them can be updated to use the new notification system

as for skype, that is up to the skype developers as the program is closed source.

---

### Post by Lorenz on 2009-03-17
> **Polygon said:**
> the notifications can't come from a website, but if you use one of the many programs that put a gmail icon in your taskbar, im sure some if not all of them can be updated to use the new notification system

as for skype, that is up to the skype developers as the program is closed source.

Can you (or anyone reading this) recommend a good one? I googled some, but not sure if I found the right things.

---

### Post by Sophont on 2009-03-18
> **Lorenz said:**
> Can you (or anyone reading this) recommend a good one? I googled some, but not sure if I found the right things.

mail-notification. You'll find it in the repository with Synaptic.

Or you just
```
sudo apt-get install mail-notification
```
in terminal.

---

### Post by Lorenz on 2009-03-18
Thank you Sophont, unfortunately it has it's own notification and doesn't use the jaunty style :(

---

### Post by gnomeuser on 2009-03-18
I think this raises a whole other set of questions. In this Web 2.0 world with cloud computing. Why is the desktop we currently have so poorly integrated with these new fangled technologies.

Most people today probably use something like GMail instead of a desktop client, yet we can't associate mailto links with the GMail compose window and notifications of new mails can't be set up anywhere despite imap access being available for monitoring.

These seem like simple tasks that should just work.

---

### Post by PsychedelicReaction on 2009-03-18
> **Lorenz said:**
> Thank you Sophont, unfortunately it has it's own notification and doesn't use the jaunty style :(

Run gconf-editor, go to apps -> mail-notification -> popups and clear the "actions" value :)

---

### Post by Lorenz on 2009-03-18
> **PsychedelicReaction said:**
> Run gconf-editor, go to apps -> mail-notification -> popups and clear the "actions" value :)

Thank you very much indeed! this works a treat!

---


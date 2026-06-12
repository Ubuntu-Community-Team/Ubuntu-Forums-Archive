---
title: "Upon upgrading to 20.04, no applications launch from gnome-shell (except favorites)"
date: 2021-04-21
forum: Installation &amp; Upgrades
---

### Post by rossetti-gabriel on 2021-04-21
Hi,

I upgraded to 20.04 (from 19.04) and now when I search for an application and I click on it, it does not launch, nothing happens. If I add the application to my favorites, and click there, then it works. How can I figure out what is wrong and fix it please?

Thank you,
Gab

---

### Post by CelticWarrior on 2021-04-21
Welcome.

> [COLOR=#000000]I upgraded to 20.04 (from 19.04)[/COLOR]
You couldn't have, not directly anyway.
Dido you upgraded like 19.04 -> 19.10 -> 20.04? Some other method? Or was it actually a fresh installation?
If you did install 20.04 from scratch did you kept the older /home?

---

### Post by rossetti-gabriel on 2021-04-22
Hi,

Thank you :-)

yes, you are right, Eoan => 19.10, not 19.04. So I upgraded as in used the software updater.

---

### Post by rossetti-gabriel on 2021-04-27
Nobody knows how I can debug the issue?

---

### Post by rossetti-gabriel on 2021-04-27
Hi,

 I posted here: [https://ubuntuforums.org/showthread.php?t=2460923&p=14033229#post14033229](https://ubuntuforums.org/showthread.php?t=2460923&p=14033229#post14033229) and I don't want to crosspost, but I think my original post was not in the correct forum.

Does someone know how to debug the issue I am having please?

Thank you,
Gab

---

### Post by ajgreeny on 2021-04-27
Posts merged to avoid confusion.

Please do not create duplicate threads; report the wrongly sited thread with the "Report Post" button below left of every post and ask for it to be moved.

---

### Post by ajgreeny on 2021-04-27
Can you start applications not already in your Favourites by using terminal commands?

---

### Post by ubfan1 on 2021-04-27
Desktop icons in the .desktop extension files now need to have a right-click and set the "Allow Launchnig" checkoff before they will work.  But I thought the default was to launch a text editor, so that's not "nothing".

---

### Post by rossetti-gabriel on 2021-04-29
> **ajgreeny said:**
> Posts merged to avoid confusion.

Please do not create duplicate threads; report the wrongly sited thread with the "Report Post" button below left of every post and ask for it to be moved.

Thanks, I didn't know that button

---

### Post by rossetti-gabriel on 2021-04-29
> **ajgreeny said:**
> Can you start applications not already in your Favourites by using terminal commands?


yes

---

### Post by rossetti-gabriel on 2021-04-29
> **ubfan1 said:**
> Desktop icons in the .desktop extension files now need to have a right-click and set the "Allow Launchnig" checkoff before they will work.  But I thought the default was to launch a text editor, so that's not "nothing".

But I don't launch from the desktop, I go to the overview (Activities button/hotspot), in the search bar type in the apps name and click on it. I expect the app to open (as it always has) but nothing happens. If I add the pp to the side bar (my favorites) or type the name in the command line it opens fine.

---

### Post by ubfan1 on 2021-04-29
I see the .desktop files I brought in from an older distribution, and which needed the explicit right-click/allow launching, work from the desktop, but fail from the Activities/search/.  They are treated as unknown files, and a text editor is invoked. Looks like Gnome "took over" their launching.  Maybe  setting a mimetype would work, but I don't know what Gnome uses to invoke a desktop file.

---

### Post by rossetti-gabriel on 2021-04-29
> **ubfan1 said:**
> I see the .desktop files I brought in from an older distribution, and which needed the explicit right-click/allow launching, work from the desktop, but fail from the Activities/search/.  They are treated as unknown files, and a text editor is invoked. Looks like Gnome "took over" their launching.  Maybe  setting a mimetype would work, but I don't know what Gnome uses to invoke a desktop file.

Ah, I see what you mean, but it should do something in this case, either open in the terminal, execute, ask me or like you open the editor. I am not sure also how I would update all the shortcuts at once. Wat would be nice is to be able to see a log about what happens, so I can see if there is an error maybe.

---

### Post by ubfan1 on 2021-04-29
Try to install dex, and then associate the .desktop in a mimetype.  dex worked for me directly on a non .wine desktop file, but seemed to fail in a winepath, and just opened a file selector.

---

### Post by rossetti-gabriel on 2021-05-03
> **ubfan1 said:**
> Try to install dex, and then associate the .desktop in a mimetype.  dex worked for me directly on a non .wine desktop file, but seemed to fail in a winepath, and just opened a file selector.


Nope, doesn't work any better for me. How can I debug the issue?

---


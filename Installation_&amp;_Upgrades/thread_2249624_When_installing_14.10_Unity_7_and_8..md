---
title: "When installing 14.10? Unity 7 and 8."
date: 2014-10-23
forum: Installation &amp; Upgrades
---

### Post by irv on 2014-10-23
When installing Ubuntu 14.10 can you install it with Unity 8? I would think it still comes with Unity 7?
I played around with Unity 8 and it is completely different then 7. I have a touch screen so I am interested in giving it a try even though there are a lot of bugs yet.
Maybe another good question would be can you switch between them?

---

### Post by grahammechanical on 2014-10-23
Ubuntu 14.10 does indeed come with Unity 7. Earlier today I tried unity8-desktop-session-mir on 14.10 and it does give an option at the login screen but all I got was a black screen, even though I am using Nouveau.

There is supposed to be an option to load an experimental Unity 8 session on 14.04 and 14.10 and in future 15.04 but I did not get very far with it in 14.04 and now in 14.10 it still is not working.

[https://wiki.ubuntu.com/Unity8Desktop](https://wiki.ubuntu.com/Unity8Desktop)

Now here is something strange. The wiki page says

> [COLOR=#333333][FONT=Ubuntu Beta]Unity 8 uses Mir display technology. Proprietary video drivers do not yet offer the required level of support for Mir, so your experience if you're using the binary block nVidia or AMD drivers will be somewhat disappointing.[/FONT][/COLOR]

Now, I have installed Ubuntu Desktop Next and with Nouveau I got login screen bounce but with Nvidia drivers I got beyond the LightDM log in screen on to the Phone login screen and to the phone UI as well. But the sad thing is that at this stage of development all we get with Desktop Next is a full screen version of the phone UI. I cannot find any way of bring out the normal Ubuntu desktop. 

But I am beginning to wonder if unity8-desktop-session-mir now works better on Nvidia drivers than it does on Nouveau.

Regards.

---

### Post by irv on 2014-10-23
I tried it off a USB drive and it worked on my Asus laptop. I also tried it in virualbox but it didn't run right.

---


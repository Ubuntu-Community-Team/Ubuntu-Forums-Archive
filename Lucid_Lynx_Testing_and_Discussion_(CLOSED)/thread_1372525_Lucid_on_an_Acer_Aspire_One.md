---
title: "Lucid on an Acer Aspire One"
date: 2010-01-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by teh603 on 2010-01-04
Finally got tired of seeing the .iso sitting around on my desktop, so I burned Alpha 1 to my USB stick to see how things went. Here's a few things I've noticed:

* Startup "thermometer" doesn't work. It just sat there for minute or so, dumped me to a page of command prompt text, and then gave me pointer control and played the startup chime.

* No option to set "shared key" instead of "open system" when first creating a connection to a wifi network. Editing the connection info once created works.

*Empathy doesn't seem to be connecting when given my account information for the first time. After quitting and then reloading it seems to work fine.

*Sound is STILL borked. Bug filed. Which is very very odd considering it plays the startup chime normally.

*Software Center crashed. Reported and apparently somebody's fixed it already. Bring back Synaptic plz?
Edit: Synaptic still answers me from the command prompt. Take that, software center!

* Suspend seems to work fine. Not trying Hibernate for lack of swap space.

*Need to check battery. Claims 2 hours 20 minutes like when the laptop was new (hell, better'n when it was new), but I need a chance to actually check how it works.

*Odd display issue- it seems to act like its resizing, at odd times. Reported.

*Seems to have fixed cell modem performance issues I observed under Karmic.

*Wifi light still fixed as it was under Karmic, but performance is better.

---

### Post by phillw on 2010-01-04
>  *Sound is STILL borked. Bug filed. Which is very very odd considering it plays the startup chime normally.

Th couple of audio gotchas that got me were.
1) not having the restricted extras installed
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)    The one for 9.04 & 9.10 worked fine for me.

2) having the modem hardware installed - and specifically enabled.
System --> Administration --> Hardware Drivers

I'm sorry if you've already tried them both. The modem one took me a while to find out about.

Regards,

Phill.

---

### Post by teh603 on 2010-01-04
I'll try again, since I don't have the laptop started up, but the hardware drivers thing might be the issue. I don't see how the restricted formats issue could cause the system beep to stop playing, though.

---

### Post by phillw on 2010-01-04
> **teh603 said:**
> I'll try again, since I don't have the laptop started up, but the hardware drivers thing might be the issue. I don't see how the restricted formats issue could cause the system beep to stop playing, though.

If it's gone mute on you .. then, I'd have a bet on the modem driver !! *Although* it has not been unknown for my sound to suddenly be set to mute in Sound Preferences, which can have me scratching my head for a while !!!

Regards,

Phill.

---

### Post by Seventh Reign on 2010-01-04
> **teh603 said:**
> 

*Software Center crashed. Reported and apparently somebody's fixed it already. Bring back Synaptic plz?
Edit: Synaptic still answers me from the command prompt. Take that, software center!

They Removed Synaptic????  I know they're were supposed to merge everything into the Software Center eventually, but its wayyyyy too early to remove it altogether.

---

### Post by teh603 on 2010-01-04
> **Seventh Reign said:**
> They Removed Synaptic????  I know they're were supposed to merge everything into the Software Center eventually, but its wayyyyy too early to remove it altogether.Ended up looking like they hadn't, or it reappeared in the menu after I called it up thru the terminal. Not sure which, because I'm pretty sure I didn't see it beforehand.

It seems like sound itself isn't borked, but the system doesn't play a sound when you change the system volume like it does in most other computers and I believe Jaunty. Which is an annoying "issue."

---

### Post by phillw on 2010-01-04
> **teh603 said:**
> It seems like sound itself isn't borked, but the system doesn't play a sound when you change the system volume like it does in most other computers and I believe Jaunty. Which is an annoying "issue."

Yes, very, very annoying on those systems whereby it does. **I'm changing the volume, for crying out loud ---- All my attention is on the slider --- WHY Beep at me ?**  If they're going to leave it like it is, I for one, will be a very happy bunny !!!  (I also like the new little status window that shows up if you just use your Fn - Volume control, coz you're too lazy to click on the speaker)

Just goes to show, you can't please all the people all of the time !!!

Yeah, they were playing with apt a day or two back. I've just done a quick head count, and i think summat like 300 alterations went thru as 'Accepted' today -- yikes !!!  :)

Regards,

Phill.

---


---
title: "Any way to remove icons from indicator applet?"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Luke has no name on 2010-04-23
I can't remove the useless envelope, and for some unknown reason, the Universal Access icon has decided to plant itself in the top right. I don't want it there, but there are no preferences with the indicator applet. 

I understand the desire for consistency in the indicator interface, but it could definitely be a bit more flexible. 

Any help at getting these icons (esp the UA one) off my desktop would be nice. Unfortunately, I feel someone will come in here and tell me to remove some obscure package, which while it may work, should not be the way this needs to be done.

---

### Post by Didius Falco on 2010-04-23
> **Luke has no name said:**
> I can't remove the useless envelope, and for some unknown reason, the Universal Access icon has decided to plant itself in the top right. I don't want it there, but there are no preferences with the indicator applet. 

I understand the desire for consistency in the indicator interface, but it could definitely be a bit more flexible. 

Any help at getting these icons (esp the UA one) off my desktop would be nice. Unfortunately, I feel someone will come in here and tell me to remove some obscure package, which while it may work, should not be the way this needs to be done.

If you want the "envelope" gone, remove the indicator-messages package,
and keep indicator-sound (which is for the volume) and indicator-application installed.
Don't remove indicator-applet, which is the host applet that all of the above plug into.

```
sudo aptitude purge indicator-messages
```

To remove the  "universal access" icon from notification area:

Alt+F2

```
gnome-keyboard-properties
```

under accessibility uncheck the box that says "Accessibility features can be toggled with keyboard"

The Access Icon should disappear right away, but the envelope will probably stay until you log out and back in or reboot.

I agree that it needs to be more consistent and accessible. Hopefully we'll see a control panel of some kind that let's you pick and choose which icons to display.

Meanwhile, I hope this helps. 

Regards,

Didius

---

### Post by chriskin on 2010-04-23
can i move to the notification area icons that used to be there but now are at the indicator applet?
the applet takes too much space for my screen and its controls are strange (left click should open the app, right click the properties. not left click opens the app and right click send you to the applets menu (!) - if i wanted to be there i would click the small lines/dots at the start, like other applets do)

---

### Post by VMC on 2010-04-23
> **Didius Falco said:**
> If you want the "envelope" gone, remove the indicator-messages package,
and keep indicator-sound (which is for the volume) and indicator-application installed.
Don't remove indicator-applet, which is the host applet that all of the above plug into.

```
sudo aptitude purge indicator-messages
```

Thank you! You answered a question I had but never asked because I didn't think it was possible. I thought I was stuck with that empty envelope. that purge removed it. I had already remove evolution and the gang, so it was just empty anyway.

---

### Post by Didius Falco on 2010-04-23
> **chriskin said:**
> can i move to the notification area icons that used to be there but now are at the indicator applet?
the applet takes too much space for my screen and its controls are strange (left click should open the app, right click the properties. not left click opens the app and right click send you to the applets menu (!) - if i wanted to be there i would click the small lines/dots at the start, like other applets do)

You have to be more specific. Package maintainers are being encouraged to write plugins that allow their app to use the indicator applet. 

For Rhythmbox, go to **Edit/Plugins/Status Icon** and uncheck the  box. This particular plugin controls both the status icon that appears  in the notification app and the status popups, so it's a case of both or  neither. Personally, I'd rather have a separate button on the menu  panel, so it works out fine for me.

For Empathy, it's **Edit/Preferences/Notifications**. Uncheck the **Enable  bubble notifications** radio button and Bob's your uncle.

Basically, you need to dig through the preferences and plugins for most  apps.

> **VMC said:**
> Thank you! You answered a question I had but never  asked because I didn't think it was possible. I thought I was stuck with  that empty envelope. that purge removed it. I had already remove  evolution and the gang, so it was just empty anyway.


You are very welcome. I'm considering writing up a quick how-to on this, or at least saving a boiler-plate template post, as this seems to come up a lot.

Ideally, I'd like everyone to contribute information on the name and location of these plugins for all apps, or at least those most commonly used.

I'd be nice to have a master list as a reference, which everyone that needs the info could be referred to...

---

### Post by obscur156 on 2010-04-24
Thanks Didius,i was anoyed too by this envelope.
Best regards.

---

### Post by shindou01 on 2010-04-24
> **Didius Falco said:**
> If you want the "envelope" gone, remove the indicator-messages package,
and keep indicator-sound (which is for the volume) and indicator-application installed.
Don't remove indicator-applet, which is the host applet that all of the above plug into.

```
sudo aptitude purge indicator-messages
```To remove the  "universal access" icon from notification area:

Alt+F2

```
gnome-keyboard-properties
```under accessibility uncheck the box that says "Accessibility features can be toggled with keyboard"

The Access Icon should disappear right away, but the envelope will probably stay until you log out and back in or reboot.

I agree that it needs to be more consistent and accessible. Hopefully we'll see a control panel of some kind that let's you pick and choose which icons to display.

Meanwhile, I hope this helps. 

Regards,

Didius
then how do I restore the volume icon?

---

### Post by barbz127 on 2010-04-24
Add the indicator applet back onto the panel, if you removed the indicator-messages package you should only have the volume controls I believe.

Cheers
Paul

---

### Post by chriskin on 2010-04-24
> **Didius Falco said:**
> You have to be more specific. Package maintainers are being encouraged to write plugins that allow their app to use the indicator applet. 

For Rhythmbox, go to **Edit/Plugins/Status Icon** and uncheck the  box. This particular plugin controls both the status icon that appears  in the notification app and the status popups, so it's a case of both or  neither. Personally, I'd rather have a separate button on the menu  panel, so it works out fine for me.

For Empathy, it's **Edit/Preferences/Notifications**. Uncheck the **Enable  bubble notifications** radio button and Bob's your uncle.

Basically, you need to dig through the preferences and plugins for most  apps.


i don't want them gone, i want them back to the notification area
sound, transmission and emesene should be at the notification area, not indicator applets
will they go back there if i install karmic's panel?

---


---
title: "Stopping the Notifications"
date: 2010-04-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Captain Smiley Pants on 2010-04-20
Hi, while testing out Lucid for a Eee 1005HA and things seems to be smooth sailing (besides hardware acceleration for video working... a different thread though), except one thing that's kind of bugging me.

While playing Rhythmbox and having new music come and go, I get a notification about it in one of my displays. I usually turn this off with a new installation, and usually it IS because of Rhythmbox itself. I've looked around in the preferences and have found nothing.

Later, while using the chat software preloaded on Lucid, the same type of notification came up when people were chatting with me. So this is making me wonder... Is this Notification software system wide?

Is there a way to edit what software can and cannot use the notifications? Is there a way to, if needed, turn off the notifications completely? Is it a glitch or error on my end when I highlight a notification and it vanishes, and if I'm quick enough to realize I can take my mouse off the notification it will be right back where my mouse previously was until the notification dies off?

I kind of miss just being able to right click on these to make them go away really quick. Hopefully this is all just beta stuff...

---

### Post by Didius Falco on 2010-04-20
Third party apps are being encouraged to use the notications system, but I've been able to turn things off that I didn't want.

For Rhythmbox, go to **Edit/Plugins/Status Icon** and uncheck the box. This particular plugin controls both the status icon that appears in the notification app and the status popups, so it's a case of both or neither. Personally, I'd rather have a separate button on the menu panel, so it works out fine for me.

For Empathy, it's **Edit/Preferences/Notifications**. Uncheck the **Enable bubble notifications** radio button and Bob's your uncle.

Basically, you need to dig through the preferences and plugins for most apps.

I hope this helps...

Regards,

Didius

---

### Post by rogerpittman on 2010-04-20
I think what you're looking for is Broadcast Messaging Preferences.  Go to **System** --> **Preferences** --> **Broadcast Preferences**.  From there you can choose which messages you receive.

---


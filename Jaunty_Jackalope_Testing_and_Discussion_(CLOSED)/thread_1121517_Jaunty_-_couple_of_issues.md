---
title: "Jaunty - couple of issues"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Tom_T on 2009-04-10
Hi
I've just upgraded my Acer 1694WMLI Laptop from 8.10 to 9.04.

Upgrade went fine, but today a couple of strange things have happened.

When I booted up the default login screen has changed. Instead of the new Jaunty login screen I got last night, I now get a sort of grey screen listing all my users. 

I can still login, but it but now it doesn't remember by keyring.

After the upgrade when I connected to the wireless or changed the volume on the laptop a new dark popup appeared and showed my wireless connection or volume settings.  Today it's back to the usual 8.10 popup.

The normal logout / change user panel app has failed to load.

There appears to be no support for a Corsair Flash Voyager 8GB USB Key.

Even though the system shows being up to date brasero is still shown in update manager, but it is greyed out.

Any idea how to sort this ??

Thanks :)

---

### Post by Thura on 2009-04-10
To change login screen, run "sudo gdmsetup".

> Braseo is still shown in update manager.
I think it is a bug. It does also for me. There is an update for Braseo, but it is not updating automatically, despite showing in update manager. It can be solved by opening synaptic, find braseo and manually updating.

For popups, play with notification-properties .... To see dark popups, make sure you got "notify-osd", ( install from synaptic ), or uninstall, if you don't want.

---

### Post by Tom_T on 2009-04-10
Thanks

When I rebooted again I ended up at a command prompt.. so I had a play !!

staring with xinit I got a new terminal window, I then ran gnome-session and go a working desktop.

From a new terminal I reconfigured gdm and now it seems to be working.  Not sure what went wrong, but since the upgrade I have a kdm entry in services. I've made sure that is disabled.

Where do I find notification-preferences ??

Thanks :)

---

### Post by Thura on 2009-04-10
Umm, Run ( Alt + F2 ) >> notification-properties ... 
Yep, that's it.

---


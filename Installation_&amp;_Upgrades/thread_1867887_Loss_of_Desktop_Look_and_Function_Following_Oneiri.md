---
title: "Loss of Desktop Look and Function Following Oneiric Upgrade"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by jackn on 2011-10-23
Following an Oneiric upgrade, I found the system to be aesthetically pleasing and to work very well.

Then, something happened, and the desktop appearance and functionality changed.
The following issues came up:
[LIST]
[*]The top panel is not the lovely default black anymore, but some ill-defined gray (see thumbnail).
[*]There's no keyboard layout indicator, nor can I switch between layouts with the bound keyboard shortcut (though I can from terminal running setxkbmap). This, although the keyboard layout part of 'system settings' lists four different layouts which used to work perfectly.
[/LIST]

In a guest session, I can both get the right appearance (black top) and different keyboard layouts to work. 
This shows that the software is there and works properly, but that something happened to my user session.

In addition, online radios which I could consistently listen to now display their players, but without sound. Other radios work fine.
Contrary to the above issues, the radio issue, perhaps unrelated, still persists in a guest session.

Following suggestions in the forums, I've installed Gnome-tweak-tool, but this doesn't seem relevant.
I've also reinstalled unity, which did help - as the thumbnail shows, I now have a sound indicator in the top panel, an indicator which disappeared at the same time as the other changes have taken place.

I'm thinking of reinstalling, a desperate solution, as these issues are quite important.

Help?
jackn

---

### Post by kherring7383 on 2011-10-24
There's a bug with the Unity Compiz Plugin. I too had a similar problem and was able to reset the plugin.

Check out these links:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html%20http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html")

[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)


Or try these commands from terminal:

To reset the Unity launcher icons:
 unity --reset-icons

To reset Unity:
unity --reset

To reset Compiz:
gconftool-2 --recursive-unset /apps/compiz-1

unity --reset

Hope this helps

---

### Post by jackn on 2011-10-25
Thank you so much, Kherring, for this helping hand.

I tried the commands.


Following
```
gconftool-2 --recursive-unset /apps/compiz-1
```
the terminal seemed to have no trouble, silently returning to the prompt.


When I ran
```
unity --reset
```, however, the screen froze. 
The terminal was complaining about not getting the expected responses from compiz. I don't understand those. Nor could I copy and paste the messages, as the screen was frozen.

Is it possible to reinstall both unity and compiz? Should I?

Thank you again,
jackn

---


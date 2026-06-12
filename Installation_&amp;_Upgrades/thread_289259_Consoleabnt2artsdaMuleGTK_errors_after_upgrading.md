---
title: "Console/abnt2/artsd/aMule/GTK errors after upgrading"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by Zólhos on 2006-10-30
Hi guys.

I've installed 6.10 in 3 different machines.

One was an upgrade from Ubuntu 6.06 to 6.10
One was an upgrade from Kubuntu 6.06 to 6.10
One was a completely new installation of an Ubuntu 6.10 using the Alternate CD.

All of them (including the new installation!) got the same error:
The console is screwed up. I use "Brazilian Portuguese pt_br ABNT2" keybard, and my console USED to work correctly, now it doesn't.  Some keys like "/" just doesn't work. Other keys like "ç" work, but for example, when it is asking for my login name (and only on that, not after logging in), if i type for example "ááá", and press backspace, backspace just won't work... Sometimes it works with other characters...
Very very odd...
Also, the console FONT changed. This version has "ZEROS" with a little point in the middle, the others had a slash inside the zero... (this is not exactly a bug, but may be a symptom of the bug).
Running "sudo dpkg-reconfigure console-setup" didn't seem to work. Even when rebooting.
Since I still got an 6.06 installation on another computer (yes, lotsa computers...), how can I compare both old and actual console configurations to try to fix them up? Which file? I think this is a very annoying bug for brazilian-portuguese-abnt2 users...

Another problem: some fonts (like the fonts on "aMsn") looks like "unaliased".
Another problem: aMsn is sometimes crashing, but I didn't investigate more...

Another: aMule also crashes. Open aMule, open 3 tabs of searches, try to close them... It always crashes for me. I've serached on the Internet, and other people seem to get this bug too. Looks like the new amsn is kinda unstable...
This is the message:
"(amule:6686): Gtk-CRITICAL **: gtk_container_remove: assertion `GTK_IS_TOOLBAR (container) || widget->parent == GTK_WIDGET (container)' failed

(amule:6686): Gtk-CRITICAL **: gtk_container_remove: assertion `GTK_IS_TOOLBAR (container) || widget->parent == GTK_WIDGET (container)' failed

(amule:6686): Gtk-CRITICAL **: gtk_container_remove: assertion `GTK_IS_TOOLBAR (container) || widget->parent == GTK_WIDGET (container)' failed

Gtk-ERROR **: file gtkcontainer.c: line 2447 (gtk_container_propagate_expose): assertion failed: (child->parent == GTK_WIDGET (container))"

Another: firefox2 seems to be slow................................

Another, and not least important (just on Kubuntu): VERY SERIOUS: artsd uses 98% of cpu (ALL THE ****ing TIME!!!), and gives me odd messages every 2 or 3 minutes... Obviously, sound doesn't works... I forgot what was written, when I get that machine again I will check it out.

Another: on Kubuntu, xserver-xorg package wasn't installed anymore after the upgrade.............

Guys, help me please =X
Is any of these a known bug with a known solution that I can fix up?

Thanks a lot!
Zólhos

---

### Post by Zólhos on 2006-11-01
Bump...........

No clue?

---

### Post by chinaski on 2006-12-17
same problem with aMule here, made several searches in the forum, found no solution yet :(

---


---
title: "removing compiz"
date: 2012-10-26
forum: Installation &amp; Upgrades
---

### Post by alpage2 on 2012-10-26
After a clean install of ubuntu 12.10, compiz seems to be enabled by default, but my old tower PC has insufficient resources, resulting in very slow graphic effects.

If I simply uninstall compiz, will it leave me with the normal gnome desktop?

I just want to be sure that I don't end up with no window manager!

Thanks in anticipation.
Alan

---

### Post by deadflowr on 2012-10-26
If you've installed the gnome-shell, or gnome classic desktop, then removing compiz should have little to no effect, however if your running unity, which sounds unlikely, then removing compiz will bork up the system as unity is a plugin shell/shell plugin for compiz.
Gnome-shell uses mutter, a portmanteau of metacity and clutter.
I can't remember what classic uses, so there's a chance of bad effect.

You can also install the new gnome remix:

[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10")

And avoid unity altogether(hopefully, if you choose).

---

### Post by alpage2 on 2012-10-26
Thanks deadflowr

Yes, I have unity, so I'll install the gnome remix first, before I uninstall compiz - many thanks for the tip.

Alan

---

### Post by alpage2 on 2012-10-28
Problem solved!

After following the upgrade instructions, and then rebooting, I chose the Gnome Classic (no effects) session, and my machine is back to lightning fast :)

Whilst fade effects on windows and menus are nice if they are fast enough, mine were glacially slow (yawn)!!

Thanks again to Deadflowr for the advice :KS

Regards
Alan

---


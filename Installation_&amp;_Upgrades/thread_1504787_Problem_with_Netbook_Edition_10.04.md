---
title: "Problem with Netbook Edition 10.04"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by failedpublisher on 2010-06-08
Hi there

I just upgraded from Netbook Remix 9.10 to Lucid Lynx 10.04.  I used to use the non-Netbook version of the Remix, where it was a simplified Gnome desktop which maximised the windows for me.  Wasn't a fan at all of the new "netbook launcher".  So I tried to disable it by typing:

sudo apt-get remove netbook-launcher

However, this now means Ubuntu launches but I am unable to now access any programs.  I get the top bar with networking and mail and volume and all that, but nothing else.  Right clicking on these panels does nothing.  

Through Grub I booted using the recovery mode into root, and typed

sudo apt-get install netbook-launcher

But this does not seem to have had any effect.  I get the error "The panel encountered a problem while loading OADIID:GNOME_GoHome"

Any help much appreciated as I have all my file on this computer and it looks like I have lost them.

Ray

---

### Post by darkod on 2010-06-08
What is the "non-netbook version of the Remix"? The Netbook Remix is the netbook version. Unless there are some customized versions floating around but in that case you shouldn't just upgrade to the next version without investigating.

If using the ubuntu released versions, you either use the Desktop or Netbook Remix (for 10.04 called Netbook Edition).

The netbook-launcher is the outlook of the netbook version. You can't expect much if you remove it. Why not just use the Desktop version then?

You could try to add:

sudo apt-get install ubuntu-desktop

That's the standard layout of the Desktop version, but I'm not sure how it would work right now. Maybe wait for second opinion.

PS. As for your files, all of them should be there. You should always be able to access them from live mode.

---

### Post by kerry_s on 2010-06-08
log out, select gnome in the session menu & log in.
unlock the window picker applet so you can slide it over to get to the panel, right click the panel & add 1 of the menus.

---

### Post by failedpublisher on 2010-06-11
Thank you both for these responses.

The alternative Netbook edition of 9.10 I was talking about was the ability to switch off the netbook launcher and use a restricted Gnome environment.  This was still the Netbook Edition, but looked more like the normal Ubuntu window environment.

I managed to logout and then login again using the Gnome desktop and set his as default.  Now I can use my computer again without the annoying Netbook Launcher and have access to my files once again.  Thanks so much for this help.

---


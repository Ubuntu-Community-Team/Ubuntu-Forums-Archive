---
title: "autostart not working in KDE + kubuntu8.10 (Gnome &amp; KDE dual login)"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mailkarthi on 2008-10-13
Hi,

I am using Kubuntu 8.10 b2. Originally my system had Gnome and later I installed KDE4.1 as well.

My problem is, when I boot in KDE, both Gnome and KDE network manager loads. Killing GNome manger makes KDE network manager to disconnect and it would never connect unless Gnome network manager is started.

Also changes I make to startup list is not considered on next boot. Meaning I disabled Empathy from startup and added Kopette is enabled. But always Empathy loads and Kopette is not loading on startup.

I had KDE4.1 and Gnome both in 8.04 and this was never the issue. All this started after I upgraded to 8.10. Any resolution or is it a know bug?

---

### Post by adam on 2008-10-15
I'm having the same problem with autostart. KDE has an "Autostart only in KDE" option, and Gnome doesn't seem to. Every time I login, gnome-keyring-manager starts. If I click "deny", knetwork-manager won't connect to a network. I can, however, put in the password, connect to a network and then kill "nm-applet" manually without losing connectivity.

Gnome-power-manager seems to also turn on randomly in KDE.

I don't have gnome-power-manager, gnome-keyring-d, or nm-applet in KDE's autostart, and there's no entry for any of them in ~/.config/autostart at all.

---


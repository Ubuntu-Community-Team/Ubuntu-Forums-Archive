---
title: "Gnome Software says that updates cannot be installed"
date: 2021-05-27
forum: Installation &amp; Upgrades
---

### Post by Paddy Landau on 2021-05-27
Every so often, gnome-software gives the error, "Unable to download updates: you do not have permission to install software".
[ATTACH=CONFIG]288569[/ATTACH]
Usually, this goes away when I reboot.

Today, it is persistent. I have looked for solutions. What I found were:

[LIST]
[*]Run gnome-software from sudo
[*]Clear apt's cache
[*]Run apt autoremove
[*]Run all updates
[*]Uninstall and reinstall gnome-software
[*]Reboot
[*]Delete ~/.local/share/gnome-software/ (but this folder doesn't exist)
[/LIST]
I've done all of these, and the error remains.

What can I do to fix this?

---

### Post by Paddy Landau on 2021-05-27
Now. out of the blue, it's working again.

I don't know&#8230; Pretty weird!

---

### Post by Paddy Landau on 2021-06-17
&#8230; And it's back again, both yesterday and today.

Still pretty weird!

---


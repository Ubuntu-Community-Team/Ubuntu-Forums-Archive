---
title: "Nautilus doesn't start after upgrade"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by cbrick77 on 2011-10-16
Short version:
After upgrading from 11.04 to 11.10, my desktop isn't drawn and nautilus won't open. After tweaking some things I have been stalled at the error output of 
```
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
Initializing nautilus-gdu extension
nautilus: symbol lookup error: nautilus: undefined symbol: ubuntu_menu_proxy_get
``` I have a patch from [[COLOR="Blue"]here[/COLOR]]("http://http://patches.ubuntu.com/by-release/ubuntu/n/nautilus/nautilus_1:3.2.0-0ubuntu5.patch") but I don't know if it will fix my problem (mostly because I don't know how to apply a patch). Gedit also throws the "Gtk-Message: Failed to load module "canberra-gtk-module"" error but will still start. I have filed a bug report [[COLOR="Blue"]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/874582")

Long Version:
So after upgrading from 11.04 to 11.10 I noticed that my desktop wasn't being drawn so I tried checking nautilus. Clicking on the home folder icon in the dock didn't do anything so I tried launching it from the terminal. It originally gave me this output:
```
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
Initializing nautilus-open-terminal extension
Initializing nautilus-gdu extension
nautilus: symbol lookup error: nautilus: undefined symbol: gtk_overlay_new
```

I tried various remedies found while searching around. I have tried removing nautilus-open-terminal while leaving ubuntuone-client-gnome, vice versa, both, and neither. None had fixed it.

I filed a bug report [[COLOR="Blue"]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/874582").

Under the Gnome shell version of Ubuntu I ran
```
gconftool-2 --type bool --set '/apps/ubuntuone/nautilus/show-location' false
```
per a post I saw. It got nautilus running, but the desktop wasn't drawn. Under the 2D version of Ubuntu Nautilus wouldn't run after that code and the desktop still wasn't drawn.

I read that it was because of not having GTK+ 3.2.0 so I installed that. It did not get nautilus running but it did give a new error:
```
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
Initializing nautilus-gdu extension
nautilus: symbol lookup error: nautilus: undefined symbol: ubuntu_menu_proxy_get

```

Having searched for anything about "ubuntu_menu_proxy_get" I found a patch from [COLOR="Blue"][http://patches.ubuntu.com/by-release/ubuntu/n/nautilus/](http://patches.ubuntu.com/by-release/ubuntu/n/nautilus/)[/COLOR] , specifically [[COLOR="Blue"]this one[/COLOR]]("http://patches.ubuntu.com/by-release/ubuntu/n/nautilus/nautilus_1:3.2.0-0ubuntu5.patch"). I have no idea if it works as I have no clue how to apply a patch (and searching for a tutorial yielded few results).

I have time and time again uninstalled nautilus and reinstalled, but that hasn't helped at all. Running it as sudo does nothing.

It's not a big problem in terms of running the OS as a whole, but it is annoying. Does anyone have any suggestions at all because I've not found anyone with the same problem and would like this resolved.

Thanks in advance!

---

### Post by cbrick77 on 2011-10-22
As per the [bug report]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/874582"), it turns out the problem, at least for me, was libgtk-3.so.0 which was taking over the ubuntu library. Deleting it solved the problem.

More info is in the comments on the bug report.

---

### Post by gdata on 2013-01-06
try this 
sudo apt-get install libcanberra-gtk3-module

---

### Post by overdrank on 2013-01-06
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---


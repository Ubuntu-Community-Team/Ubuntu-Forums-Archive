---
title: "djvulibre plugin failure with Feisty"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by gc1 on 2007-07-04
The plugin has been installed with Synaptic, as well as the djview package. However I can't get djvu files to download from findmypast.com though I did get them with older systems. Maybe there's a problem with Synaptic not putting in a symbolic link? In my home folder there is a folder /mozilla/plugins which does not have the nsdejavu.so file....should it be there?

I tried putting it in by drag and drop from /usr/lib/mozilla-firefox/plugins but I'm told I don't have permission for that. Using sudo to launch Nautilus I can drag and drop the file but the icon shows up with a locked symbol. That won't work. Is the link needed to make the plugin work and if so how do I get it using drag and drop?

---

### Post by Tux Aubrey on 2007-09-21
Its been months since this was posted without a single reply.

I am having the same problem with djvlibre in the feisty repos - as well as for gutsy.  

Does anyone have this plugin working on Firefox in Ubuntu?

---

### Post by gc1 on 2007-09-24
I wonder if there's a problem of having a djvu capability in evince, a multi-capable viewer which came by default with Feisty.
In my system long ago I remember having to clear out an old djvu install before getting a new one to work. Maybe the djvu bit of evince is creating a problem with djvu as a plugin to Firefox?

Graham

---

### Post by Tux Aubrey on 2007-09-26
Thanks for your reply - I'll try uninstalling evince and doing djvu again from scratch (interestingly, I did manage to get the plug-in working on a virtual machine install of Elive, which does not come packaged with Evince).

---


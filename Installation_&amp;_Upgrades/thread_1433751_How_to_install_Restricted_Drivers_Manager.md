---
title: "How to install Restricted Drivers Manager?"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by Flaredancer on 2010-03-19
[noob]
Okay. So I've just recently installed my first Linux OS, Ubuntu Studio. I don't have the wireless card driver and I can't get it with the regular Driver Manager, so a friend recommended I get the restricted drivers manager.

He said the command to get that went like this:

sudo apt-get install jockey-gtk

But when I did that it just said I already had that. So, me beilng weird, I switched jockey-gtk to restricted-manager and got this output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package restricted-manager is a virtual package provided by:
  jockey-gtk 0.3.3-0ubuntu8.2
You should explicitly select one to install.
E: Package restricted-manager has no installation candidate


What do I do to get the manager? 

(It isn't in the 'Add/Remove' section either.)

Thanks for any help!
-Flaredancer

EDIT:

[/noob]

---

### Post by nothingspecial on 2010-03-19
I`m not tottaly sure with ubuntu studio but you should already have it.

What happens if you type ```
sudo jockey-gtk
```

---

### Post by Flaredancer on 2010-03-19
> **nothingspecial said:**
> I`m not tottaly sure with ubuntu studio but you should already have it.

What happens if you type ```
sudo jockey-gtk
```

The Hardware Drivers application opens. But there are no drivers available here.

"No proprietary drivers are in use on this system."

---

### Post by nothingspecial on 2010-03-19
In that case you need to start a new thread about your wireless problem.

Go to the absolute beginners forum and ask there.

In your post paste the output of

```
sudo lshw -C network
```

so people can see what wireless card you have.

---


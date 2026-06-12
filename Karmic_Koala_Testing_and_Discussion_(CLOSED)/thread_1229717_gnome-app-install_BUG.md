---
title: "gnome-app-install BUG"
date: 2009-08-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by miegiel on 2009-08-02
I've got a bug in gnome-app-install that prevents me from using *Add/Remove* from the *Applications* menu. A few days back it changed the filter to *show only installed programs* and since then I can't use it any more.

see : [https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/389749](https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/389749)

For now I'd be happy if I could somehow change the filter by editing whatever file it is that is "remembering" the filter. I tried searching and even browsing for the file in my home (assuming it should be there somewhere), but to no avail.

I'd be really happy if someone could point met in the right direction or even just provide inspiration on how to dig further. It's not that I can't install anything, there is always apt-get, but *Add/Remove* is great if I need to find some software I don't know the (exact) name of.

---

### Post by pastalavista on 2009-08-02
Try using Synaptic Package Manager in the System > Administration menu.

---

### Post by miegiel on 2009-08-02
> **pastalavista said:**
> Try using Synaptic Package Manager in the System > Administration menu.

Thanks, never noticed synaptic also sorted apps by category :oops:

---

### Post by wayne_cat on 2009-08-02
> **miegiel said:**
> I've got a bug in gnome-app-install that prevents me from using *Add/Remove* from the *Applications* menu. A few days back it changed the filter to *show only installed programs* and since then I can't use it any more.

see : [https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/389749](https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/389749)

For now I'd be happy if I could somehow change the filter by editing whatever file it is that is "remembering" the filter. I tried searching and even browsing for the file in my home (assuming it should be there somewhere), but to no avail.

I'd be really happy if someone could point met in the right direction or even just provide inspiration on how to dig further. It's not that I can't install anything, there is always apt-get, but *Add/Remove* is great if I need to find some software I don't know the (exact) name of.

you can "reset" the filter with gconf-editor ... change the key "filter_applications" in

apps->gnome-app-install

---

### Post by miegiel on 2009-08-02
Thanks Wayne \\:D/

---

### Post by omegavirus on 2009-08-11
> **wayne_cat said:**
> you can "reset" the filter with gconf-editor ... change the key "filter_applications" in

apps->gnome-app-install

Thanks for the solution!

---

### Post by phenest on 2009-08-11
Isn't it true that gnome-app-install is being redesigned to replace all the package managers starting with Add/Remove. Could this be intentional?

---

### Post by miegiel on 2009-08-11
> **phenest said:**
> Isn't it true that gnome-app-install is being redesigned to replace all the package managers starting with Add/Remove. Could this be intentional?

That sounds odd to me, why would it intentionally crash on only one filter setting? Personally I think it's a typo in line 242-243 of */usr/lib/python2.6/dist-packages/AppInstall/Menu.py* or so. Not that I understand the code much :twisted: The code just looks a bit strange to me.

also see : [https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/389749](https://bugs.launchpad.net/ubuntu/+source/gnome-app-install/+bug/389749)

---

### Post by phenest on 2009-08-11
> **miegiel said:**
> That sounds odd to me, why would it intentionally crash on only one filter setting?

It was a suggestion, as it is something under development.

---

### Post by miegiel on 2009-08-11
> **phenest said:**
> It was a suggestion, as it is something under development.

maybe your right #-o now it's crashing on me regardless of the filter setting

---

### Post by ktp on 2009-08-11
> **phenest said:**
> Isn't it true that gnome-app-install is being redesigned to replace all the package managers starting with Add/Remove. Could this be intentional?

That is the long term vision right now.

---


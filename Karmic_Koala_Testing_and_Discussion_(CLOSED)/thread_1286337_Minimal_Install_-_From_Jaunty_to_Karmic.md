---
title: "Minimal Install - From Jaunty to Karmic"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by moiecoute on 2009-10-08
Hi all,

I use the minimal install of Jaunty and am wondering about upgrading to Karmic whether the upgrade can be done through the update manager.

Also will the upgrade just upgrade the existing components or install all the things I have tried to avoid by using the minimal install, e.g., Evolution, Brasero etc.

Thanks

---

### Post by sandyd on 2009-10-08
> **moiecoute said:**
> Hi all,

I use the minimal install of Jaunty and am wondering about upgrading to Karmic whether the upgrade can be done through the update manager.

Also will the upgrade just upgrade the existing components or install all the things I have tried to avoid by using the minimal install, e.g., Evolution, Brasero etc.

Thanks
see
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

the second question is a bit questionable. this is because the new versions of the software may depend on different packages. if needed, it will pull them in.

---

### Post by cariboo on 2009-10-08
I really depends on what you have installed. If you are using the gnome-desktop, you may not get evolution. If you have the ubuntu-desktop it will probably update evolution as well of the rest of the Ubuntu-desktop depends.

---

### Post by moiecoute on 2009-10-09
> **cariboo907 said:**
> I really depends on what you have installed. If you are using the gnome-desktop, you may not get evolution. If you have the ubuntu-desktop it will probably update evolution as well of the rest of the Ubuntu-desktop depends.

Thanks Carlee and Cariboo907.

I think it was gnome-core or gnome-minimal. Definitely was not gnome-desktop or ubuntu-desktop.

---

### Post by Paqman on 2009-10-09
> **moiecoute said:**
> Thanks Carlee and Cariboo907.

I think it was gnome-core or gnome-minimal. Definitely was not gnome-desktop or ubuntu-desktop.

You should be fine, but if you want to check you can check to see what packages the Karmic version of gnome-core has:

[Karmic gnome-core]("http://packages.ubuntu.com/karmic/gnome-core")

Put simply, unless you have ubuntu-desktop installed, you won't get upgraded to karmic ubuntu-desktop. All the update does is replace all your existing Jaunty packages with their Karmic equivalents.

---

### Post by moiecoute on 2009-10-11
> **Paqman said:**
> You should be fine, but if you want to check you can check to see what packages the Karmic version of gnome-core has:

[Karmic gnome-core]("http://packages.ubuntu.com/karmic/gnome-core")

Put simply, unless you have ubuntu-desktop installed, you won't get upgraded to karmic ubuntu-desktop. All the update does is replace all your existing Jaunty packages with their Karmic equivalents.

Thanks Paqman.

---


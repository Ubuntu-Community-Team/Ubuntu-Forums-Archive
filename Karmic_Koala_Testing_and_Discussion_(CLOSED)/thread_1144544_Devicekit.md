---
title: "Devicekit"
date: 2009-04-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Slug71 on 2009-04-30
Just wanted to start a thread with another .kit name.

Nah really, i wonder if Devicekit will be installed by default in Karmic?

---

### Post by crjackson on 2009-04-30
> **Slug71 said:**
> Just wanted to start a thread with another .kit name.

Nah really, i wonder if Devicekit will be installed by default in Karmic?

What is it exactly?

---

### Post by Slug71 on 2009-04-30
> **crjackson said:**
> What is it exactly?

Its a new modular Hardware Abstraction Layer which is replacing HAL.

---

### Post by crjackson on 2009-04-30
> **Slug71 said:**
> Its a new modular Hardware Abstraction Layer which is replacing HAL.

What are the advantages?

---

### Post by Slug71 on 2009-04-30
A c/p:

> devicekit is a simple system service that a) can enumerate devices; b) emits signals when devices are added removed; c) provides a way to merge device information / quirks onto devices. It is designed to partially replace hal and overcome some of the design limitiations of hal. Devicekit functionality is provided in the form of dbus services on the system bus.

Apart from devicekit itself, there is devicekit-disks, which is a system service to keep track of block devices. The functionality offered by devicekit-disks is a superset of what hal provides for block devices.

There is also devicekit-power, which takes over the power-management-related parts of hal and the more complex functionality of gnome-power-manager. As a consequence, gnome-power-manager itself becomes much simpler.

The new udev-extra module will provide udev rules that are needed to make the devicekit architecture work. Functionality that was provided via .fdi files in hal will eventually be moved to udev rules, and setting acls on devices will also be done here at some point.

Devicekit-disks comes with a graphical frontend called palimpsest (the package name is gnome-disk-utility). Furthermore, there's a nautilus extension to format disks (nautilus-gdu), accessible from context menu. 

---

### Post by crjackson on 2009-04-30
Wow, that does sound cool. I'll be surprised if it's ready by the time Karmic is released though.

---

### Post by Slug71 on 2009-04-30
> **crjackson said:**
> Wow, that does sound cool. I'll be surprised if it's ready by the time Karmic is released though.

It's in F-11.

---

### Post by crjackson on 2009-04-30
> **Slug71 said:**
> It's in F-11.

:oops:

---

### Post by ghindo on 2009-04-30
I was pretty sure that DeviceKit development had ceased in favor of something else, but I can't find the link right now.  I'll keep looking around.

**EDIT:**  Yup:

[http://lists.freedesktop.org/archives/devkit-devel/2009-March/000123.html](http://lists.freedesktop.org/archives/devkit-devel/2009-March/000123.html)> This is probably the last release of DeviceKit. The functionality of DeviceKit is going to be merged into the udev-extras with the only changes being the D-Bus name as well as the prefix for the GObject library and the command line tool.

---

### Post by amano on 2009-05-01
good catch, I didn't know that yet.

---

### Post by gnomeuser on 2009-05-01
> **ghindo said:**
> I was pretty sure that DeviceKit development had ceased in favor of something else, but I can't find the link right now.  I'll keep looking around.

**EDIT:**  Yup:

[http://lists.freedesktop.org/archives/devkit-devel/2009-March/000123.html](http://lists.freedesktop.org/archives/devkit-devel/2009-March/000123.html)

Not so much ceased as been moved to be named udev-extras. DeviceKit was always amongst other things about removing the duplication with udev that HAL had. It is a better fit this way, but the large DeviceKit project remains. That is why you will see things like Devicekit-disks and Devicekit-power. It is just the main DeviceKit source that has been.. renamed.

Devicekit should be in jaunty, I believe that gnome-power-manager e.g. uses it. If not then I just saw new git snapshots in the pipeline on karmic-changes so you will definitely enjoy it then.

---

### Post by 3rdalbum on 2009-05-01
I think they should rename Pulseaudio to "Soundkit" - maybe it would become more popular.

---

### Post by Slug71 on 2009-05-01
> **gnomeuser said:**
> Not so much ceased as been moved to be named udev-extras. DeviceKit was always amongst other things about removing the duplication with udev that HAL had. It is a better fit this way, but the large DeviceKit project remains. That is why you will see things like Devicekit-disks and Devicekit-power. It is just the main DeviceKit source that has been.. renamed.

Devicekit should be in jaunty, I believe that gnome-power-manager e.g. uses it. If not then I just saw new git snapshots in the pipeline on karmic-changes so you will definitely enjoy it then.

No it wasnt installed by default with Jaunty.

---

### Post by Slug71 on 2009-05-01
> **ghindo said:**
> I was pretty sure that DeviceKit development had ceased in favor of something else, but I can't find the link right now.  I'll keep looking around.

**EDIT:**  Yup:

[http://lists.freedesktop.org/archives/devkit-devel/2009-March/000123.html](http://lists.freedesktop.org/archives/devkit-devel/2009-March/000123.html)

Thanks i didnt know that.

As gnomeuser pointed out though, its just a rename.

---

### Post by chrisccoulson on 2009-05-02
This will definately be in Karmic by default, as gnome-power-manager 2.26.1 which depends on DK-disks has already been uploaded (just not built just yet)

Also, please see this on the Gnome desktop-devel-list today: [new dependencies in gvfs]("http://mail.gnome.org/archives/desktop-devel-list/2009-May/msg00004.html")

---

### Post by Slug71 on 2009-05-02
Thanks for the info Chris.

---

### Post by Jay_Bee on 2009-05-03
So **that**'s what's been screaming "Your hard disk is failing" at me in F11 :)
Um... oh no :(

---

### Post by gnomeuser on 2009-05-04
A little bit more information about DeviceKit and how it fits into the ecosystem now that it's place in the universe has changed a bit:

[http://lists.freedesktop.org/archives/devkit-devel/2009-April/000140.html](http://lists.freedesktop.org/archives/devkit-devel/2009-April/000140.html)

Additionally davidz recently blogged about some of the effects we are seeing already due to DeviceKit-disks:

[http://blog.fubar.dk/?p=105](http://blog.fubar.dk/?p=105)

---

### Post by Gina on 2009-05-04
Should be good :) :)

---


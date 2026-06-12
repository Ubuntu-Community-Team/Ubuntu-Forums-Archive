---
title: "Unable to install gnome-shell?"
date: 2009-12-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rubenverweij on 2009-12-14
Some broken packages it seems... I got this output:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-shell: Depends: gobject-introspection-glib-2.0 but it is not installable
               Depends: gobject-introspection-freedesktop but it is not installable
               Depends: gobject-introspection-repository but it is not installable
E: Broken packages

```
Any ideas or should I file a bug?

---

### Post by LKjell on 2009-12-14
Try another mirror.

---

### Post by SevenMachines on 2009-12-14
gobject-introspection-* packages are being renamed as gir1.0-* packages. gnome-shell hasn't been updated to reflect these changes yet. it'll be uninstallable until it is i'm afraid

---

### Post by lidex on 2009-12-14
Have you enabled the Universe Repository?
Packages available here:
[http://packages.ubuntu.com/karmic/gnome-shell]("http://packages.ubuntu.com/karmic/gnome-shell")

---

### Post by jpeddicord on 2009-12-14
> **SevenMachines said:**
> gobject-introspection-* packages are being renamed as gir1.0-* packages. gnome-shell hasn't been updated to reflect these changes yet. it'll be uninstallable until it is i'm afraid

Echo that. Haven't been able to install it for weeks. You can still grab the source and build from live.gnome.org, but that requires a significant amount of patience.

---

### Post by Merk42 on 2009-12-14
> **jpeddicord said:**
> Echo that. Haven't been able to install it for weeks. You can still grab the source and build from live.gnome.org, but that requires a significant amount of patience.

It's not that bad, you just kinda wait a while as it builds, you can do other stuff in the meantime.

At any rate, I've made note in the [GNOME Shell](http://ubuntuforums.org/showthread.php?t=1305154) thread, and would like to be updated again when it is fixed

---

### Post by SevenMachines on 2009-12-14
it looks like it was last built when gobject-introspection generated dependencies on gobject-introspection-* packages. nowadays gobject-introspection would generate the right dependencies on gir1.0.
but theres a gir1.0-mutter dependency in the build-dep which isnt satisfiable so lucid source will fail to build until thats resolved

---

### Post by Merk42 on 2009-12-14
> **SevenMachines said:**
> it looks like it was last built when gobject-introspection generated dependencies on gobject-introspection-* packages. nowadays gobject-introspection would generate the right dependencies on gir1.0.
but theres a gir1.0-mutter dependency in the build-dep which isnt satisfiable so lucid source will fail to build until thats resolved

So building from source is also impossible in Lucid?

---

### Post by rubenverweij on 2009-12-14
Thanks for your suggestions, I will try to build it from source. (if that's possible)

---

### Post by SevenMachines on 2009-12-14
> **Merk42 said:**
> So building from source is also impossible in Lucid?
i was talking about the packaging source in lucid, not the actual source code

---

### Post by Merk42 on 2009-12-14
> **SevenMachines said:**
> i was talking about the packaging source in lucid, not the actual source code

Okay that's what I thought.

---

### Post by lidex on 2009-12-14
So you're saying the packages you're missing are:
> The following packages have unmet dependencies:
  gnome-shell: Depends: gobject-introspection-glib-2.0 but it is not installable
               Depends: gobject-introspection-freedesktop but it is not installable
               Depends: gobject-introspection-repository but it is not installable
E: Broken packages

Why not download and install them from here?
[http://packages.ubuntu.com/karmic/gnome-shell]("http://packages.ubuntu.com/karmic/gnome-shell")

---

### Post by jpeddicord on 2009-12-14
> **lidex said:**
> So you're saying the packages you're missing are:


Why not download and install them from here?
[http://packages.ubuntu.com/karmic/gnome-shell]("http://packages.ubuntu.com/karmic/gnome-shell")

Because this is Lucid, not Karmic, and installing those will create conflicts with the gir1.0-* packages.

---

### Post by SevenMachines on 2009-12-14
> **lidex said:**
> So you're saying the packages you're missing are:

Why not download and install them from here?
[http://packages.ubuntu.com/karmic/gnome-shell](http://packages.ubuntu.com/karmic/gnome-shell)

i would imagine its the gir1.0-mutter-2.28 thats the holdup. its not available. the gobject-introspection-* packages are moved across to gir1.0 packages, installing the old ones would undoubtedly cause a conflict mess.
gnome-shell wants a newer (debian) version of mutter than the current lucid one too, 2.28.0-2 as compared to the 2.28.0-0ubuntu1 that we currently have.
in short, lucid needs a newer sync of mutter from debian testing, currently 2.28~git20091024-1.

---

### Post by lidex on 2009-12-14
> Because this is Lucid, not Karmic

Color me embarrassed :redface: 
Came over from an RSS link and didn't see which forum I was in. Must....run....away...

---


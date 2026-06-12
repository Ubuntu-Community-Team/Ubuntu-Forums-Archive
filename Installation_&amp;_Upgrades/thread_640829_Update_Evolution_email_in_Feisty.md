---
title: "Update Evolution email in Feisty"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by stchman on 2007-12-14
Hello all.

I have been running Feisty for some time very happily.  I would like to update Evolution.  The Evolution that comes with Feisty is 2.10.1.  Gutsy has a much later version 2.12.0.  

Is there a way I can use the Gutsy repos to install the latest Evolution?  If no and you build Evolution from source how do you work out the dependencies?

Thanks.

---

### Post by stchman on 2007-12-15
I downloaded the source for Evolution and ran ./configure

I had to install the package bison, but here is the output:

```
checking for GNOME_PLATFORM... configure: error: Package requirements (gtk+-2.0 >= 2.10.0
         gconf-2.0 >= 2.0.0
         gnome-vfs-2.0 >= 2.4.0
         libbonoboui-2.0 >= 2.4.2
         libglade-2.0 >= 2.0.0
         libgnomecanvas-2.0 >= 2.0.0
         libgnomeui-2.0 >= 2.0.0
         libxml-2.0 >= 2.0.0) were not met:

No package 'gtk+-2.0' found
No package 'gconf-2.0' found
No package 'gnome-vfs-2.0' found
No package 'libbonoboui-2.0' found
No package 'libglade-2.0' found
No package 'libgnomecanvas-2.0' found
No package 'libgnomeui-2.0' found
No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_PLATFORM_CFLAGS
and GNOME_PLATFORM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

Some of these packages don't exist.  Let me know what you think.

Thanks.

---

### Post by Partyboi2 on 2007-12-15
> **stchman said:**
> I downloaded the source for Evolution and ran ./configure

I had to install the package bison, but here is the output:

```
checking for GNOME_PLATFORM... configure: error: Package requirements (gtk+-2.0 >= 2.10.0
         gconf-2.0 >= 2.0.0
         gnome-vfs-2.0 >= 2.4.0
         libbonoboui-2.0 >= 2.4.2
         libglade-2.0 >= 2.0.0
         libgnomecanvas-2.0 >= 2.0.0
         libgnomeui-2.0 >= 2.0.0
         libxml-2.0 >= 2.0.0) were not met:

No package 'gtk+-2.0' found
No package 'gconf-2.0' found
No package 'gnome-vfs-2.0' found
No package 'libbonoboui-2.0' found
No package 'libglade-2.0' found
No package 'libgnomecanvas-2.0' found
No package 'libgnomeui-2.0' found
No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_PLATFORM_CFLAGS
and GNOME_PLATFORM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```Some of these packages don't exist.  Let me know what you think.

Thanks.

You could try the following and see. You might want to double check them.
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

gtk+-2.0 = libgtk2.0-dev
gconf-2.0 = libgconf-dev
gnome-vfs-2.0 = libgnomevfs2-dev
libbonoboui-2.0 = libbonoboui2-dev
libglade-2.0 = libglade2-dev
libgnomecanvas-2.0 = libgnomecanvas2-dev
libgnomeui-2.0 = libgnomeui-dev
libxml-2.0 = libxml-dev

Personally I think its a headache trying to get it to install.
Hope you get it to work!
:)

---

### Post by stchman on 2007-12-15
> **Partyboi2 said:**
> You could try the following and see. You might want to double check them.
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

gtk+-2.0 = libgtk2.0-dev
gconf-2.0 = libgconf-dev
gnome-vfs-2.0 = libgnomevfs2-dev
libbonoboui-2.0 = libbonoboui2-dev
libglade-2.0 = libglade2-dev
libgnomecanvas-2.0 = libgnomecanvas2-dev
libgnomeui-2.0 = libgnomeui-dev
libxml-2.0 = libxml-dev

Personally I think its a headache trying to get it to install.
Hope you get it to work!
:)

Are all build from source this much of a PITA?  I am in dependency hell.  I have finally gotten down to a dependency I cannot satisfy.

```
checking for GTKHTML... configure: error: Package requirements (libgtkhtml-3.14 >= 3.16.0) were not met:

Requested 'libgtkhtml-3.14 >= 3.16.0' but version of libgtkhtml is 3.14.1

```

3.14.1 is the latest in Feisty.  Any suggestions?

---

### Post by hugmenot on 2007-12-15
Evolution is so seriously tied to the current version of Gnome that you can just as well upgrade to Gutsy. You already saw how many dependencies from Gutsy you have to pull in.

Here are two options: You enable the Gutsy repo only for a minute to specifically install Evolution. Of course all the needed Gnome dependecies from Gutsy are also pulled in, which means that you upgrade to a portion of Gutsy. Or, you enable the Gutsy source repo "deb-src", and then fetch the sources automatically by using pbuilder. It will fetch all deps, build them, and then fetch evolution and build it with the build-deps. 

Not worth the hassle. Just upgrade completely and you're done. Some software can be easily built from source but Evolution is too much integrated.

---

### Post by hugmenot on 2007-12-15
Also, what you're doing now will inevitably lead to a cluttered and messed up system. The automake script will litter files all over your system, and are not tracked by APT or anything. You will likely face unexplainable crap later on.

What you are trying is exactly what distros like Ubuntu or Debian are doing, but smarter, because they have all the packaging and dependecy architecture. Just trust them and use their stuff.

---

### Post by Partyboi2 on 2007-12-15
> Requested 'libgtkhtml-3.14 >= 3.16.0' but version of libgtkhtml is 3.14.1Have a look at [http://www.gnome.org/projects/evolution/download.shtml](http://www.gnome.org/projects/evolution/download.shtml)
for gtkHTML. You will need to compile it.
Like I said there will be headaches and there could be breakages.
Is it worth it?

---

### Post by stchman on 2007-12-15
Is this just an Evolution thing and most other apps don't require this level of dependencies?

Thanks.

---

### Post by foureight84 on 2007-12-20
you guys can just do sudo apt-get build-dep evolution. that takes care of most of the evolution dependencies. then install the evolution development package, compile the gtkhtml and that's about it.

---


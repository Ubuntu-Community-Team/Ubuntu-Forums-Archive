---
title: "Problem Installing C++ IDE (Code::Blocks)"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by yao_man on 2008-02-23
I'm not sure if this is the right place for this but I didn't know where else to put it.

I am trying to install Code::Blocks from source and I had succeeded until I tried typing in 

./configure --enable-contrib
make
make install

as it says in the build file.

I got the following output 

...
checking whether to build the foreign projects importer plugin... yes
checking whether to build the scripted wizard plugin... yes
checking whether to build the to-do plugin... yes
checking which (if any) contrib plugins to build... Unknown contrib plugin none, ignoring
none
checking if the compiler supports precompiled headers... yes
checking for wx-config... /usr/bin/wx-config
checking for wxWidgets version >= 2.8.0... yes (version 2.8.7)
checking for wxWidgets static library... no
checking for wxWidgets platform... wxGTK
checking for pkg-config... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK2... configure: error: Package requirements (gtk+-2.0 >= 2.0.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK2_CFLAGS
and GTK2_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

alex@alex-desktop:~/Desktop/temp/codeblocks-1.0svn4893$ make
make: *** No targets specified and no makefile found.  Stop.
alex@alex-desktop:~/Desktop/temp/codeblocks-1.0svn4893$ make install

I think I just need to update my gtk plugin, but don't know how or where to do so.

Any help would be appreciated.

---

### Post by toa on 2008-02-23
Try installing GTK completey through Synaptic rather than source.

[http://aycu40.webshots.com/image/45839/2004851116977042364_rs.jpg](http://aycu40.webshots.com/image/45839/2004851116977042364_rs.jpg)

---

### Post by yao_man on 2008-02-23
This may be stupid, but I don't know how to do that. I'm very new to Ubuntu and any Linux based system.

Also, that link you gave me didn't work. It said the image contained errors and could not be displayed.

If you don't mind, could you help me or walk me through installing code::blocks completely. I would very much appreciate any help at all.

---


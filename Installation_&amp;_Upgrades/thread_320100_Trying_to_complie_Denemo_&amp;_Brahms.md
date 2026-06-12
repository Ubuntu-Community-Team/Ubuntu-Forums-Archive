---
title: "Trying to complie Denemo &amp; Brahms"
date: 2006-12-16
forum: Installation &amp; Upgrades
---

### Post by Ginjeet on 2006-12-16
Hi, I'm trying to compile these music-sheet editor softwares, stucking at "./configure"
( on Kubuntu: )

Brahms:
```

./configure
...
checking for Qt... configure: error: Qt (>= Qt 3.0.2) (headers and libraries) not found. Please check your installation!

```

Denemo:
```

./configure
...
checking for DENEMO... configure: error: Package requirements (gtk+-2.0 >= 2.0.3) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DENEMO_CFLAGS
and DENEMO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Please help!

G.

---

### Post by patrick295767 on 2006-12-17
try to install 'gtk+-2.0'

apt-cache search gtk+-2.0
apt-cache search gtk+-

---

### Post by Ginjeet on 2006-12-17
> **patrick295767 said:**
> try to install 'gtk+-2.0'

apt-cache search gtk+-2.0
apt-cache search gtk+-

tried already, no go.
I do think I have gtk, qt installed btw. (because "apt-get install denemo" works)



but still, thanks.

Any other ideas??

---

### Post by Grehan on 2006-12-28
Hi Ginjeet,

The package that you most likely still missing is the one containing the development files.
In addition to 'libgtk2.0-0' you need 'libgtk2.0-dev'.
Type this in a terminal:

sudo apt get install libgtk2.0-dev

...and accept whatever dependancies it requires. When that is done run ./configure in your Denemo source folder again to check if any thing else is needed to compile it.

I am not sure about the Brahms dependancies though, but I know for a fact that Denemo recently got updated to 0.7.6. Today actually, according to GnomeFiles. :) 

I hope this information helps.

-Grehan

---


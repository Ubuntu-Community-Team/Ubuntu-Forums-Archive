---
title: "Find which bit of source prints message"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by stan3 on 2008-10-29
Trying to work out which bit of source this message comes from since upgrading to intrepid:

```

$ xvfb-run gnome-terminal -x date
Xlib:  extension "RANDR" missing on display ":99.0".
$

```

Have tried:

```

$ for i in $(ldd /usr/bin/gnome-terminal 2>&1 | sed -n 's/.* => \([^ ]*\) .*/\1/p'); do apt-get source $(dpkg -S $i | cut -d: -f1); done
$ grep -r 'missing on display' .

```

But don't get any hits.  Any ideas?

---


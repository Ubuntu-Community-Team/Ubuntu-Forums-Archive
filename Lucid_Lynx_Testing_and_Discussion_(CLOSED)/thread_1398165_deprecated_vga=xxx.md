---
title: "deprecated vga=xxx"
date: 2010-02-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dino99 on 2010-02-04
hi,

on a daily updated lucid32 with grub-ppa package, when i run grub-mkconfig, vga=xxx is inserted into the boot line.
Of course i have to remove that when booting. Can't find why it is built in.

---

### Post by ibuclaw on 2010-02-04
vga has been replaced with gfxpayload.

AFAIK, there is no interface to this variable yet, but I suppose the most you can do is this for the time being:

/etc/grub.d/00_headers
```

    cat << EOF
if loadfont `make_system_path_relative_to_its_root ${GRUB_FONT_PATH}` ; then
  set gfxmode=${GRUB_GFXMODE}
[COLOR="navy"]  set gfxpayload=1280x800@24[/COLOR]
  insmod gfxterm
  insmod ${GRUB_VIDEO_BACKEND}
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
EOF

```

Regards
Iain

---

### Post by dino99 on 2010-02-04
> **tinivole said:**
> vga has been replaced with gfxpayload.

AFAIK, there is no interface to this variable yet, but I suppose the most you can do is this for the time being:

/etc/grub.d/00_headers
```

    cat << EOF
if loadfont `make_system_path_relative_to_its_root ${GRUB_FONT_PATH}` ; then
  set gfxmode=${GRUB_GFXMODE}
[COLOR="navy"]  set gfxpayload=1280x800@24[/COLOR]
  insmod gfxterm
  insmod ${GRUB_VIDEO_BACKEND}
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
EOF

```

Regards
Iain

thanks, it's not a big issue, is it known ? May i fill a report on LP ?

---

### Post by jfernyhough on 2010-02-04
GFXPAYLOAD and GFXMODE can be set in /etc/default/grub

You can also edit the default kernel line to remove vga=xxx, just run a sudo grub-update afterwards.

---

### Post by dino99 on 2010-02-09
As i have two distros with grub2 1.98 and one with 1.96 (jaunty), this weird vga=xxx seem to be due to 1.96 release only. So, i have a new question: can we use 1.98 with Jaunty ?

---

### Post by jfernyhough on 2010-02-09
I'd presume so. I have a PPA enabled (ricotz?) that adds GRUB 1.98 to Karmic.

---

### Post by ranch hand on 2010-02-09
I enabled the lucid main repo for a couple things in Jaunty.  One was grub197 (yes it was a while back) and it works great.  I need to get the 1.98 version as I am sure it will be fine.

---

### Post by dino99 on 2010-02-10
> **ranch hand said:**
> I enabled the lucid main repo for a couple things in Jaunty.  One was grub197 (yes it was a while back) and it works great.  I need to get the 1.98 version as I am sure it will be fine.

thanks, but Kansasnoob & VMC have pointed problems with 1.98 (from ppa), so now i only use 1.98 (from lucid). (see my last posts)
As you have great experience with grub2, what do you think about 1.98 with jaunty ?

---

### Post by ranch hand on 2010-02-10
So far I am only running grub1.97 in 9.04.  Just have not been on that drive long enough to change the bugger.

Works great on 9.10.

---


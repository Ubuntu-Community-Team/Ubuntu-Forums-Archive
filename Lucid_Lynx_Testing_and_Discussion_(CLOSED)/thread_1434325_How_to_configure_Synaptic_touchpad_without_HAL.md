---
title: "How to configure Synaptic touchpad without HAL?"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by megaexception on 2010-03-20
i have acer notebook with synaptic touchpad, and i want to configure touchpad options, like tapping, scrolling, sensibility, etc.

in pre-9.10, i've done this with xorg.conf (input device -> options).
in 9.10, i've done this with hal policy (xml file in /etc/hal/fdi/policy with options).
in 10.04beta1, hal is removed, xorg.conf is ignored.


i've tried to use udev (i've found example in /lib/udev/rules.d/66-xorg-synaptics.rules), tried to place rules in both /lib/udev/rules.d/ and /etc/udev/rules.d, but no effect.
i've looked into /var/log/udev, and i see that rules are matching, but Xorg doesn't use options set using udev.


please, can you advice me, how can i achieve synaptic configuration?


p.s. i do no want to run xinput --set-prop .. each session, and i do not want to install gnome to use gnome-control-panel?

---

### Post by uljanow on 2010-03-20
It is required to use udev. Try something like the following in /etc/udev/rules.d :

```
ACTION!="add|change", GOTO="xorg_synaptics_end"
KERNEL!="event*", GOTO="xorg_synaptics_end"

ENV{ID_INPUT_TOUCHPAD}!="1", GOTO="xorg_synaptics_end"

ENV{x11_options.TapButton1}="1"
ENV{x11_options.TapButton2}="2"
ENV{x11_options.TapButton3}="3"
ENV{x11_options.HorizEdgeScroll}="1"
ENV{x11_options.RBCornerButton}="3"

LABEL="xorg_synaptics_end"
```

---

### Post by megaexception on 2010-03-20
> **uljanow said:**
> It is required to use udev. Try something like the following in /etc/udev/rules.d :

```
ACTION!="add|change", GOTO="xorg_synaptics_end"
KERNEL!="event*", GOTO="xorg_synaptics_end"

ENV{ID_INPUT_TOUCHPAD}!="1", GOTO="xorg_synaptics_end"

ENV{x11_options.TapButton1}="1"
ENV{x11_options.TapButton2}="2"
ENV{x11_options.TapButton3}="3"
ENV{x11_options.HorizEdgeScroll}="1"
ENV{x11_options.RBCornerButton}="3"

LABEL="xorg_synaptics_end"
```

as i've told, i have very similar file in /etc/udev/rules.d, and udev catches touchpad add event, but Xorg doesn't use ENV{x11_options....}.

---

### Post by megaexception on 2010-03-21
solved.i have mistyped x11_options. twice. checked man page for names, double checked udev rule, and everything start to work :)

---


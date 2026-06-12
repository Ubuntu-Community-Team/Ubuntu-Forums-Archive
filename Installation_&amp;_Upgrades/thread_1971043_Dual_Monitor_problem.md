---
title: "Dual Monitor problem"
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by cewan on 2012-05-02
Hi everybody,
I have upgraded to 12.04 from 11.10 and Display settings is not working for me. When I try to change displays I get the following error:

**GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `org.gnome.SettingsDaemon.XRANDR_2' on object at path /org/gnome/SettingsDaemon/XRANDR**

Anyone have any idea on what the problem is?

I am running a Lenovo Thinkpad T410 with Intel graphics.

I have googled this and also searched the forum but cannot find anything relevant.

---

### Post by valdmanv on 2012-05-04
Having the same problem:confused:
any workarounds?

---

### Post by cewan on 2012-05-04
> **valdmanv said:**
> Having the same problem:confused:
any workarounds?

Not really, I guess there is a solution using xrandr from command line. But that doesn't help non-hackers :-/

---

### Post by AncientPC on 2012-12-27
Looks like it's related to this [bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1007588").

A short term solution is to use `arandr`.

---


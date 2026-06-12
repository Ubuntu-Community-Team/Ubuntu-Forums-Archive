---
title: "X not starting on edgy"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by prabhus14 on 2006-10-11
Can someone help me. I recently upgraded to edgy from dapper. After this my Xserver is not starting up. My Xorg.log has the below messages

(II) LoadModule: "i915"
(WW) Warning, couldn't open module i915
(II) UnloadModule: "i915"
(EE) Failed to load module "i915" (module does not exist, 0)
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.3
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.5
(EE) No drivers available.

Fatal server error:
no screens found

Mine is a dell laptop (Inspiron B130).

Uname -a
Linux jumanji 2.6.17-7-386 #2 Wed Sep 6 17:53:03 UTC 2006 i686 GNU/Linux

Appears like some problem with intel 915 driver. So I download the latest driver from dri.freedesktop.org. But I am getting the below error.

Installing files:
        GL & GLU libraries...install.sh: 708: Syntax error: Bad fd number
done
        core libraries...install.sh: 708: Syntax error: Bad fd number

Can someone help me out. My email is [email]prabhu.subramanian@gmail.com[/email]

---


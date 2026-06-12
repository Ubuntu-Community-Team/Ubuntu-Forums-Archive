---
title: "ccsm in intrepid problem with enabling effects"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dondad on 2008-10-15
In ccsm, when I try to enable any of the effects, the box gets checked, then a couple of seconds later it unchecks itself and won't let me enable anything. Any idea where to look for the problem? If I go to the setup page for any of the effects and check the "enable" box, it stays checked, but if I go back to the main page, it is gone and also gone if I go back to the specific page.

---

### Post by loomsen on 2008-10-15
start ccsm in a terminal, reproduce your error, and read what the systemdebugger aka terminal wants to tell ya...

---

### Post by dondad on 2008-10-16
> **loomsen said:**
> start ccsm in a terminal, reproduce your error, and read what the systemdebugger aka terminal wants to tell ya...

Here is what I got when I opened ccsm and then tried to enable 3d windows.

```


GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

Any idea how to fix this?

Thanks for the help.

---

### Post by dondad on 2008-10-19
> **dondad said:**
> Here is what I got when I opened ccsm and then tried to enable 3d windows.

```


GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

Any idea how to fix this?

Thanks for the help.

bump

Still doing it. I can enable cube gears, but no atlantis or any of the effects like 3d windows. The box checks, then unchecks itself after a few secondds.

---

### Post by dondad on 2008-10-25
bump again. Still doing the same thing. I completely removed compiz and everything that I could find related to it. On reinstall, it still does the same thing. Should I post this on the desktop effects and customization forum?

---


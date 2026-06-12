---
title: "Having issues with Intel video again? Cannot enable Compiz and crashing with Alt+Tab"
date: 2009-08-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andresmh on 2009-08-29
Please add more info to these bugs if you're having the same issues:
[https://bugs.edge.launchpad.net/ubuntu/+source/compiz/+bug/420308](https://bugs.edge.launchpad.net/ubuntu/+source/compiz/+bug/420308)
[https://bugs.edge.launchpad.net/ubuntu/+source/compiz/+bug/420312](https://bugs.edge.launchpad.net/ubuntu/+source/compiz/+bug/420312)

---

### Post by TrueTom on 2009-08-29
The applet uses ```
jockey-gtk --check-composite
``` to check if there is compositing support on your system... This seems to fail for my Intel card too...

---

### Post by TrueTom on 2009-08-29
Here is a small test for Composite check of the current driver...

```
#include <X11/extensions/Xcomposite.h>
#include <gdk/gdk.h>
#include <gdk/gdkx.h>

int main(int argc, char *argv[])
{
    int event_basep = 0, error_basep = 0;

    gdk_init(&argc, &argv);

    int result = XCompositeQueryExtension(GDK_DISPLAY(), &event_basep, &error_basep);

    printf("%d\n", result);
}
```

---

### Post by andresmh on 2009-08-29
I ran jockey-gtk --check-composite and I got

```

There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.

```

---

### Post by andresmh on 2009-08-29
lspci | grep VGA returns:

```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

```

---

### Post by tahina on 2009-08-29
I get the refusal to enable visual effects too, but when I try it again right after, it works. I don't get the crash with the alt-tab.

---

### Post by TrueTom on 2009-08-29
The **jockey-gtk** command failing shouldn't be a problem, though, I'm not sure why it is run before checking the current driver for composite support...

---

### Post by TrueTom on 2009-08-29
I'm calling it a day. My guess is that the timeout of 8 seconds that the applets waits for Compiz to start is too short...

---

### Post by TrueTom on 2009-08-29
Ok, the timeout is only a side problem. The real problem is, that after you click the "Normal" checkbox the "Do you want to keep the settings?" dialog should be shown immediately. Instead, for me, the hour glass cursor is shown until the timout hits...

Edit: Which doesn't seem to be the fault of compiz...

---


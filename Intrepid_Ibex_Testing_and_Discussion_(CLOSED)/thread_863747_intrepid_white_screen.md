---
title: "intrepid white screen"
date: 2008-07-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by danbuter on 2008-07-18
I installed the Alpha 2 for Ubuntu II. It brings up everything ok, even showing the heron wallpaper. Then the screen goes pure white. I can still see my mouse pointer, but nothing else. Any help will be appreciated.

---

### Post by Rocket2DMn on 2008-07-18
This is a known problem with compiz with mesa, see [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/245888](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/245888)

To get around this, I have been hitting ALT+F2 after login and typing out
```
metacity --replace
```
without being able to see what is happening (it's running that command though), so compiz is disabled and replaced with the standard window manager, metacity.

---

### Post by danbuter on 2008-07-18
That did the trick. Thanks!
Now, if I delete Compiz, I shouldn't have this problem anymore, correct?

---

### Post by Rocket2DMn on 2008-07-18
I wouldn't delete it, then you can't test it :)
Remember, this is a development release of Ubuntu, so stuff is bound to break.

---

### Post by waspbr on 2008-07-19
lemme guess you have an ati card?
had that problem in hardy, solved it by using envy to get the lastest ati drivers.

---

### Post by chrismine on 2008-07-19
> **waspbr said:**
> lemme guess you have an ati card?
had that problem in hardy, solved it by using envy to get the lastest ati drivers.
Sorry - I get the same white screen with Nvidia 6200. As far as I remember it started after the latest xorg was installed.

---

### Post by waspbr on 2008-07-19
hmmm... the plot thickens

---

### Post by spamzilla on 2008-07-19
Same happens with Intels 965 chipset (x3100)

---

### Post by adult swim on 2008-07-19
> **spamzilla said:**
> Same happens with Intels 965 chipset (x3100)

this happened on my intel 945 but it fixed itself a few update cycles ago
as someone already mentioned metacity --replace works just fine
if you want to have metacity as your default window manager on startup this page will walk you through it [http://www.ubuntu1501.com/2008/04/stop-compiz-fusion-from-loading.html](http://www.ubuntu1501.com/2008/04/stop-compiz-fusion-from-loading.html)

---

### Post by psyke83 on 2008-07-19
> **adult swim said:**
> this happened on my intel 945 but it fixed itself a few update cycles ago
as someone already mentioned metacity --replace works just fine
if you want to have metacity as your default window manager on startup this page will walk you through it [http://www.ubuntu1501.com/2008/04/stop-compiz-fusion-from-loading.html](http://www.ubuntu1501.com/2008/04/stop-compiz-fusion-from-loading.html)

Umm.... no ;). That's overcomplicating things unnecessarily. Go to System/Preferences/Appearance, click the Desktop Effects tab and select "None".

---

### Post by klange on 2008-07-19
The problem is in Mesa reporting "all's well" to run Compiz with direct rendering, which won't work because Compiz won't map textures from pixmaps (which gives white windows).

Forcing indirect by changing /usr/bin/compiz (compiz-manager) so that INDIRECT="yes" should fix things.

---

### Post by danbuter on 2008-07-20
I ended up deleting Compiz (which I have done since it's inclusion anyways). That program should be optional, not default. And I have Intel 950 graphics.

---

### Post by psyke83 on 2008-07-20
> **danbuter said:**
> I ended up deleting Compiz (which I have done since it's inclusion anyways). That program should be optional, not default. And I have Intel 950 graphics.

Yeah, but it can cause problems if you "delete" (i.e. remove) the compiz package; it can cause the "ubuntu-desktop" metapackage or other important packages to get uninstalled. If that happens, then you will encounter difficulties during upgrades, and it won't help the testing process very much...

Just *disable* Desktop Effects the way I mentioned earlier in this thread.

---

### Post by wesswei on 2008-07-20
Well, like danbuter said, compiz, while awesome and nice effects SHOULD be optional. It was in the 7.04 release. 

Nevertheless if you have ATI, and you WANT compiz, the solution could be that the fglrx module is not loading. Instead mesa is loading and clearly can't handle compiz.

Follow adult swim's way to immediately disable.

This should restore metacity. Follow psyke83's way to turn compiz off.

Also if you're using an ATI card and have fglrx (proprietary driver) installed, make sure it is in use and not mesa.
in terminal:
```
fglrxinfo
```

should say ati and not mesa.

---

### Post by InfinityCircuit on 2008-07-30
How do I switch fglrx from mesa to ati?

```
dmr@kronos:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 1.4 (2.1 Mesa 7.1 rc3)

```

Right now I have the same problem with desktop effects on a Radeon HD 3650 (R6xx)

EDIT: I now see that it is using radeon as the driver.  Switching to fglrx corrupts the colors and keeps me down to 800x600.  This is probably a problem with Intrepid kernels and fglrx atm.

---


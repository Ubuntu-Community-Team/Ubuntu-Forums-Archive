---
title: "Broken Scrolling on Touchpad and Broken Konsole"
date: 2009-05-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tripinva on 2009-05-19
Hello:

After last night's updates, my system locked up.  Upon resetting it with the Magic SysRq key, I had two rather large problems.

First and less important, the scrolling on my touchpad is broken once again.  It spent some time being broken during the Jaunty alphas but I downgraded and that resolved it for the short term.  In my brief search last night, I was unable to find the old package.  I also don't want to file a bug report until I know whether it's an actual bug or just something stupid on my end.

EDIT:  Amazing what being awake will do; I found the package and downgraded successfully.  Scrolling is fixed.

The second problem is a lot more troublesome.  I live with Konsole open all the time.  I love my command line, and when I went to log in, I get blank windows with no prompt and no way to type in them.  Now I had this problem during the Jaunty alpha and made a script that mounted /dev/pts on bootup, since apparently it was failing to mount.  Running that did not fix the problem this time.  I've been flipping to Ctrl+Alt+F1, but that's frustrating and takes more time.

Any thoughts on these issues?  I'm running the latest Kubuntu alpha packages with KDE4.2.85 and the new kernel.

- Trip

---

### Post by t.rei on 2009-06-10
I am having an issue like that with kde4 in karmic. Scrolling simply does not work. 

It works fine in:
gnome
enlightenment
xfce

I can use the touchpad to move the pointer but neither the "tapping to click" nor the scrolling works as in all other desktops. help? It's definately a no-kde criteria for me, right now.

---

### Post by features on 2009-06-11
Hi all,

I have the same issue with my touchpad, but in Gnome, so I guess it's not just a KDE thing.

---

### Post by Reiger on 2009-06-11
Same problem with both Gnome and KDE here. At first its really annoying; then you basically get used to it. :p

---

### Post by soapytheclown on 2009-06-11
strange i've just done the latest updates and mine is still working fine as is my konsole too! sound however is still not!

---

### Post by neferty on 2009-06-14
bump. after upgrading to KK alpha1 (and 2) tapping doesn't work anymore (I'm on VAIO VGN series. The new .30 kernel provides a far better support for built-in vaio features, but tapping ceased to work :-/). Is there any solution for this?

---

### Post by taavikko on 2009-06-14
> **neferty said:**
> but tapping ceased to work :-/). Is there any solution for this?

[https://bugs.launchpad.net/bugs/378391](https://bugs.launchpad.net/bugs/378391)

---

### Post by neferty on 2009-06-15
so, as I understand it, I have to manually add these lines to my 11-x11-synaptics.fdi, correct?
```
<merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">2</merge>
        <merge key="input.x11_options.TapButton3" type="string">3</merge>
```

---

### Post by geojorg on 2009-06-15
The package you need is in William Grant PPA, it solves the problem with tap.

xfree86-driver-synaptics - 0.15.2-0ubuntu7~wgrant3 

You can find it here.
[https://launchpad.net/~wgrant/+archive/ppa](https://launchpad.net/~wgrant/+archive/ppa)

---

### Post by zoff_ita on 2009-06-15
I solved the problem in Gnome simply installing gsynaptics and enabling Tapping in its settings...

---


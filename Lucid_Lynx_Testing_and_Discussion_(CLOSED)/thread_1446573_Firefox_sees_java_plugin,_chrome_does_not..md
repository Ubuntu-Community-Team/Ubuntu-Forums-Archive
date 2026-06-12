---
title: "Firefox sees java plugin, chrome does not."
date: 2010-04-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ubername on 2010-04-04
Hi
Chrome is not properly recognizing my java plugin (icedtea). When I go to websites which require java I don't get any messages saying 'java not installed' or similar, but the applets fail to execute. In Firefox all is well. Interestingly when I do 'about: plugins' in chrome it does not display a java plugin, yet firefox shows the IcedTea plugin. I have a symlink to libjavaplugin.so in /usr/lib/mozilla/plugins.

IcedTeaPlugin and all the other java stuff were installed via the main repos.

Any clues to get chrome to work with java?

p.s. How do you disble smilies? about: plugins should not have a space in it, but otherwise you get about:plugins !

---

### Post by NCLI on 2010-04-04
> **ubername said:**
> p.s. How do you disble smilies? about: plugins should not have a space in it, but otherwise you get about:plugins !

You'll have to put it in a ```
 box.

[CODE]about:plugins
```

---

### Post by PhilippeK on 2010-04-04
Java in Chrome : got this problem before (java working in firefox not in chrome)

1st: use Java jre 1.6.0_18 (download from java;Com). Before downloading and installing you have to remove any other java and definitively eliminate icedtea
2d: the java plugin is now libnpjp2 and not anymore libjavplugin
3d: once all that is done you should see the plugin in about:plugins of firefox AND chrome
4th BUT in my case java applet works in firefox but not in Chrome. In chrome when the applet does not open, I right click "reload frame" and all goes fine

Hoping this will help you

---

### Post by PhilippeK on 2010-04-04
Forgot to tell: use the "chrome unstable" version; last version is 5.0.366.2dev (if not in the synaptic, download it from internet).

---

### Post by Uncle Spellbinder on 2010-04-04
Java jre 1.6.0_19 is actually the current version, not 18.

---

### Post by zenarcher on 2010-04-04
I have Java JRE 1.6.0_19 installed and Java is working fine with the Chrome browser.  Installed Java from the repositories and Chrome browser from the Chrome browser website.

Cheers,
zenarcher

---

### Post by ubername on 2010-04-06
> **PhilippeK said:**
> Java in Chrome : got this problem before (java working in firefox not in chrome)

1st: use Java jre 1.6.0_18 (download from java;Com). Before downloading and installing you have to remove any other java and definitively eliminate icedtea
2d: the java plugin is now libnpjp2 and not anymore libjavplugin
3d: once all that is done you should see the plugin in about:plugins of firefox AND chrome
4th BUT in my case java applet works in firefox but not in Chrome. In chrome when the applet does not open, I right click "reload frame" and all goes fine

Hoping this will help you

Thanks, using java from java.com and getting rid of icetea etc has done the trick. Now to sort out my strange flash behaviour in chrome... Watch this forum for more!

---

### Post by Pitel on 2010-04-20
I have similirar problem... Chrome on lucid seems to not recognize plugins in /usr/lib/mozilla/plugins/. I've also Adobe Reader plugin here which is "invisible" in chrome. But it works in karmic.

---


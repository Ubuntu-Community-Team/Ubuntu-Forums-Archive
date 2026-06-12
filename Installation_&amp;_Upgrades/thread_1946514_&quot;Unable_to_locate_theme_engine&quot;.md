---
title: "&quot;Unable to locate theme engine&quot;"
date: 2012-03-25
forum: Installation &amp; Upgrades
---

### Post by TejasMChavan on 2012-03-25
I had fresh installation of Ubuntu 12.04 yesterday and did update today.
While installation of these updates, in terminal I got these warnings;

**GTK warnings **: Unable to locate theme engine in module_path "pixmap" at usr/share/perl5/Debconf/Frontend/Gnome.pm Line 103**

What are these warnings for??

After some research I reached here... [http://apt.ubuntu.com/p/gtk2-engines-pixbuf](http://apt.ubuntu.com/p/gtk2-engines-pixbuf)

Should I apply these??

---

### Post by TejasMChavan on 2012-03-25
Okay an update...
After the update I am facing strange problem... 
The panel and dock is flickering when its doing some action like if I move cursor over it, or when program is loading, web page is refreshing, (i mean the animated movement, when its happening it flickers...)

Please someone help...

---

### Post by arpanaut on 2012-03-25
The GTK Warning is inconsequential and updating should pull the pixbuf file automatically to fix.

You have had simply some bad timing as far as the flickering issue, this just happened in the past 24-36 hours, as a result of a major upgrade to compiz and unity... should be sorted in short order.

You are aware that 12.04 is still in development, still at Beta 1 stage, with another month to go before final release.
Being such, one should expect and plan for breakage and instabilities. 

Some are saying that using in a terminal: ```
unity --reset
```

solves the flickering issue, some not.  Anyway it is a non fatal issue and will be fixed shortly.

see here: [http://ubuntuforums.org/showthread.php?t=1946138](http://ubuntuforums.org/showthread.php?t=1946138)

---

### Post by TejasMChavan on 2012-03-25
> **arpanaut said:**
> The GTK Warning is inconsequential and updating should pull the pixbuf file automatically to fix.

You have had simply some bad timing as far as the flickering issue, this just happened in the past 24-36 hours, as a result of a major upgrade to compiz and unity... should be sorted in short order.

You are aware that 12.04 is still in development, still at Beta 1 stage, with another month to go before final release.
Being such, one should expect and plan for breakage and instabilities. 

Some are saying that using in a terminal: ```
unity --reset
```

solves the flickering issue, some not.  Anyway it is a non fatal issue and will be fixed shortly.

see here: [http://ubuntuforums.org/showthread.php?t=1946138](http://ubuntuforums.org/showthread.php?t=1946138)

Thanks!! I had also reported the bug to launchpad and the guy there asked me to switch to unity-2d. Its helping me for some time now.

{Anyway can I get the title to be renamed appropriately, maybe it can help others??}

---


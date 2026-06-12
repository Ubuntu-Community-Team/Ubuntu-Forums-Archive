---
title: "Firefox create new windows when I close website"
date: 2008-08-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Hoà on 2008-08-04
I'm using Firefox 3.0.1 on Intrepid Ibex alpha. When I close websites which have many images (or flashes), it create some new windows with the images (or flashes) of those websites (Some windows're empty). If I close those windows, Firefox will also be closed. Have you ever encounted this problem before? (And if possible, how can I fix it?)

You can see this problem on my attached files.

---

### Post by OutOfReach on 2008-08-04
That is an.... extremely odd bug.

---

### Post by mgsfan on 2008-08-04
I get that too sometimes though only 2 blank windows popup for me

---

### Post by Gourgi on 2008-08-04
+1

already mentioned it here [http://ubuntuforums.org/showpost.php?p=5489313&postcount=16](http://ubuntuforums.org/showpost.php?p=5489313&postcount=16)
i still didn't find a bug report for this so i think i should fill one.

---

### Post by pyrotech on 2008-08-10
Any progress on this, anyone?

Extremely annoying with all the untitled windows that pop up all the time..
After 10 minutes og smurfing the web, I got like 40 of them clutting up my screen.. 

It happens both when I enter and leave pages.. 
It seems like it might be all the flash-commercials that pops up in a new window, and then disappears instantly, leaving an untitled window behind..

---

### Post by mc4100 on 2008-08-10
> **pyrotech said:**
> Any progress on this, anyone? 
It seems like it might be all the flash-commercials that pops up in a new window, and then disappears instantly, leaving an untitled window behind..

Have you tried AdBlockPlus ? It might be a good workaround until they fix the bug -- if that doesn't work then you might try NoScript, since that prevents flash being shown.

---

### Post by cariboo on 2008-08-11
They still pop up even with adblock plus. I do believe this is a flash bug, as it only happens on sites with flash content.

Jim

---

### Post by Abetorius on 2008-08-11
Same here. FF opens new windows with flash content of website.
Closing of such window results in closing FF.

---

### Post by pyrotech on 2008-08-18
this seems to have stopped happening after I installed flash 10..

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

\o/

---

### Post by Nullack on 2008-08-19
I stick with the repos so that my testing adds to Ubuntu and not a custom install.

Anyway the repos have the adobe flash 10 development revisions in it. Unfortunately the issue is not fixed so far.

---

### Post by gmxgeek on 2008-08-29
I am having this issue as well. Started a few days ago.

---

### Post by Naddiseo on 2008-08-29
> **gmxgeek said:**
> I am having this issue as well. Started a few days ago.

Ditto. If you close one of the blank windows it kills firefox. I think it gave some error about not being able to free memory.

---

### Post by bruce89 on 2008-08-29
This is [bug #250769]("https://bugs.launchpad.net/bugs/250769").

---

### Post by lordmyth on 2008-08-29
i get the same thing except my windows don't display the flash content, but just stay blank
[http://omploader.org/vcGtw](http://omploader.org/vcGtw)

---

### Post by Slug71 on 2008-08-29
Was doing this to me bad yesterday too. I uninstalled Firefox 3.0.1 from Synaptic and then also Flashplugin-nonfree. Restarted then reinstalled. Has been working fine for me since.  Today i been getting a couple npviewer popups like that but they go away and havent caused problems.

---

### Post by _oOMOo_ on 2008-08-29
I was experiencing this too. It does indeed seem to be a flash issue:

```

sudo apt-get remove --purge nspluginwrapper
sudo apt-get install flashplugin-nonfree
```

fixed it for me.

---

### Post by Slug71 on 2008-08-29
Thanks, will give that a try if i get probs again.

---

### Post by Gourgi on 2008-08-30
> **_oOMOo_ said:**
> I was experiencing this too. It does indeed seem to be a flash issue:

```

sudo apt-get remove --purge nspluginwrapper
sudo apt-get install flashplugin-nonfree
```

fixed it for me.

+1 fixed
i still use flashblock firefox plugin  though

---

### Post by Slug71 on 2008-08-30
> **_oomoo_ said:**
> i was experiencing this too. It does indeed seem to be a flash issue:

```

sudo apt-get remove --purge nspluginwrapper
sudo apt-get install flashplugin-nonfree
```

fixed it for me.

+1

---


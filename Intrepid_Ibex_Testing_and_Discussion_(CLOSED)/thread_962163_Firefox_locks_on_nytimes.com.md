---
title: "Firefox locks on nytimes.com"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by lancest on 2008-10-29
Firefox on my Intrepid 64 seems to lock up periodically when I visit the nytimes.com web site. I tried turning off Compiz but get same  lockup result every few hours (just without black screen). Is this related to Flash? Also this happened before on other sites but infrequent.

---

### Post by w4ett on 2008-10-29
I was getting frequent lockups due to flash on my install, so in about:config I changed the following settings:

> network.http.pipelining;true
network.http.pipelining.maxrequests;8
network.http.proxy.pipelining;true

I've had no lockups since then.

---

### Post by lancest on 2008-10-29
Tried you suggestion- still getting 7 second Firefox blackscreen lockups quite frequently. Nvidia 7300

---

### Post by Kobalt on 2008-10-29
Could be related to flash, yes. Which version do you use? Did you try removing flash for instance?

---

### Post by w4ett on 2008-10-29
I agree with Kobalt....certainly seems to be Flash related.  If you are using Flash 9,  I'd recommend trying Flash 10.  Be certain to completely remove 9 before installing version 10.

---

### Post by inportb on 2008-10-29
You could also use the excellent Flashblock extension. It blocks annoying Flash ads as a bonus :)

---

### Post by lancest on 2008-10-29
Getting pretty bad -now Firefox freezing at youtube. 
[LIST=1]
[*]Switched to older Nvidia driver but Firefox still freezing
[*]Tried swfdec but still getting some lockup (and less functionality)
[/LIST]

Of course I am using latest Flash 10.12. 
 How would I go about downgrading to 9?

---

### Post by lancest on 2008-10-29
Using Epiphany now. Alot faster and no lockups. I guess Firefox ain't it for 64 bit. (At least for my system) Might try fresh install later.

---

### Post by lancest on 2008-10-29
Ok so now Epiphany just froze. 
Since I tried swfdec before (and same behavior) I'm not sure it's Flash. Will fresh install Intrepid Final.

---

### Post by w4ett on 2008-10-29
> **lancest said:**
> 

Of course I am using latest Flash 10.12. 
 How would I go about downgrading to 9?

Try using the instructions for removal here: [http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html](http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html)

---

### Post by dabl on 2008-10-29
I only watched it for 5 minutes, but I see no problem.  Compiz is running.

---

### Post by w4ett on 2008-10-29
Agreed dabl....I see no problem with that site. (I view it at least twice daily).  My major "problem" sites were Youtube and  Myspace  ( have teenage daughters...lol).   Since doing the changes I outlined before, I've had no problems.....In fact since upgrading to Flash 10, Firefox (subjectively, at least) seems to run a bit smoother.  I might add that I run both 32 and 64 bit systems, and have noticed the same Flash induced crashes until I made the changes.

---

### Post by lancest on 2008-10-29
Appreciate it.I followed those instructions, they were great. 
I was able to verify what I did was correct using the instructions. (Got excited about Flash 10 too)
 But as soon as I opened a second tab in Firefox with youtube video playing and nytimes open- the browser eventually froze up and went black. 
I am going to test this on my 32 bit  later.

---

### Post by lancest on 2008-10-29
Those instructions worked after all. One more reboot did the trick. Pushed Firefox and Flash VERY HARD (Multi video streams) and no more lockups. . Thanks.

---

### Post by w4ett on 2008-10-29
> **lancest said:**
> Those instructions worked after all. One more reboot did the trick. Pushed Firefox and Flash VERY HARD (Multi video streams) and no more lockups. . Thanks.
Super....glad it did the trick...Please mark the thread "Solved"

Good Luck

---

### Post by psyke83 on 2008-10-29
> **w4ett said:**
> Try using the instructions for removal here: [http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html](http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html)

Please everybody, *don't* follow these instructions, or any instructions to manually install Flash or nspluginwrapper. It is irresponsible to recommend this solution as it will install a beta release of flash, and automatic updates will not occur. This is a potential security threat to your system.

Flash should work correctly by default in Intrepid. Simply install flashplugin-nonfree, and **do not** install libflashsupport.

Damage control:
```

$ sudo apt-get remove --purge libflashsupport nspluginwrapper flashplugin-nonfree
$ sudo updatedb
$ locate libflashplayer.so

```

Check the results of the locate command and delete all instances of "libflashsupport.so" on your system. Then, reinstall flash:

32-bit:
```

$ sudo apt-get install flashplugin-nonfree
```

64-bit:
```

$ sudo apt-get install flashplugin-nonfree nspluginwrapper
```

---

### Post by w4ett on 2008-10-29
[QUOTE=psyke83;6061190]Please everybody, *don't* follow these instructions, or any instructions to manually install Flash or nspluginwrapper. It is irresponsible to recommend this solution as it will install a beta release of flash, and automatic updates will not occur. This is a potential security threat to your system.[/CODE]


Hmmm....Betas are Bad?....sheesh...

Seriously...if Flash 9 & 10 from the repos are not doing the trick...why is it "Irresponsible" to recommend trying the Beta.....My O/S is Beta...why not my flash plugin?

I certainly wouldn't recommend it on the beginner's forum....but I believe it is to be considered here while we are in beta testing.

---

### Post by psyke83 on 2008-10-30
> **w4ett said:**
> Hmmm....Betas are Bad?....sheesh...

Ok, then explain the advantage of manually installing a beta version of Flash 10 (dated from May), when we already have the final build of Flash 10 in our repositories. 

Please, also let us know the advantages of a manual installation that's going to disable the ability for the flash plugin to update via the official repositories.

---

### Post by w4ett on 2008-10-30
I think I answered previously...(sorry the server hiccup'd) while I was posting......

---

### Post by psyke83 on 2008-10-30
> **w4ett said:**
> I think I answered previously...(sorry the server hiccup'd) while I was posting......

Ok, I see it now. The main causes are due to third-party packages causing conflicts (missing libraries), and windowless mode bugs.

Check:
```
$ ldd /usr/lib/flashplugin-nonfree/libflashplayer.so
```
If there are any missing libraries indicated in that output, it's most likely due to a conflicting package. I've seen many cases where people who upgraded from Hardy to Intrepid had old mozilla packages from ~fta's PPA which were missing vital symlinks. It can be easily fixed, by installing the official versions of the offending packages.

If flash content seems to "cut out" and turn into a grey box frequently, then it's a windowless mode bug. This is a problem that only 64-bit should experience*, and it's due to nspluginwrapper. A workaround is available here: [http://blogs.adobe.com/penguin.swf/2008/08/windowless_mode_fix.html](http://blogs.adobe.com/penguin.swf/2008/08/windowless_mode_fix.html)

* If you're on a 32-bit install & using nspluginwrapper, simply uninstall nspluginwrapper. The i386 build of nspluginwrapper in our repository is outdated, and does not support windowless mode properly.

---


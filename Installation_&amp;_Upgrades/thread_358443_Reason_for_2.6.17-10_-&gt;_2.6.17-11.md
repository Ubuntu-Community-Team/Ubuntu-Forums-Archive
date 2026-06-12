---
title: "Reason for 2.6.17-10 -&gt; 2.6.17-11 ?"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by lojic on 2007-02-10
Can anyone provide the motivation for the recent 2.6.17-11 kernel upgrade? I looked at the following page:

[http://www.mit-lcs.lkams.kernel.org/pub/linux/kernel/v2.6/](http://www.mit-lcs.lkams.kernel.org/pub/linux/kernel/v2.6/)

and it appears to show that the -10 kernel was released on Aug 22 and -11 was released a day later on Aug 23.

So why did we recently upgrade from -10 to -11 ? Also, at first glance, the changelog:

[http://www.mit-lcs.lkams.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.17.11](http://www.mit-lcs.lkams.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.17.11)

doesn't seem to warrant the problems that have occurred. But I'm no kernel developer, so maybe there's something sinister in there that broke my wireless that I missed.

Also, does the Ubuntu 2.6.17-11 kernel upgrade correspond to the 2.6.17-11 kernel on the first link above? I would presume it does, but maybe they're out of synch?

Any information beyond, "the ABI changed..." would be helpful.

Alright, I'll stop obsessing about my broken wireless and have some :popcorn: 

Thanks!

---

### Post by mikewhatever on 2007-02-11
The question is in order. I'd also like to now.

---

### Post by drkknight on 2007-02-11
I did the upgrade and had to reinstall my Nvidia drivers and my sound no longer works. I've got the Nvidia drivers working again, but can anyone give me some help on getting my sound to work again?

---

### Post by eduardoeltortuga on 2007-02-11
Try typing "alsamixer" in a terminal and then mess with the settings from there. Worked for me a couple of times.
     By the way, how do I download the new nvidia drivers from the text mode? When I updated Ubuntu, my old drivers did't work. Thanks and good luck!

---

### Post by Jovec on 2007-02-11
> **eduardoeltortuga said:**
> By the way, how do I download the new nvidia drivers from the text mode? When I updated Ubuntu, my old drivers did't work. Thanks and good luck!

There are a variety of ways, however, in your case, I'd suggest editing your xorg.conf to use the X.org nv driver to get your Desktop back, and then proceed with getting the proprietary nvidia drivers working again.  Any kernel upgrade will stop the proprietary nvidia drivers from working, as they need to be built against a specific kernel version (your drivers were built for .10, but you are running .11 now)


```
$sudo vim /etc/X11/xorg.conf
```

Replace vim with your text editor of choice, i.e. nano

Look for the line that says:

```
Driver         "nvidia"
``` 

and change it to read:

```
Driver         "nv"
``` 

This will use the built-in nvidia driver (with limited 3d acceleration) but will get your Desktop back.  Then, reboot or restart your login manager.

```
$sudo /etc/init.d/gdm restart
``` 

or kdm or xdm as appropriate.  Remember you'll need to install/configure the proprietary nvidia drivers again for full 3D acceleration (part of that process should/will change 'driver "nv"' back to 'driver "nvidia"' for you).  You might want to try [this thread for help]("http://www.ubuntuforums.org/showthread.php?t=281823&highlight=nvidia+envy").

---

### Post by neighborlee on 2007-02-11
> **mikewhatever said:**
> The question is in order. I'd also like to now.

 I would like to know as well...this constantly having new kernels , and then having to install nvidia again is rather annoying..its a shame the process isn't as simple as it is in windows..download to desktop and double click..instead of having to be a newb and know to install a certain file..and then to have to know how to start the CLI and run the rquired script to make xorg.conf do its thing ;)..its more than obvious why ubuntu wants to make these drivers work out of the box, instead of requiring these gyrations ;) ( although with option to opt out/in of course)

cheers
g.leej

---

### Post by drkknight on 2007-02-11
Unfortunately, alsamixer didn't work for me. It appears that my levels are on and up and music appears to be playing in Totem and Rythmbox, but no sound comes out. Is there a daemon that needs to be running or something like that?

---

### Post by mikewhatever on 2007-02-11
It looks like those discussing sound problems are in the wrong thread. drkknight, check your PM.

---

### Post by davekenny on 2007-02-11
I'd also like to know. the update broke vmware-server. the wireless won't use the bridge again.

the last time I had this problem I had to load an older version of the driver. it took several days to find the answer. at least time I know where to start.

it also changed my desktop background :confused: 

I just wonder what else it changed?

dkenny

---

### Post by hoagie on 2007-02-11
Will all of these problems caused by the upgrade, be solved by an upgrade or is there something that we have to do. After reinstalling the nvidia driver X still crashes, giving an error message saying that something is wrong with the nvidia kernel modules. 
Please answer my question.

---

### Post by mikewhatever on 2007-02-11
> **hoagie said:**
> Will all of these problems caused by the upgrade, be solved by an upgrade or is there something that we have to do. After reinstalling the nvidia driver X still crashes, giving an error message saying that something is wrong with the nvidia kernel modules. 
Please answer my question.

The [STATEMENT]("http://ubuntuforums.org/showthread.php?t=356408&page=36") at the bottom of the page says we need to reinstall any third party kernel modules. In your case, I guess that would be linux restricted modules.

---

### Post by flyingbrass on 2007-02-14
Security notices: [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

USN-416-1 is the recent kernel change.

Until a couple weeks ago they were also being posted in the [News & Announcements](http://ubuntuforums.org/forumdisplay.php?f=13) forum here.

---

### Post by lojic on 2007-02-14
> **flyingbrass said:**
> Security notices: [http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

USN-416-1 is the recent kernel change.

Until a couple weeks ago they were also being posted in the [News & Announcements](http://ubuntuforums.org/forumdisplay.php?f=13) forum here.
Thanks, that's the type of info I was looking for. Too bad they didn't reference that from the package description so people could have a way of knowing what was in the update.

---


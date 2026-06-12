---
title: "Totem BBC plugin (where??)"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2008-10-02
I've just been reading the release notes on the beta and discovered this:-

> Ubuntu 8.10 Beta features a new plugin for the Totem movie player that fetches free digital content from the BBC. To enable it, start Totem (Applications -> Sound & Video -> Movie Player), enable the plugin (Edit -> Plugins -> BBC content viewer) and select "BBC" from the drop-down labelled "Playlist". The feed is fetched from a staging server at the moment so there may be a delay while it is downloaded. 

Having done as instructed I pull down the drop down menu to find playlist, properties and youtube. WHO STOLE MY BBC??

Any theories?

---

### Post by xebian on 2008-10-02
> **macroshaft said:**
> I've just been reading the release notes on the beta and discovered this:-



Having done as instructed I pull down the drop down menu to find playlist, properties and youtube. WHO STOLE MY BBC??

Any theories?

Probably the Kubuntista(o)s did.:D  But where is the equivalent for KDE users?

---

### Post by macroshaft on 2008-10-02
I don't think there is one, it specifically states totem. Something to rally round for perhaps?

---

### Post by Kow on 2008-10-02
I cannot even get the plugin to work in totem so you may not be missing out on much atm. I follow the info. on how to enable it via the beta release notes and the plugin window basically freezes when I click the enable checkbox next to the "BBC content viewer" plugin. From command line this is where everything freezes:
> 
** (totem:8617): DEBUG: Init of Python module
** (totem:8617): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:8617): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:8617): DEBUG: Creating Python plugin instance
Traceback (most recent call last):
  File "/usr/lib/totem/plugins/bbc/bbc.py", line 48, in activate
    self.view = ContentView()
  File "/usr/lib/totem/plugins/bbc/contentview.py", line 638, in __init__
    if not self.pool.load():
  File "/usr/lib/totem/plugins/bbc/contentview.py", line 590, in load
    cache_fn = self.ensureCache()
  File "/usr/lib/totem/plugins/bbc/contentview.py", line 571, in ensureCache
    cache_file.delete()
gio.Error: Error removing file: No such file or directory


After awhile it does say it is enabled... but something just seems like it is not working 100% correct.

---

### Post by xebian on 2008-10-02
> **macroshaft said:**
> I don't think there is one, it specifically states totem. Something to rally round for perhaps?

They keep saying it but Kubuntu seems not getting equal attn IMHO.

I tried to install mozilla-totem but it brings in a ton of gnome stuff which I don't think even makes sense like launchpad-integration???

---

### Post by macroshaft on 2008-10-02
That's exactly what's happening for me, except I havn't tried running through terminal.

It's a shame about kubuntu, my first linux experience I didn't hate (I had a very bad red hat experience many moons ago) was with kubuntu and for a long time I preferred it over ubuntu, I think for a windows user it appears more familiar, as such it should be given that attention in order to wow new users over.

---

### Post by bash on 2008-10-02
There already seems to be a bug filed about it:

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/276959](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/276959)

No solution so far.

---

### Post by macroshaft on 2008-10-02
> **bash said:**
> There already seems to be a bug filed about it:

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/276959](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/276959)

No solution so far.

thanks

---

### Post by bruce89 on 2008-10-02
I wouldn't get too excited, it's not anything like the iPlayer (stupid name). It's just the podcasts that the BBC make available.

---

### Post by ronacc on 2008-10-02
it looks to me like it is trying to contact the bbc server and not getting any response , after enabling the bbc plugin and restarting totem I can see outgoing packets on my netmonitor while the wait clock spins in totem , when the clock goes away the packets stop  and no bbc in the dropdown .

---

### Post by Sealbhach on 2008-10-21
> **bruce89 said:**
> I wouldn't get too excited, it's not anything like the iPlayer (stupid name). It's just the podcasts that the BBC make available.

It's not just radio, I've found some moving pictures among the links as well. I think the BBC content is only available to Her Majesty's Subjects at the moment. If you live outside the kingdom you don't get it.

Me, I can't use Hulu coz I'm not in the US.


.

---

### Post by mc4100 on 2008-10-21
> **Sealbhach said:**
> It's not just radio, I've found some moving pictures among the links as well. I think the BBC content is only available to Her Majesty's Subjects at the moment. If you live outside the kingdom you don't get it.

Me, I can't use Hulu coz I'm not in the US.


.

Yeah, for example the Dirac test thingy, which is still a little buggy ...

Screenshot of the quality (I'm impressed):

---

### Post by | MM | on 2008-10-21
> **mc4100 said:**
> Yeah, for example the Dirac test thingy, which is still a little buggy ...

Screenshot of the quality (I'm impressed):

Did the sound get out of sync for you?  Because that what happened when i played the Dirac test stream.

Also, I'm a NZder, and for me all video content i only get a silent video of the chunnel closed, trucks all backed up...  . However, all the other audio content plays.

---

### Post by mc4100 on 2008-10-21
> **| MM | said:**
> Did the sound get out of sync for you?  Because that what happened when i played the Dirac test stream.

Also, I'm a NZder, and for me all video content i only get a silent video of the chunnel closed, trucks all backed up...  . However, all the other audio content plays.

Yes the sound is out of sync, (though I don't know if that's because it's poorly made, or a known problem with dirac encoding), and also the timing is off - in reality the video is ~10 mins long, but as you can see, it's reported as being an hour long.

---

### Post by Mazza558 on 2008-10-29
I can't get it to connect at the moment. Anyone else?

---

### Post by philinux on 2008-10-29
> **Mazza558 said:**
> I can't get it to connect at the moment. Anyone else?

Same here server error.

strace says resource temporarily unvailable.

---


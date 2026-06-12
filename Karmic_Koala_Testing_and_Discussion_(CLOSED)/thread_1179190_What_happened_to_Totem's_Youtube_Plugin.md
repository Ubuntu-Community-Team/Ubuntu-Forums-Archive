---
title: "What happened to Totem's Youtube Plugin?"
date: 2009-06-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by binbash on 2009-06-05
What happened to totem's youtube plugin guys?It is not under plugins anymore after upgrading to 2.27.1 ?

---

### Post by mc4100 on 2009-06-05
Gone here too. The changelog says "Port YouTube plugin to C, much faster." So it's just a bug, it's not been removed.

Also the BBC plugin seems to have been replaced by something that actually streams iPlayer video content (read: a revolting quality .3gp) -- it's better than nothing, I suppose.

---

### Post by binbash on 2009-06-06
Bump

---

### Post by taavikko on 2009-06-06
> **binbash said:**
> Bump

```
totem (2.27.1-1) experimental; urgency=low

  * New upstream development release:
    + This release drops the Xine backend, this allows a much simplified
      packaging.
    + The YouTube plugin is not built at the moment until we have a
      libgdata package, which is required for the plugin now.

```

However,
```
dpkg -l \*libgdata\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                    Version                                 Description
+++-=======================================-=======================================-==============================================================================================
ii  libgdata-google1.2-1                    2.26.1-0ubuntu2                         Client library for accessing Google POA through SOAP interface
ii  libgdata1.2-1                           2.26.1-0ubuntu2                         Client library for accessing Google POA through SOAP interface

```

just an educated guess, that not the right package...

---

### Post by andrewsomething on 2009-06-06
[RIGHT]> **taavikko said:**
> just an educated guess, that not the right package...

I'd guess that it requires libgdata >= 2.27

---

### Post by froggyswamp on 2009-06-06
I recently discovered (on Jaunty) the totem youtube plugin, I used it a bit and all I can say is that it's a childish implementation, the search lasts a lot of time and it doesn't seem to use a separate thread which results in ui freeze and no obvious way to stop it. Whether it's a python issue or not is not an excuse to the end user.
Hopefully the C version will take care of that.

---

### Post by binbash on 2009-06-07
> **taavikko said:**
> ```
totem (2.27.1-1) experimental; urgency=low

  * New upstream development release:
    + This release drops the Xine backend, this allows a much simplified
      packaging.
    + The YouTube plugin is not built at the moment until we have a
      libgdata package, which is required for the plugin now.

```

However,
```
dpkg -l \*libgdata\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                    Version                                 Description
+++-=======================================-=======================================-==============================================================================================
ii  libgdata-google1.2-1                    2.26.1-0ubuntu2                         Client library for accessing Google POA through SOAP interface
ii  libgdata1.2-1                           2.26.1-0ubuntu2                         Client library for accessing Google POA through SOAP interface

```

just an educated guess, that not the right package...

Thanks for this information ;)

---

### Post by durand on 2009-06-08
> **mc4100 said:**
> Gone here too. The changelog says "Port YouTube plugin to C, much faster." So it's just a bug, it's not been removed.

Also the BBC plugin seems to have been replaced by something that actually streams iPlayer video content (read: a revolting quality .3gp) -- it's better than nothing, I suppose.

Really?! It's much better than using the flash stuff though.

---

### Post by philinux on 2009-06-08
Only got Default,Demo print,java, and flash.

---

### Post by tghe-retford on 2009-06-08
> **mc4100 said:**
> Also the BBC plugin seems to have been replaced by something that actually streams iPlayer video content (read: a revolting quality .3gp) -- it's better than nothing, I suppose.
I can't get that far. Attempting to activate it throws up an error:
```
(totem:19606): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed
Traceback (most recent call last):
  File "/usr/lib/totem/plugins/iplayer/iplayer.py", line 6, in <module>
    import iplayer2
  File "/usr/lib/totem/plugins/iplayer/iplayer2.py", line 15, in <module>
    import feedparser
ImportError: No module named feedparser

** (totem:19606): WARNING **: Could not load plugin iplayer


** (totem:19606): WARNING **: Error, impossible to activate plugin 'BBC iPlayer'
```

---

### Post by mc4100 on 2009-06-08
> **tghe-retford said:**
> I can't get that far. Attempting to activate it throws up an error:
```
(totem:19606): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed
Traceback (most recent call last):
  File "/usr/lib/totem/plugins/iplayer/iplayer.py", line 6, in <module>
    import iplayer2
  File "/usr/lib/totem/plugins/iplayer/iplayer2.py", line 15, in <module>
    import feedparser
ImportError: No module named feedparser

** (totem:19606): WARNING **: Could not load plugin iplayer


** (totem:19606): WARNING **: Error, impossible to activate plugin 'BBC iPlayer'
```

Missing dependency:
```
sudo apt-get install python-feedparser
```
And then there's some more, just keep installin' ;)

---

### Post by psyke83 on 2009-06-08
> **philinux said:**
> Only got Default,Demo print,java, and flash.

What happened to the missing question marks in all your posts**?** ;)

The symlinks seem to be broken, see for yourself:

```
$ ls -l /usr/lib/xulrunner-addons/plugins/
```

Edit: should be merged to [this thread]("http://ubuntuforums.org/showthread.php?t=1181766")...

---

### Post by philinux on 2009-06-09
????????????????????????????:p

Will this get fixed automagically or do we have to manually fix this??????

---

### Post by durand on 2009-06-12
Ok I actually tried the iplayer plugin, hoping that it would stream flash quality but the quality is awful. Too bad, I really wanted to stop using their website for streaming.

---


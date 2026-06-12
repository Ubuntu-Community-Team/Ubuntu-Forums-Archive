---
title: "Flash crashing Firefox"
date: 2010-03-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rogerdean on 2010-03-03
Hello all

Flash is repeatedly crashing my Firefox on pages like this -

[http://www.foxtons.co.uk/search?bedrooms_from=2&location_ids=1014-42&price_to=350000&property_id=686357&resource=large_floorplan&search_form=map&search_type=SS&submit_type=search](http://www.foxtons.co.uk/search?bedrooms_from=2&location_ids=1014-42&price_to=350000&property_id=686357&resource=large_floorplan&search_form=map&search_type=SS&submit_type=search)

The plugin crashes under chromium too, but at least doesn't take down the browser...

Any ideas? Cheers
Roger

---

### Post by philinux on 2010-03-03
> **rogerdean said:**
> Hello all

Flash is repeatedly crashing my Firefox on pages like this -

[http://www.foxtons.co.uk/search?bedrooms_from=2&location_ids=1014-42&price_to=350000&property_id=686357&resource=large_floorplan&search_form=map&search_type=SS&submit_type=search](http://www.foxtons.co.uk/search?bedrooms_from=2&location_ids=1014-42&price_to=350000&property_id=686357&resource=large_floorplan&search_form=map&search_type=SS&submit_type=search)

The plugin crashes under chromium too, but at least doesn't take down the browser...

Any ideas? Cheers
Roger

64 or 32 bit?

I'm on 64 bit here and that site does not crash FF here, displays just fine. I dont use chromium.

---

### Post by rogerdean on 2010-03-03
hi there phil, it's 32bit, alpha3 with updates, flash from ubuntu-restricted-extras

it's the 'interactive' floorplans specifically that crash for me - can you see them ok?

cheers!

---

### Post by philinux on 2010-03-03
> **rogerdean said:**
> hi there phil, it's 32bit, alpha3 with updates, flash from ubuntu-restricted-extras

it's the 'interactive' floorplans specifically that crash for me - can you see them ok?

cheers!

Yep just fine. Odd eh.

---

### Post by rogerdean on 2010-03-03
hmmm... reinstalled adobe-flashplugin, no change

can anyone on 32bit see the page above?

cheers

---

### Post by SevenMachines on 2010-03-03
ok here with 32 repository version too on up-to-date lucid, but on amd64

---

### Post by philinux on 2010-03-03
> **rogerdean said:**
> hmmm... reinstalled adobe-flashplugin, no change

can anyone on 32bit see the page above?

cheers

Roger,

Run FF in safe mode. It could be an addon thats killing firefox off.

---

### Post by SevenMachines on 2010-03-03
crashes on pure i386 though, hmm, nspluginwrapper adding stability, thats new :)

---

### Post by rogerdean on 2010-03-03
yeah, still crashing for me, also on a new virtualbox install in safe mode. this readout from my main setup though...

```
roger@roger-laptop:~$ firefox -safe-mode

(firefox-bin:3460): GLib-GObject-WARNING **: IA__g_object_set_valist: construct property "disable-client-side-decorations" for object `GtkPlug' can't be set after construction
Segmentation fault (core dumped)
roger@roger-laptop:~$ 

```

---

### Post by SevenMachines on 2010-03-03
rogerdean: have you reported the bug crash? you might want to add firefox-dbg or something before crashing it. it might be the adobe plugin of course but you never know

---

### Post by philinux on 2010-03-03
> **rogerdean said:**
> yeah, still crashing for me, also on a new virtualbox install in safe mode. this readout from my main setup though...

```
roger@roger-laptop:~$ firefox -safe-mode

(firefox-bin:3460): GLib-GObject-WARNING **: IA__g_object_set_valist: construct property "disable-client-side-decorations" for object `GtkPlug' can't be set after construction
Segmentation fault (core dumped)
roger@roger-laptop:~$ 

```

Temporarily rename .mozilla to .mozilla.backup then run FF.

It could be a corrupt profile.

---

### Post by SevenMachines on 2010-03-03
i'm using virtualbox too (without 3d acceleration) which might be the issue. i see, a glx problem in the stacktrace

---

### Post by SevenMachines on 2010-03-03
you might want to add libgl1-mesa-glx-dbg too before sending the bug report, have some spare time too, its a big report :)

 #0  0x00228832 in _dl_sysinfo_int80 () from /lib/ld-linux.so.2
 No symbol table info available.
 #1  0x009c9230 in raise (sig=11)
     at ../nptl/sysdeps/unix/sysv/linux/pt-raise.c:42
         resultvar = <value optimised out>
 #2  0x00b8293e in nsProfileLock::FatalSignalHandler (signo=11)
     at nsProfileLock.cpp:212
         unblock_sigs = {__val = {1024, 0 <repeats 31 times>}}
         oldact = <value optimised out>
 #3  <signal handler called>
 No symbol table info available.
 #4  0x1f405e4d in glXMakeCurrentReadSGI () from /usr/lib/mesa/libGL.so.1
 No symbol table info available.
 #5  0x1f405f23 in glXMakeCurrent () from /usr/lib/mesa/libGL.so.1
 No symbol table info available.
 #6  0x0188ff0c in ?? () from /usr/lib/flashplugin-installer/libflashplayer.so
 No symbol table info available.
 #7  0x01895604 in ?? () from /usr/lib/flashplugin-installer/libflashplayer.so
 No symbol table info available.
 #8  0x01895b98 in ?? () from /usr/lib/flashplugin-installer/libflashplayer.so
 No symbol table info available.

---

### Post by rogerdean on 2010-03-03
folks, thanks very much for all the support!

phil, i've repeated my steps with a new profile, safe mode, on my main install (not virtualbox). all the same...

```
roger@roger-laptop:~$ firefox -safe-mode

(firefox-bin:4011): GLib-GObject-WARNING **: IA__g_object_set_valist: construct property "disable-client-side-decorations" for object `GtkPlug' can't be set after construction
Segmentation fault (core dumped)
roger@roger-laptop:~$ 

```

sevenmachines, i'm afraid competent bug reporting may be beyond me, i don't really know what your last two posts meant ;) sorry, my ignorance, is anyone able to take this forward?

thanks so much!
roger

---

### Post by SevenMachines on 2010-03-03
does apport not generate the bug report for you? i'm not sure i've got the time for it myself, its almost 200mb!

---

### Post by rogerdean on 2010-03-03
sorry, i don't know what apport is. is it the bug reporting thing that popped up? i may have told it to ignore future crashes - how would i get it back?

---

### Post by rogerdean on 2010-03-03
ok, i hope i've done it well enough!

[https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/531413](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/531413)

---

### Post by emarkay on 2010-03-03
Locks me up too, in Lucid.

I have had this issue for a while, lesser so now, but this looks like one I was dealing with back in Karmic, and was working with a developer, but then there were Apport issues and their time limitations.  This was back in November I recall...

---

### Post by rogerdean on 2010-03-03
interesting... those web pages were fine for me in karmic

---

### Post by grandtoubab on 2010-03-03
> **rogerdean said:**
> Hello all

Flash is repeatedly crashing my Firefox on pages like this -

[http://www.foxtons.co.uk/search?bedrooms_from=2&location_ids=1014-42&price_to=350000&property_id=686357&resource=large_floorplan&search_form=map&search_type=SS&submit_type=search](http://www.foxtons.co.uk/search?bedrooms_from=2&location_ids=1014-42&price_to=350000&property_id=686357&resource=large_floorplan&search_form=map&search_type=SS&submit_type=search)

The plugin crashes under chromium too, but at least doesn't take down the browser...

Any ideas? Cheers
Roger
No ideas but same problem as you with Firefox 3.6.

---

### Post by rogerdean on 2010-03-03
i'm not sure, the plugin crashes in chromium too...
but i'll install opera now, thanks for the tip!

---

### Post by rogerdean on 2010-03-03
ah, it's not the maps i have trouble with, it's the floorplans of the houses (and yes, i am shopping!)

opera crashes too, just freezes. here's the output -

```
roger@roger-laptop:~$ opera

(operapluginwrapper-ia32-linux:3596): GLib-GObject-WARNING **: IA__g_object_set_valist: construct property "disable-client-side-decorations" for object `GtkPlug' can't be set after construction

(operapluginwrapper-ia32-linux:3596): GLib-GObject-WARNING **: IA__g_object_set_valist: construct property "disable-client-side-decorations" for object `GtkPlug' can't be set after construction
opera: Plug-in 3596 is not responding. It will be closed.
opera: Define environment variable OPERA_KEEP_BLOCKED_PLUGIN to keep blocked plug-ins.
roger@roger-laptop:~$ 
```

---

### Post by grandtoubab on 2010-03-03
sorry but opera crashes too I was on the home page,:confused:
And the crash told me it is not a Ubuntu package so it is related to adobe flash player (shockwave) or maybe the plugin Adblock??

---

### Post by rogerdean on 2010-03-03
yeah, adobe-flashplugin i think. i submitted this bug report

[https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/531413](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/531413)

---

### Post by grandtoubab on 2010-03-03
using the plugin flashblock I get the address
[http://www.foxtons.co.uk/flash/floorplan/floorplan_viewer_advanced_tours_v10.swf?data=http://r.foxtons.co.uk/1267611103/chpk0343436_rooms.xml&file=http://r.foxtons.co.uk/1242745544/chpk0343436.swf](http://www.foxtons.co.uk/flash/floorplan/floorplan_viewer_advanced_tours_v10.swf?data=http://r.foxtons.co.uk/1267611103/chpk0343436_rooms.xml&file=http://r.foxtons.co.uk/1242745544/chpk0343436.swf)

before the crash.
 And when I click on the arrow--> crash

I am too lazzy for desinstall Adobe and reinstall the free flash plugin:lolflag:

---

### Post by rogerdean on 2010-03-03
interesting again... your link there doesn't crash, but the floorplans embedded in the main pages always crash

---

### Post by grandtoubab on 2010-03-03
same here I can see the plan in full page of firefox

---

### Post by grandtoubab on 2010-03-03
and even the pictures when I move the mouse on the room

---


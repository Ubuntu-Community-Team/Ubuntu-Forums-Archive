---
title: "mysterious crash report with 3rd party app"
date: 2010-04-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by spillz on 2010-04-17
I have written a gtk+ photo manager in python called phramyd ([http://www.launchpad.net/phraymd](http://www.launchpad.net/phraymd)). The program has run fine on Ubuntu's from Hardy to Karmic, but I keep getting a crash report on Lucid: 

"Sorry, the program phraymd closed unexpectedly" [Report Problem] [Close]

The application doesn't actually crash. I can't report the problem because this is third party software. I can click close my problem continues normally, but I'd like to get to the bottom of this. The problem is I don't know where to look.

Does anyone know where I can find the info about the crash, what might be causing it or what tools I can use to investigate it? Perhaps this is just an early Lucid problem but I'm not sure.

---

### Post by SevenMachines on 2010-04-17
the crash seems to be while importing the map plugin
```
Traceback (most recent call last):
  File "/usr/share/phraymd/phraymd/plugins/mapui.py", line 178, in set_source_signal
    tile_cache=os.path.join(settings.cache_dir,'maps/')+map_source[widget.get_active()][2],
IndexError: tuple index out of range

```i'm guessing the tuple out of range thing is due to widget.get_active() no longer returning what you expect in the couple of lines around mapui.py:178

[EDIT] there have been a few changes in pygtk in lucid as far as i can see from the bugs cropping up

---

### Post by SevenMachines on 2010-04-17
incidently, you might want to try the [programming forum]("http://ubuntuforums.org/forumdisplay.php?f=39"), they'll be python people around there.
There might be knowledgeble python people about here but i'm certainly not one of them :)

---

### Post by SevenMachines on 2010-04-17
actually, on a second look, you might want to look at the initialisation code int the try/catch block in mapui.py:40. essentially, i think try: will give you something like
AttributeError: 'module' object has no attribute 'MAP_SOURCE_OPENSTREETMAP'

so catch: ends up setting a blank map_source, which then fails on line 178. The try block needs to be fixed up i imagine, and the catch block should really set up a useful default tuple, whatever that might be

---

### Post by spillz on 2010-04-17
> **SevenMachines said:**
> actually, on a second look, you might want to look at the initialisation code int the try/catch block in mapui.py:40. essentially, i think try: will give you something like
AttributeError: 'module' object has no attribute 'MAP_SOURCE_OPENSTREETMAP'

so catch: ends up setting a blank map_source, which then fails on line 178. The try block needs to be fixed up i imagine, and the catch block should really set up a useful default tuple, whatever that might be

So just a stupid error on my part. As I recall the osmgpsmap author had noted that phraymd needed to be updated for changes in the API :oops:.

Many thanks, SevenMachines!!

---

### Post by SevenMachines on 2010-04-17
no worries, hope i was helpful in some way!
i tinkered with changing
osmgpsmap.MAP_SOURCE_MAPS_FOR_FREE
to
osmgpsmap.source_get_repo_uri(osmgpsmap.SOURCE_MAPS_FOR_FREE)

and using
map_source=('Null', osmgpsmap.source_get_repo_uri(osmgpsmap.SOURCE_NULL), 'null')
as the default on catch which seemed to take care of the problems, though just to re-emphasise, i know no python so that may be a bit stupid :)

Nice application by the way, best of luck with it

---

### Post by spillz on 2010-04-17
> **SevenMachines said:**
> no worries, hope i was helpful in some way!
i tinkered with changing
osmgpsmap.MAP_SOURCE_MAPS_FOR_FREE
to
osmgpsmap.source_get_repo_uri(osmgpsmap.SOURCE_MAPS_FOR_FREE)

and using
map_source=('Null', osmgpsmap.source_get_repo_uri(osmgpsmap.SOURCE_NULL), 'null')
as the default on catch which seemed to take care of the problems, though just to re-emphasise, i know no python so that may be a bit stupid :)


that sounds about right. btw, what did you use to figure out that it was osmgpsmap causing the crash report?

> 
Nice application by the way, best of luck with it


thanks. Still a lot of features that need to be implemented. Pity you don't know python :)

---

### Post by SevenMachines on 2010-04-18
just running phraymd from the command line and using a python console to test out the occasional few lines or so (i don't know how to use pdb properly!). Eclipse's autocomplete in this sort of situation where i don't know anything is a gift too :)

---


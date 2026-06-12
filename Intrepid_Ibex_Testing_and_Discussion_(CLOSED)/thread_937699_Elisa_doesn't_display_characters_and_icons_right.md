---
title: "Elisa doesn't display characters and icons right"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by olavjunior on 2008-10-04
Elisa goes black and just shows randomly some icons and text. (see screenshots)  

I've tried both the version following Intrepid and the svn 5.12. 

For the svn I don't see anything, everythings black. Hiting enter in the main menu gives me this output:
```
    self.body.connect("file-loaded", lambda x: self._layout())
exceptions.TypeError: <Image object (pgmimage150) at 0xb66ebe4>: unknown signal name: file-loaded
``` I guess it's this error that's causing the bug.

Is this due to the libffi5 discussed in this thread? [http://ubuntuforums.org/showthread.php?t=830140&highlight=elisa](http://ubuntuforums.org/showthread.php?t=830140&highlight=elisa)

---

### Post by plun on 2008-10-04
Well.. there are ongoing bugs about this and
elisa-plugins-ugly is broken both in Debians and Ubuntus repo.

Maybe a libiffi problem. I have seen "debates" but no answer.


From this ppa I manually downloaded some packages.  
[https://launchpad.net/~elisa-developers/+archive](https://launchpad.net/~elisa-developers/+archive)

Still problem with high CPU and composited environment.
Howto disable visualization ?


But Elisa works...:D

---

### Post by olavjunior on 2008-10-04
Well, it actually is unusable for me.. Have you gotten around the problem with the launchpad files? And if so, witch?

I don't know how to disable the visualization. Have been searching for an answer to that earlier

---

### Post by plun on 2008-10-04
Well.... this is within the "higher division" about trouble.

As you wrote you also installed the SVN version and its often causes
a mess with python site-packages.

My lesson is to stay away from SVN and Elisa...


One start can be to uninstall everything with purge

```
sudo apt-get remove --purge elisa*
```

Then a autoremove of left behind packages BUT !! you must know what you are doing !

Also uninstall svn version

If I then install elisa-plugins-ugly from ppa I can then install elisa from Intrepids repo.
[B]
You don't enable this Hardy ppa just download the deb file.[/B]

Or wait for a fix for Intrepids Elisa....


Another important issue is the **f key** for toggling window, much better to run Elisa in a smaller window.

---

### Post by olavjunior on 2008-10-04
That didn't solve it, sadly.. I purged elisa, and used apt-get autoremove, then reinstalled elisa from repos, and installed ugly from launchpad. Still I have the same problem as described above..

---

### Post by plun on 2008-10-04
Start Elisa from terminal, it probably "spits out" a lot.

Try to figure out important errors.

Old SVN site packages is one important thing to check.


For me it works except high CPU...

[[img]http://ubuntu-pics.de/thumb/4032/elisa_RHAak1.jpg[/img]](http://ubuntu-pics.de/bild/4032/elisa_RHAak1.jpg)

---

### Post by olavjunior on 2008-10-04
Well, I don't find any errors regarding to svn as far as I can tell. But here's a full terminal output from Elisa (not that much)

the last lines comes when I try to navigate, so I think that's the bug here

---

### Post by plun on 2008-10-04
Ok...

One more thing to try is to delete your ~**.elisa** folder (hidden > Ctrl-h).

Start again from terminal.

EDIT

You probably also have a site-package mess

> WARNING:root:Cannot find theme file: /usr/lib/python2.5/site-packages/elisa/plugins/poblesec/base/styles.conf
WARNING:root:Cannot find resource file: /usr/lib/python2.5/site-packages/elisa/plugins/poblesec/base/resources.conf
WARNING:root:Cannot find theme configuration files
WARN  MainThread      pigment_frontend            okt. 04 15:16:24  exception importing decorator elisa.plugins.favorites.controller:music_decorator:
failure <type 'exceptions.ImportError'> at elisa/plugins/favorites/controller.py:55: <module>(): No module named shoutcast.models (elisa/plugins/pigment/pigment_frontend.py:200)

---

### Post by olavjunior on 2008-10-04
Yea, I've already tried that one (removing .elisa)

But what do I do to fix the site-package mess?

---

### Post by plun on 2008-10-04
> **olavjunior said:**
> Yea, I've already tried that one (removing .elisa)

But what do I do to fix the site-package mess?

Viking trick...:D

```
sudo apt-get remove --purge elisa*
```

```
gksudo nautilus
```

/usr/lib/python2.5/site-packages/


Delete all Elisa site packages

Install again...

Perhaps not in the noble art of Linux school....:D

---

### Post by olavjunior on 2008-10-04
Well, did it, but the site-packages didn't get recreated when installing elisa! Now I get this error:
```
junior@junior-laptop:~$ elisa
Traceback (most recent call last):
  File "/usr/bin/elisa", line 222, in <module>
    main()
  File "/usr/bin/elisa", line 199, in main
    options = _parse_options(sys.argv)
  File "/usr/bin/elisa", line 104, in _parse_options
    from elisa.core.options import Options
ImportError: No module named elisa.core.options

```

Little ruff that viking trick;)

EDIT: Forget it, I used reinstall from Synaptic, and now the packages got reinstalled. But still, the same problem... :(

Do you have the file /usr/lib/python2.5/site-packages/elisa/plugins/poblesec/base/resources.conf? I don't..

---

### Post by plun on 2008-10-04
Well....

Have you done uninstall from your svn folders  ?

As I wrote SVN often causes a complete mess.

The "viking trick" then often works...:D

You can also take a look at Elisas forum..

[http://elisa.fluendo.com/forums/](http://elisa.fluendo.com/forums/)

---

### Post by olavjunior on 2008-10-04
well, the svn is just in my home folder. Didn't think that could mess things up. But maybe I'll just have to try. Or wait.. :) I guess the Elisa team will release the newest version in Intrepid repos soon. 

I know the Elisa forums, but they're so slow... But thanks for trying to help me plun, appreciated! You don't know anything about this by any chance? :p [http://ubuntuforums.org/showthread.php?t=937257](http://ubuntuforums.org/showthread.php?t=937257)

---

### Post by plun on 2008-10-04
Elisa....:KS

```
locate elisa
```

[http://elisa.fluendo.com/forums/viewtopic.php?id=677](http://elisa.fluendo.com/forums/viewtopic.php?id=677)


---------------------------------------------

I think your other issue is something with lack of detection.

File a bug against Xorg

I also cannot see what graphic driver you are running. (just a quick look at the other thread.)

---

### Post by olavjunior on 2008-10-04
ok, thanks again! i don't know my driver, but it's 
  * Graphics card: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
anyways, another thread...

---

### Post by olavjunior on 2008-10-21
I'm still having this issue with Elisa! I've purge removed all affected packages and reinstalled them all! Don't tell me I'm the only one with intrepid having this issue????

---


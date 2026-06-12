---
title: "Problem with Elisa 0.5.2 install..."
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by kmullinax on 2008-07-28
Ok, so I just can't leave well enough alone and went back to trying to install 0.5.2 on Ubuntu.
I've successfully tacked a few of the issues that have come up, but now I'm stuck here:

WARN  MainThread      interface_controller        Jul 28 08:09:41  creating frontend frontend1 failed. A full traceback can be found at [Failure instance: Traceback: <type 'exceptions.ImportError'>: cannot import name ticker
/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py:216:simulate
/usr/lib/python2.5/site-packages/twisted/internet/base.py:561:runUntilCurrent
/usr/lib/python2.5/site-packages/twisted/internet/task.py:236:_tick
/usr/lib/python2.5/site-packages/elisa-0.5.2-py2.5.egg/elisa/core/interface_controller.py:104:load_frontends_iter
--- <exception caught here> ---

I've verified that I have the latest version of ticker.py installed in /usr/share/pycentral/pympd/site-packages/pympd/modules/ but for some reason I still get the "cannot import name ticker" issue.

Does anyone have any ideas?

---

### Post by Partyboi2 on 2008-07-28
If you are using hardy why not install Elisa 0.3.5 which is in the ubuntu repo's

---

### Post by kmullinax on 2008-07-28
I had 3.5 installed, but was having all kinds of issues with cover art being pulled incorrectly from Amazon.  I tried updating the art in the amazon_cache, but the art in Elisa just won't update.  Plus there's no way in 3.5 to fast-forward through movies without clicking on the progress bar and that tends to be really buggy.  I can't ever seem to get the movie to go to the point where I last was watching it.
Anyway, I'm trying to install 5.2 in hopes that those problems were solved.  As it is, 3.5 isn't really usable for what I do with it.

---

### Post by Partyboi2 on 2008-07-28
Have you got all the dependencies installed that are mentioned in the readme file?

---

### Post by kmullinax on 2008-07-28
yep.
i just went through and swept my computer of all elisa files and then tried to do a clean install of version 0.5.3 which was released today but it froze in the same spot -- trying to load "ticker"

---

### Post by rgsteele on 2008-07-29
Are you using the version in the repository or the tarball?

I'm using the repository version, and I was getting the same error.  I figured out that the svn version of Pigment I was using wasn't getting updated properly. (I think pigment and pigment-python used to be in two separate repositories, and at some point they were merged.) So the solution for me was to delete my Pigment directory, and do a fresh copy of Pigment from svn:
```
svn co https://code.fluendo.com/pigment/svn/trunk pigment
```

Just to confirm, do you have Pigment installed permanently? If you don't, you need to run ./pigment/pigment/misc/pgm-uninstalled before you run Elisa. The "cannot import name ticker" error refers to a file in the pigment-python library.

Hope this helps!

---

### Post by kmullinax on 2008-07-29
Thank you!
Now I'm getting somewhere... I re-installed pigment per your instructions and started it via the command line, then launched Elisa.

It *almost* made it!!

I got to the main screen and then it crashed with a fatal error... this time it said: 
Elisa failed to initialize: [Failure instance: Traceback: <type 'exceptions.TypeError'>: <__main__.PgmGlViewport object (pgmglviewport0) at 0x1ec4a00>: unknown signal name: update-pass

Any ideas?

---

### Post by rgsteele on 2008-08-02
I'm thinking maybe the tarball version of Elisa may be incompatible with new versions of Pigment, but that's just a guess. (From what I gleaned from a Google search the update-pass signal is a new addition to Pigment.)

You might want to try the repository version of Elisa. You can get it with this command:

```
bzr branch lp:elisa
```

---


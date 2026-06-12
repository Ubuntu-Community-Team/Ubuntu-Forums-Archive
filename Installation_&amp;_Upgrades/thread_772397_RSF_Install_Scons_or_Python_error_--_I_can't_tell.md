---
title: "RSF Install: Scons or Python error -- I can't tell"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by cengelsma on 2008-04-28
I just did a fresh install of Hardy so I've been in the arduous task of reinstalling everything.  I've been trying to install Madagascar ([http://rsf.sourceforge.net](http://rsf.sourceforge.net)) because I use it for seismic processing and digital signal analysis.  On Gutsy, everything configured and constructed fine, but I'm getting a strange error with the installation this time around.

I first tried to configure and make; make install and the configure and make worked, then make install threw a permission denied error so I had to re-run everything as sudo.  Now, when I try to configure, make or make install it gives me this error:

```
chris@chris-laptop:~/Desktop/madagascar-0.9.5$ sudo ./configure
Checking for Python ... /usr/bin/python
Checking for RSFROOT ... /usr/local/rsf
Checking for SCons ... /usr/bin/scons
Running /usr/bin/scons  config...
------------------------
scons: Reading SConscript files ...
ValueError: invalid literal for int() with base 10: '0d20071203':
  File "/home/chris/Desktop/madagascar-0.9.5/SConstruct", line 4:
    import configure
  File "/home/chris/Desktop/madagascar-0.9.5/configure.py", line 6:
    version = map(int,string.split(SCons.__version__,'.'))
------------------------
Done with configuration.

```

I'm not sure if this is a Scons error or a Python error, I believe everything is up-to-date.  How do I tackle this?

---


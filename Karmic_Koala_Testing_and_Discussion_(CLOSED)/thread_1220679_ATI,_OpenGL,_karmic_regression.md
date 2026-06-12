---
title: "ATI, OpenGL, karmic regression?"
date: 2009-07-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Hobbes on 2009-07-23
Hello all,

I am using an ATI Radeon 9800. I know it's a little old but from my limited research I think it should support OpenGL 2.0 just fine.  I am trying to play a game called "Heroes of Newerth" ([http://www.beta.heroesofnewerth.com/](http://www.beta.heroesofnewerth.com/)), but when I run it it says "OpenGL 2.0 not supported."

The output of "glxinfo | grep OpenGL" is: 
```
glxinfo | grep OpenGL
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.4 Mesa 7.5
OpenGL extensions:

```

and "radeontool --debug" gives:
```
Found card 1002:4e48 (30000)
  (unknown card)
mapping ctrl region
```

I think it should be an _r350_ card (though not 100% this would show up).. but I seem to remember it identifying correctly in the past.  The good news is that compiz and everyday stuff works, so it is not life and death :)

Any ideas?

---

### Post by lean on 2009-07-23
You should use the (closed) fglrx driver to get OpenGL 2.0

---

### Post by Seren on 2009-07-23
> **lean said:**
> You should use the (closed) fglrx driver to get OpenGL 2.0

r300 to r500 are no longer supported by fglrx, so it is not an option. You would need to downgrad to intrepid IIRC.

The status regarding the free driver can be found here :
[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

For OpenGL2.0, it is defined as WIP (work in progress). So I am not sure if it should work or not.

---

### Post by Hobbes on 2009-07-23
@lean: yeah, not only is there not an fglrx driver for 2.6.31 yet (that i know of), but also my card I believe is no longer supported by the driver, like Seren says :(

Thanks for the link, like you said it's a little hard to follow but looks like OpenGL 2.0 may not be finished for r300.  Too bad :(

---

### Post by shakaran on 2009-07-23
Yeah, same for me. Before with 7.5rc4 I have OpenGL 2.0 support, now not. And glxgears runs in fullscreen mode by default? not it a windows as before.

```
$ radeontool --debug
Found card 1002:5462 (30000)
  (unknown card)
mapping ctrl region

```

```
$ glxinfo | grep OpenGL
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX/SSE2 TCL
OpenGL version string: 1.4 Mesa 7.5
OpenGL extensions:
```

I have ATI Mobility Raden X600 (rv380) is a graphic card for laptop.

---

### Post by Primefalcon on 2009-07-24
I am using an x1300 and though I am only using jaunty the free driver (which I am using) is perfectly capable....

I look froward to using an even later version of it, but unfortunately I am hesitant to upgrade yet due to my machine having to be fairly reliable due to being a work machine (I accept it's not as stable as an LTS but standard releases are fairly rock solid anyhow).

The one question I do have though is regarding the ext4 file system I trialed that for a little while and it was pretty unstable cause crashes often under jaunty, will this be different since ext4 will be default on karmic?

---


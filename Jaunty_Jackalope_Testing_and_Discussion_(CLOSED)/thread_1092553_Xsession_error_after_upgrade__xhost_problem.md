---
title: "Xsession error after upgrade  xhost problem"
date: 2009-03-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nyarnon on 2009-03-10
I encounter the following error

.xsession-errors
```

/etc/X11/Xsession.d/60x11-localhost: 4: Syntax error: Bad fd number

```

contents of that file:

60x11-localhost
```

# This file is sourced by Xsession(5), not executed.

[ -x /usr/bin/xhost ] && [ -x /usr/bin/id ] &&
    xhost +si:localuser:`id -un` >& /dev/null

```

after moving that into a tmp dir everything boots as it should.
Can it be removed fd is probably a file descriptor?

---

### Post by tawmas on 2009-03-10
I just had the same problem.

As you guessed, fd stands for file descriptor. The syntax >& which appears in the last line (line 4) is wrong. I believe it should be something like >1&2 or such some. I solved that by editing the & out, i.e. the line now reads:

```
xhost +si:localuser:`id -un` > /dev/null
```

I checked with my nightly backup, and this file is new. It looks like what it does is to allow your user to connect to the X server, so I'm not sure it can be safely removed.

Right now, I'm without compiz, btw. I have no idea if that's related or not.

---

### Post by Technoviking on 2009-03-10
Same here.

---

### Post by Technoviking on 2009-03-10
Reported bug.

[https://bugs.edge.launchpad.net/ubuntu/+source/xorg-server/+bug/340730](https://bugs.edge.launchpad.net/ubuntu/+source/xorg-server/+bug/340730)

---

### Post by nick_stokie on 2009-03-10
..+1 but then seems to have been fixed for me by an update in the last five minutes

(as tawmas suggested in post 2, the '&' has been removed)

---

### Post by tawmas on 2009-03-10
> **Technoviking said:**
> Reported bug.

[https://bugs.edge.launchpad.net/ubuntu/+source/xorg-server/+bug/340730](https://bugs.edge.launchpad.net/ubuntu/+source/xorg-server/+bug/340730)

I've confirmed it. Seems like the kind of problem that will get solved quickly.

---

### Post by nyarnon on 2009-03-10
@tawmas

I figured as much after man xhost, but I do not notice any effect of leaving the file out. Lets wait and see.

---

### Post by tawmas on 2009-03-10
> **nick_stokie said:**
> ..+1 but then seems to have been fixed for me by an update in the last five minutes

(as tawmas suggested in post 2, the '&' has been removed)

Cool! :-) I had just updated, so they were extra-quick to catch this one! :-)

I'm now downloading the new updates. I see x11-common in there, so I believe the fix is indeed in there.

---

### Post by captive on 2009-03-10
Yes it seems to be fixed. I solved it putting 
```
#!/bin/bash
```
instead of
```
#!/bin/sh
```
in /etc/gdm/Xsession

---

### Post by Technoviking on 2009-03-10
Fix here with latest updates.

---

### Post by nick_stokie on 2009-03-10
what's the current record for the time between reporting and fixing a bug? This must come pretty close?

;)

---

### Post by tawmas on 2009-03-10
> **nick_stokie said:**
> what's the current record for the time between reporting and fixing a bug? This must come pretty close?

;)

I think this one got fixed before being reported, so the new record is a negative time. Difficult to beat in future! ;-)

I'm going to close the LP bug.

... and then back to fixing my broken compiz. :-( If I could only recall what directories I need to delete to zap my configuration and start anew...

EDIT: I see you've already done that! :-D

---

### Post by nyarnon on 2009-03-10
Thats it, that was the last time I updated through synaptic. Twice on one day is enough. :-)

---


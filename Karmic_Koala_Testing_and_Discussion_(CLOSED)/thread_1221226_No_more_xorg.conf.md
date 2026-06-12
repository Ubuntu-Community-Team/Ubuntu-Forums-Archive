---
title: "No more xorg.conf"
date: 2009-07-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tahina on 2009-07-23
I just noticed that xorg.conf is nowhere to be found. IIRC it used to be in /etc/X11/

Did this just happen today or have I missed something? 

The thing is, I thought I'd have a look at this UXA thing I've been hearing about. How can I tell if I have UXA or EXA or whatever? If I don't have UXA, could I just pop an xorg.conf with just the relevant section in it into /etc/X11 ?

---

### Post by wayne_cat on 2009-07-23
If no xorg.conf file is present , Xorg will probe the system to autoconfigure itself. You can run:
```

 Xorg -configure 
```to generate an initial xorg.conf  ... copy it to /etc/X11 ... change your settings ... done

---

### Post by mariner09 on 2009-07-23
The latest 2.6.31 kernel in Alpha 3 is supposed to have UXA by default...

[http://www.ubuntu.com/testing/karmic/alpha3](http://www.ubuntu.com/testing/karmic/alpha3)

---

### Post by tahina on 2009-07-23
Cool. Thanks. Both of you.

---

### Post by RAOF on 2009-07-23
> **mariner09 said:**
> The latest 2.6.31 kernel in Alpha 3 is supposed to have UXA by default...
...

More accurately, for much of the Karmic development cycle, the xserver-xorg-video-intel drivers (all from the 2.7.xxx series) haven't supported anything *but* UXA.

---

### Post by MattFinck21 on 2009-08-15
i was missing my xorg.conf too, i ran ```
Xorg -configure
```from root shell prompt in the "recovery mode"

it said somthing like "New configuration saved in /root/org.conf.new"

now, i just copied that file to /etc/X11 as xorg.conf, that should sove the missing xorg.conf right?

---

### Post by dagrump on 2009-08-15
Man, knew I should of paid the renewal on my Psychics union card.
 What problem?

---

### Post by psyke83 on 2009-08-15
> **tahina said:**
> I just noticed that xorg.conf is nowhere to be found. IIRC it used to be in /etc/X11/

Did this just happen today or have I missed something? 

The thing is, I thought I'd have a look at this UXA thing I've been hearing about. How can I tell if I have UXA or EXA or whatever? If I don't have UXA, could I just pop an xorg.conf with just the relevant section in it into /etc/X11 ?

For some time Xorg has been capable of running without a configuration. Recent versions of Ubuntu shipped with a "bare" configuration (just the Sections defined, with nothing really substantial defined within them), but it seems that for Karmic this file is being phased out.

EXA support in the intel driver is completely dead and buried now. The version of the intel driver in Karmic has no support for XAA, EXA or DRI1 at all. There is just UXA and DRI2.

You can view the Xorg.0.log in the Log Viewer or check for UXA via:
```
$ cat /var/log/Xorg.0.log | grep -i uxa
```

---

### Post by Skraut on 2009-08-18
Ok, so what's the best way to adjust the monitor settings?  I'm trying to enable dual head using xrandr, and getting the "xrandr: screen cannot be larger than:" error.

The solution according to the xrandr wiki is to edit the virtual line of the xorg.conf.  Should I go ahead and create one and edit it, or is there a new way of achieving this that doesn't require an xorg.conf?

---

### Post by fifth on 2009-08-18
> **psyke83 said:**
> For some time Xorg has been capable of running without a configuration. Recent versions of Ubuntu shipped with a "bare" configuration (just the Sections defined, with nothing really substantial defined within them), but it seems that for Karmic this file is being phased out.

EXA support in the intel driver is completely dead and buried now. The version of the intel driver in Karmic has no support for XAA, EXA or DRI1 at all. There is just UXA and DRI2.

You can view the Xorg.0.log in the Log Viewer or check for UXA via:
```
$ cat /var/log/Xorg.0.log | grep -i uxa
```

Ok so does ...

```
chris@black-lap:~$ cat /var/log/Xorg.0.log | grep -i uxa
(II) UXA(0): Driver registered support for the following operations:

```

... mean I'm not getting UXA?

---

### Post by amano on 2009-08-18
The Intel driver only uses UXA. There is no support for EXA left anymore thus it cannot be forced via xorg.conf.

---

### Post by psyke83 on 2009-08-18
> **Skraut said:**
> Ok, so what's the best way to adjust the monitor settings?  I'm trying to enable dual head using xrandr, and getting the "xrandr: screen cannot be larger than:" error.

The solution according to the xrandr wiki is to edit the virtual line of the xorg.conf.  Should I go ahead and create one and edit it, or is there a new way of achieving this that doesn't require an xorg.conf?

The intel driver now only supports a virtual size of 2048x2048. However, I believe that for 9xx hardware and later, the limit has been extended to 4096x4096 (but it may need a more recent version of the driver, in the Xorg-edgers repository, for example).

---


---
title: "I have no 3D anything :["
date: 2005-03-01
forum: Installation &amp; Upgrades
---

### Post by ixus_123 on 2005-03-01
after multiple installs I have finally got my system as I like it, well almost - I have no trace of any £D features.  £D plugins in xmms don't work & all my 3D screen savers are greyed out (Gears et al)

It's not a huge concern but I did quite like some of those savers

Any ideas?

---

### Post by Slapdash on 2005-03-01
I am no expert but recon its a driver issue.
Try Apt-Get / Synaptic and search for nvidia/ATI to install.

---

### Post by ixus_123 on 2005-03-01
nvidia driver is installed

---

### Post by p!=f on 2005-03-01
What you get by running this command?
```

[~] > glxinfo | grep direct
direct rendering: Yes

```

---

### Post by ixus_123 on 2005-03-01
bash: direct: command not found

?

---

### Post by p!=f on 2005-03-01
[QUOTE=ixus_123]bash: direct: command not found

?[/QUOTE]
You must have a typo there or you did not use the grep command. Are you sure you wrote it exactly as above?

---

### Post by ixus_123 on 2005-03-01
yep just the first line gave me a file I can't open, the second line give the  error

I tried them separately & both together copied & pasted

---

### Post by ixus_123 on 2005-03-01
Oh, I just tried it again with out the  < 

I got this:

```
kieren@ubuntu:~ $ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
kieren@ubuntu:~ $ direct rendering: Yes
```

---

### Post by ixus_123 on 2005-03-02
Where do i go from there?  I'm in new learning territory now :)

---

### Post by p!=f on 2005-03-02
What's your graphic card?
What driver does your XFree86 / Xorg use?
```

[~] > grep -i driver /etc/X11/xorg.conf
        Driver          "keyboard"
        Driver          "mouse"
        Driver          "nvidia"
        #Driver         "nv"

```
(note that [~] > is my bash prompt (do not paste :)), replace xorg.conf with X86Config-4 if you're on Warty)

---

### Post by ixus_123 on 2005-03-02
My graphics card is a 32mb Nvidia - I couldn't tell you the model no - it's about 5 years old though

```
:~ $ grep -i driver /etc/X11/XF86Config-4
        Driver          "keyboard"
        Driver          "mouse"
        Driver          "nv"
kieren@ubuntu:~ $
```

---


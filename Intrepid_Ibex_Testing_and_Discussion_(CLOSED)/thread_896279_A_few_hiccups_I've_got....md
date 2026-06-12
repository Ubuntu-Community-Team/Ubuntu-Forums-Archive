---
title: "A few hiccups I've got..."
date: 2008-08-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by SomeGuyDude on 2008-08-21
Maybe some of these aren't new, but since I'm hitting them all at once...

1) Compiz doesn't work whatsoever. Attempting to start it causes a big bug-out:

```
crew@crew-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

2) Maybe related, but opening things (anything) makes the screen flicker like crazy.

3) I have no splash screen now.

4) Network Manager took a few tries to recognize my WEP hex key. Like, four tries.

That's what I noticed just in my first 10 minutes. I know about the shutdown/logout thing, but those struck me as slightly odd.

There are some good things, too. For example my WiFi LED works again. But this is really damn annoying. Even Hardy's alpha was working better by this point, just sluggish.

---

### Post by RAOF on 2008-08-21
> **SomeGuyDude said:**
> ...
1) Compiz doesn't work whatsoever. Attempting to start it causes a big bug-out:

```
crew@crew-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

That is the output for a successful compiz startup.  What makes you think Compiz isn't working? :)

---

### Post by klange on 2008-08-21
> **SomeGuyDude said:**
> Maybe some of these aren't new, but since I'm hitting them all at once...

2) Maybe related, but opening things (anything) makes the screen flicker like crazy.


I assume you have an Intel system?
That's a known (upstream) bug that's supposed to be fixed sometime soon.

Usplash has had problems with uvesafb since the beginning, guess they haven't been fixed.

NetworkManager 0.7 still has some bugs that need to be fixed.

---

### Post by SomeGuyDude on 2008-08-21
> **RAOF said:**
> That is the output for a successful compiz startup.  What makes you think Compiz isn't working? :)

Ah, I'm an idiot. It just erased all my settings for some reason. I was confused.

And yes, Intel graphics card.

---

### Post by Rotarychainsaw on 2008-08-30
I just upgraded as well, and the screen flickering is pretty annoying. Is it both drivers that are affected (intel/i810)? I forget which one I use. . .

---

### Post by jfernyhough on 2008-08-30
A trick I've used to get wireless networks to work again is to remove the entry from "Edit Connections..." When you connect again it will prompt for the key again but this time it should stick. It sounds like something to do with the keyring manager, a permission or similar.

---


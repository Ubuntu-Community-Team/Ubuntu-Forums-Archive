---
title: "Not displaying movie video in Totem."
date: 2009-08-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Locke_99GS on 2009-08-26
Ok, I feel like the noob. I'm on Karmic, fully updated of course. I have all the gstreamer plugins and all the stuff from Medibuntu, and when I play a video encoded in DivX5 or Quicktime (can't test with others) with Totem I usually get audio but never video. Sometimes Totem hangs, and it usually it won't quit. The window closes, but the process still exists.

This all worked fine in Jaunty. Any ideas, or something I'm missing? I've never had an issue like this, and I'm not finding relevant information when searching.

I haven't tried playing them in VLC yet.

edit: Just installed VLC 1.0.1 from the repos with a resulting fat NO-GO. Same issue, no video but do have audio.


Thanks in advance.

---

### Post by taavikko on 2009-08-26
test with
```
gstreamer-properties
```
On video tab, does the test show anything (varying output-module)?

Also the GPU would be nice extra info.

---

### Post by nystire on 2009-08-26
What video drivers are you running? And what output plugins are you using?

---

### Post by Locke_99GS on 2009-08-26
gstreamer-properties test shows a blank black box, but it doesn't freeze.

nvidia drivers 185.18-36 on a 9500gt.

---

### Post by taavikko on 2009-08-26
> **Locke_99GS said:**
> gstreamer-properties test shows a blank black box, but it doesn't freeze.

nvidia drivers 185.18-36 on a 9500gt.

Has the module been properly builded?
```
dkms status
```

---

### Post by Locke_99GS on 2009-08-26
```

locke@Pimpshit:~$ dkms status
nvidia, 185.18.36, 2.6.31-5-generic, x86_64: installed 
nvidia, 185.18.36, 2.6.31-7-generic, x86_64: installed 

```

Appears so. 

I did notice from gstreamer-properties the following output:

```

locke@Pimpshit:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

```

Though, it doesn't seem as though any of those plugins have anything to do with my issue.

---

### Post by Locke_99GS on 2009-08-26
You can see in this first screenshot Totem in the background and gstreamer foreground set to autodetect.

[ATTACH]126342[/ATTACH]



I did discover that by switching the gstreamer output plugin to "No Xv" that I get video output. So it is not autodetecting properly? Hmmm..

[ATTACH]126343[/ATTACH]

---

### Post by Locke_99GS on 2009-08-26
And, one last update;

Setting gstreamer to "No Xv" worked, though I am still curious as to why the "autodetect" setting didn't function correctly. Thats where I had left it in previous releases of Ubuntu.

Also, setting VLC to using anything other than XVideo output worked fine. I have it on X11 right now.


Any ideas as to why I had to configure this myself?

---


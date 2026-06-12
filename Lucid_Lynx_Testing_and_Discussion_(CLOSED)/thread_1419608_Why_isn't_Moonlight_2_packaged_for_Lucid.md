---
title: "Why isn't Moonlight 2 packaged for Lucid?"
date: 2010-03-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Keyper7 on 2010-03-02
Just curious. There wasn't time to do it before the freeze or is there some other reason?

I was very excited when 2.0 was released and thought I'd see it in the Lucid repositories...

---

### Post by david_ on 2010-03-02
You can easily install it as firefox extension: [http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

---

### Post by Keyper7 on 2010-03-02
> **david_ said:**
> You can easily install it as firefox extension: [http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

Thanks, but I know that. That was not my question.

---

### Post by philinux on 2010-03-02
> **Keyper7 said:**
> Just curious. There wasn't time to do it before the freeze or is there some other reason?

I was very excited when 2.0 was released and thought I'd see it in the Lucid repositories...

It's been requested to be packaged. Status = wishlist.
[https://bugs.launchpad.net/ubuntu/+bug/374990](https://bugs.launchpad.net/ubuntu/+bug/374990)

---

### Post by Keyper7 on 2010-03-02
> **philinux said:**
> It's been requested to be packaged. Status = wishlist.
[https://bugs.launchpad.net/ubuntu/+bug/374990](https://bugs.launchpad.net/ubuntu/+bug/374990)

Didn't find that, seems like my Google-fu is weak. Thanks, philinux.

---

### Post by philinux on 2010-03-02
> **Keyper7 said:**
> Didn't find that, seems like my Google-fu is weak. Thanks, philinux.

Lol. google-fu = ubuntu moonlight package request

---

### Post by Keyper7 on 2010-03-02
> **philinux said:**
> Lol. google-fu = ubuntu moonlight package request

Tried all those words, except "request". Turns out it was the key. :)

---

### Post by castrojo on 2010-03-02
I always do a tag search for "needs-packaging" when looking for something like this. For debian search for "wnpp" or "ITP".

---

### Post by gnomeuser on 2010-03-02
To me, and I know a lot of people, while Moonlight is extremely welcome and a great project so long as there is only support for Firefox it is of limited use.

Luckily our wonderful upstream are reportedly working on that.

---

### Post by emarkay on 2010-03-02
Yea, another "official" package requested to be added to the bloat,  that does not increase stability, security or productivity at all.

Whatever happened to the good old days of Linux?

---

### Post by Merk42 on 2010-03-02
> **emarkay said:**
> Yea, another "official" package requested to be added to the bloat,  that does not increase stability, security or productivity at all.

Whatever happened to the good old days of Linux?

I'm pretty sure Ubuntu isn't the only Linux distribution

I'm also going to guess that Moonlight is, for a lack of a better word, a Linux equivalent to a Microsoft product is the basis for your issue with its being an official package.

---

### Post by 23meg on 2010-03-02
> **emarkay said:**
> Yea, another "official" package requested to be added to the bloat,  that does not increase stability, security or productivity at all.

* sigh *

The packaging request is about adding an LGPL package to the Universe component. Nothing to do with defaults. If you don't care about Moonlight, its presence in Universe doesn't affect you in any way.

---

### Post by Ibidem on 2010-03-02
There is one advantage (from an end-user's perspective) to installing from upstream: If you install from Novell, it comes with several proprietary (MS) codecs, which cannot be redistributed.   (If you don't consider that an advantage, why use Moonlight at all? )

FWIW, Novell provides an installer for Ubuntu (Karmic).

What could be packaged is only the open-source portion (LGPL).

---

### Post by zekopeko on 2010-03-02
> **emarkay said:**
> Yea, another "official" package requested to be added to the bloat,  that does not increase stability, security or productivity at all.

Whatever happened to the good old days of Linux?

We moved to the future of Linux, leaving in dust various dinosaurs to do what they do best. Extinct on a massive scale leaving room for critters that are better adapted to the new environment.

---

### Post by zekopeko on 2010-03-02
> **Ibidem said:**
> There is one advantage (from an end-user's perspective) to installing from upstream: If you install from Novell, it comes with several proprietary (MS) codecs, which cannot be redistributed.   (If you don't consider that an advantage, why use Moonlight at all? )

FWIW, Novell provides an installer for Ubuntu (Karmic).

What could be packaged is only the open-source portion (LGPL).

It can be linked to ffmpeg or possibly gstreamer. The upside to MS codecs is that they are legal to download and use in the backward nations that have software patents.

---

### Post by Keyper7 on 2010-03-03
> **zekopeko said:**
> I can be linked to ffmpeg or possibly gstreamer.

Exactly, the version in the Karmic repositories uses ffmpeg. Gstreamer would be even better.

---


---
title: "A fault in ImageMagick or maybe the image is bad?"
date: 2009-03-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by moma on 2009-03-25
Hello,

[Could you please verify this error on your 32 or 64bits Ubuntu (Jackalope). Requires you to install "imagemagick" package first.]

I am playing with my Gscreendump app and I found an image that causes ImageMagick to crash.
These are the commands I run:

# Get the base image
[COLOR="Green"]wget [http://www.edbl.no/tmp/header.gif](http://www.edbl.no/tmp/header.gif)[/COLOR]

# Convert it to png
[COLOR="Green"]convert header.gif image1.png[/COLOR]

# Rotate 45 degrees
[COLOR="Green"]convert image1.png -rotate 45 image2.png[/COLOR]

Error:
[COLOR="Red"]convert: magick/memory.c:452: CopyMagickMemory: Assertion `destination != (void *) ((void *)0)' failed.
[/COLOR]
The same error happens when I call
MagickRotateImage(image, background, angle);
from c code. The code is [here...]("http://code.google.com/p/gscreendump/source/browse/trunk/src/sd_imagemagick.c") [look for magickwand_rotate_image() function].
---------------
I generated the image1.png by drag & dropping the "header.gif" image to my Gscreendump application.
Read about the amazing Gscreendump here
[http://ubuntuforums.org/showthread.php?t=1096860](http://ubuntuforums.org/showthread.php?t=1096860)
and
[http://code.google.com/p/gscreendump/](http://code.google.com/p/gscreendump/)
You can save_as or import images to any format (PDF files, PNG, etc....), thanks to ImageMagick.
---------------

EDIT: The operatingsystem where this error occurs is
[COLOR="Green"]cat /etc/*issue*[/COLOR]
Ubuntu Linux 9.04 (64bits) Jaunty Jackalope (development branch, [alpha6...]("http://www.ubuntu.com/testing/jaunty/alpha6"))

[COLOR="Green"]convert -version[/COLOR]
Version: ImageMagick 6.4.5 2009-01-22 Q16 OpenMP [http://www.imagemagick.org](http://www.imagemagick.org)
Copyright: Copyright (C) 1999-2008 ImageMagick Studio LLC
---------------

EDIT: The same test on 64bits Ubuntu 8.10.
The above commands work well (without errors) in 64bits Ubuntu 8.10. The ImageMagick version is
[COLOR="Green"]mogrify -version[/COLOR]
Version: ImageMagick 6.3.7 08/21/08 Q16 [http://www.imagemagick.org](http://www.imagemagick.org)
Copyright: Copyright (C) 1999-2008 ImageMagick Studio LLC
----------------

See also: [http://www.imagemagick.org/discourse-server/viewtopic.php?f=3&t=13410](http://www.imagemagick.org/discourse-server/viewtopic.php?f=3&t=13410)

---

### Post by taavikko on 2009-03-25
confirm on 32bit Jaunty.


While using graphicsmagick the rotate works
```
gm convert image1.png -rotate 45 image2.png
```

---

### Post by moma on 2009-03-25
Hello,

Kiitos. Thanks for your confirmation.

The ImageMagick team reports that they have a patch for this error.
Read their answer on [http://www.imagemagick.org/discourse-server/viewtopic.php?f=3&t=13410&p=45198#p45198](http://www.imagemagick.org/discourse-server/viewtopic.php?f=3&t=13410&p=45198#p45198)

Let's hope the patch makes its way to Ubuntu 9.04 very soon.

---

### Post by moma on 2009-03-28
Hello,

I just discovered that the current ImageMagick version in Jauntu is 6.4.5. It is BUGGY and HOPLESSLY old. 

Ubuntu users have hard time when participating on the ImageMagick forums because Ubuntu's IM version is ancient, old and relatively buggy. People don't want to suppport old, buggy versions!

Take a look at this ChangeLog list.
[http://trac.imagemagick.org/browser/ImageMagick/branches/ImageMagick-6.5.0/ChangeLog](http://trac.imagemagick.org/browser/ImageMagick/branches/ImageMagick-6.5.0/ChangeLog)

It shows that Jaunty's ImageMagick is around 80+ patches and releases behind the latest version.

[COLOR="Red"]Sorry to say this, but Ubuntu is practically useless for work with ImageMagick. 
[/COLOR]

---

### Post by stoffe on 2009-03-28
> **moma said:**
> Hello,
[COLOR="Red"]Sorry to say this, but Ubuntu is practically useless for work with ImageMagick. 
[/COLOR]

Maybe this is true for this particular release if it's an unlucky version with extra bugs, but seeing as I've put imagemagick to good use since 2000, 9 years back, I would say that calling it "useless" because it's old, based on a 0.0.5 minor version is a bit... odd.

---

### Post by nanomad on 2009-03-28
Bug report filled:
[https://bugs.launchpad.net/ubuntu/+source/imagemagick/+bug/350154](https://bugs.launchpad.net/ubuntu/+source/imagemagick/+bug/350154)

---


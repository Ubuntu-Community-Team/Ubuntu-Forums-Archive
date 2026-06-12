---
title: "brlcad, can't start framebuffer"
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by dwretman on 2010-10-30
Hi all,

I am posting this question here since I am not sure where it belongs.

I have installed brlcad on my ubuntu, I did it from source and all was well. Now I am trying to follow the thin manual and it worked great to the point when it was time to render the object I created.

To do this I need to start a framebuffer server pointing to some /dev/sgip stuff, the ting is that my ubuntu do not have a /dev/sgip device. Is there anyone who knows what this is and if there is any device equal to this I can use?

BR
Daniel

---

### Post by brlcad on 2010-10-30
> **dwretman said:**
> Hi all,

I am posting this question here since I am not sure where it belongs.

I have installed brlcad on my ubuntu, I did it from source and all was well. Now I am trying to follow the thin manual and it worked great to the point when it was time to render the object I created.

The question is probably more appropriate for the BRL-CAD user [mailing list]("https://sourceforge.net/mail/?group_id=105292") [1] but I'll be happy to respond here.  First off, the "thin" manual you're working off of is not the best starting resource.  There is considerably better documentation including an extensive 16-part tutorial series and a quick reference mged command sheet on the [website]("http://brlcad.org/wiki/Documentation") [2].  That's more than 400+ pages of documentation that just scratch the surface of what all is possible with BRL-CAD. 

[1] [https://sourceforge.net/mail/?group_id=10529](https://sourceforge.net/mail/?group_id=10529)
[2] [http://brlcad.org/wiki/Documentation](http://brlcad.org/wiki/Documentation)

> **dwretman said:**
> To do this I need to start a framebuffer server pointing to some /dev/sgip stuff, the ting is that my ubuntu do not have a /dev/sgip device. Is there anyone who knows what this is and if there is any device equal to this I can use?

You don't need to specify a framebuffer device.  Leave off the -F/dev/sgip altogether.  It will use a default framebuffer.  The 'fbhelp' command (outside of mged) lists your framebuffer devices.

Cheers!
Sean

---

### Post by dwretman on 2010-10-31
Thanks allot :popcorn:
Daniel

---


---
title: "sudoers permissions stopped working?"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by David Tomic on 2009-10-01
Hi all,

For a long time now I've had my /etc/sudoers file configured so that I don't get prompted for a [sudo] password when I'm switching between PPP connections.

```
# Cmnd alias specification
Cmnd_Alias PPP =  /usr/bin/pon, /usr/bin/poff
```

This has never given me any problems, until tonight when it's suddenly started prompting me for passwords again.

I've even tried adding /usr/bin/gedit to the list - just for the sake of testing - and that doesn't work either.

Does anyone have any clues why this would have suddenly stopped working, and more importantly, how I might be able to fix it again?

Thanks for your help ...

Regards,
--David

---


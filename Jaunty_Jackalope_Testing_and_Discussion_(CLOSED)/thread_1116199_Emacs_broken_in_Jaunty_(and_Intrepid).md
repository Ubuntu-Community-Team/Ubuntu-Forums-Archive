---
title: "Emacs broken in Jaunty (and Intrepid)?"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by gjb1002 on 2009-04-04
I'm trying to decide whether to take the plunge and upgrade my Hardy installation. Fortunately, I have Amazon's EC2 cloud to try things out on first...

Emacs doesn't work on either the Intrepid or Jaunty desktop instances there. I don't know if this is cloud-specific, I had trouble believing a Linux installation could really go six months with totally broken emacs...

It just says 'Undefined color: "black"' when I try to start it.
Now this seems to be some problem with "rgb.txt", which is indeed missing from /etc/X11 as various posts and bugs indicate. But just copying my Hardy file there doesn't help. In any case, there seems to be an rgb.txt file inside the emacs package, shouldn't it be using that?

Any tips gratefully appreciated. I'm too scared to upgrade my local computer while I fear that emacs will not work when I have...

---


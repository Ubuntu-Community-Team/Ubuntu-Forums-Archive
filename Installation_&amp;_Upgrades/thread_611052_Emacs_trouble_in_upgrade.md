---
title: "Emacs trouble in upgrade"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by dm215 on 2007-11-12
So my upgrade to Gutsy went pretty well, aside from a Firefox x86_64 issue which turned out to be fixable and now a problem migrating to emacs 22.

Fortunately, emacs 21 is still installed, even though the installer says it will remove it.  I say fortunately, because emacs 22 is not text highlighting anything, while emacs 21 still is, just as before.

I don't know if this has something to do with my .emacs file, which I don't really understand (I had it built by the customization macro within emacs 21), but the commands there all seem to have something to do with my color scheme.  I suspect this actually is the problem -- I may still have highlighting, but no color scheme whatsoever.

Anyway, I know this is really an emacs question, but since my gutsy upgrade is what got me here, I thought that somebody might have run across this as a particular ubuntu issue.  In any event, I haven't run across any problems of this sort on the emacs help boards, while here there is at least one similar problem:

[http://ubuntuforums.org/showthread.php?t=589753&highlight=gutsy+emacs](http://ubuntuforums.org/showthread.php?t=589753&highlight=gutsy+emacs)

By the way, the contents of my .emacs file is located at that link location, and the issue experienced by the OP in that post is not my problem: my emacs22/site-lisp and emacs21/site-lisp directories are identical (at least for a level or two).

Thanks,
-David

---


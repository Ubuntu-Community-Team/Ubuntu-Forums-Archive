---
title: "Gedit auto-indent behaviour changed?"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kareeser on 2010-03-21
So, the gedit auto-indent behaviour seems to have changed... ostensibly, "for the better", but not for me.

I tend to write code by writing from the outside in:
```
<?php
```
```
<?php

?>
```
```
<?php
#Some code...
?>
```

... instead of in a straight line, which cuts down on the amount of missing end-tags that I'm prone to do.

Except now, when I press enter twice after writing the first tag, the middle line no longer inherits the indent of the previous line, but instead, has no indentation whatsoever. Which leads to wasted time as I tab back to the previous position.

Gedit does this, I think, because it detected no text in the line, and assumed it was an empty line, and saved a couple bytes by not adding the indents, but it's a pain in the butt.

Anyone know how I can change it back?

---

### Post by 23meg on 2010-03-21
Edit > Preferences > Editor > Enable automatic indentation ?

---

### Post by Kareeser on 2010-03-21
*sigh*.

No. Not quite :)

The automatic indentation is carried over to the line I press enter until, but the previous lines don't have that indentation.

---

### Post by MacUntu on 2010-03-21
It's actually not a Gedit thing as Gedit doesn't implement the auto-indentation. What you are looking for is a change in the package gtksourceview2: [http://git.gnome.org/browse/gtksourceview/commit/?id=186127e1163236b365d658e7121684ccfa16c3c3](http://git.gnome.org/browse/gtksourceview/commit/?id=186127e1163236b365d658e7121684ccfa16c3c3)

You'd need to download the Ubuntu sources, undo those changes and recompile the thing.

---


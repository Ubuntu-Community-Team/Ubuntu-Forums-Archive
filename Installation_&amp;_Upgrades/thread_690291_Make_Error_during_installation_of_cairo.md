---
title: "Make Error during installation of cairo"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by ikak on 2008-02-07
Hey all,

Started installing Cairo and that because I want to check out cairo-dock(gnome-dock), so I went to the HOWTO on these forums for installing cairo-dock.  I installed all the libraries necessary like it shows in the HOWTO. Downloaded the cairo tarball, extracted it on my desktop.  In the Terminal I went into the cairo directory, typed in ./configure with all the parameters and such(basically just copy and pasted the command from the HOWTO).  No errors came up in the configuration. The next step is 'make' and I got the following error:

```
cairo-type1-subset.c:368: error: implicit declaration of function 'isspace'
make[2]: *** [cairo-type1-subset.lo] Error 1
make[2]: Leaving directory `/home/phill/Desktop/cairo-1.2.6/src'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/phill/Desktop/cairo-1.2.6/src'
make: *** [install-recursive] Error 1
```

I saw in some posts/threads, that I had to install cairo-clock, so I tried that, installed successfully but I still get this error. Thanks for the help.

---

### Post by Partyboi2 on 2008-02-08
Open up the cairo-type1-subset.c file
```
gedit /home/phill/Desktop/cairo-1.2.6/src/cairo-type1-subset.c file
```look for this:
> * Contributor(s):
 *    Kristian Høgsberg [EMAIL="krh@redhat.com"]<krh@redhat.com>[/EMAIL]
 */

#include "cairoint.h"
#include "cairo-scaled-font-subsets-private.h"
#include "cairo-output-stream-private.h"

/* XXX: Eventually, we need to handle other font backends */
#include "cairo-ft-private.h"

#include <ft2build.h>
#include FT_FREETYPE_H
#include FT_OUTLINE_H
#include FT_TYPE1_TABLES_H Its around line 40-46 then add #include <ctype.h>
so it will look like this:
> #include "cairo-ft-private.h"
**[COLOR=Red]#include <ctype.h>[/COLOR]**
#include <ft2build.h>
#include FT_FREETYPE_H
#include FT_OUTLINE_H
#include FT_TYPE1_TABLES_Hsave then run make again.

---

### Post by chinaliuxiaojun on 2008-02-10
ths for Partyboi2!
i have did as you said and it work correctly
i think i must say thinkful to you!

---

### Post by Partyboi2 on 2008-02-10
Glad it works :)

---


---
title: "Change /bin/sh in Edgy back to bash?"
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by SFDD on 2006-12-02
I'm having some script-running trouble with my company's product since upgrading to Edgy. I think I've figured out that it's a dash/bash issue. If I run the script using "sh.distrib" instead of "sh" it starts fine, but then dies when it spawns another script. (sh.distrib is pointing to bash and sh is now pointing to dash)

Two questions:

1. How do a redirect the "sh" link to bash?
2. If I do this, am I asking for trouble? Is there a "cleaner" way to do this  so that I can get this product going again?

Thank you!

---

### Post by SFDD on 2006-12-02
Okay, I read in another post how to change the symlink:

 rm -f /bin/sh
 ln -s /bin/bash /bin/sh

But the question remains: If I do this, can I expect other software that "knows" Edgy is using dash to break somehow? I'm sorry if this is a dumb question, but I'm not a Linux guru. I know just enough (after many complete reinstalls!) to not make any assumptions. ;)

Thanks!

---


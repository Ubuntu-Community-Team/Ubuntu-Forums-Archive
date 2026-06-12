---
title: "Latest Firefox updates break extensions"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by ktenney on 2008-07-25
Howdy,

Today's FF3 update has disabled many of my extensions
because they are considered incompatible.

Suggestions?

Thanks,
Kent

---

### Post by Partyboi2 on 2008-07-25
You could just wait till the extensions are updated. :)

---

### Post by ktenney on 2008-07-25
> **Partyboi2 said:**
> You could just wait till the extensions are updated. :)

Right, however it strikes me as odd.

Did you apply the FF3 and gecko updates?
Did you see similar results?

Thanks,
Kent

---

### Post by ktenney on 2008-07-25
OK, I see there was a version bump from 3.0 to 3.0.1

I'll go with changing the install.rdf files::

<em:maxVersion>3.0</em:maxVersion>
to
<em:maxVersion>3.0.*</em:maxVersion>

and see what happens

Thanks,
Kent

---

### Post by ktenney on 2008-07-25
That seems to do the trick, extensions pinned at 3.0 seem
to be working fine if changed to 3.0.*

---


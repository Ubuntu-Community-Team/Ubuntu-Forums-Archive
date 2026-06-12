---
title: "Apache changes"
date: 2008-08-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sddfdds on 2008-08-08
I'm experiencing two odd issues with the current version of apache.  In trying to upgrade Gallery, the Gallery updater insists the storage directory is not writable (I have checked and double checked the entire thing pkus -R is chmodded 777).  In addition to that, a symlink that previously worked now errors out with "Symbolic link not allowed or link target not accessible"

Any ideas?

Thanks

edit: So apparently the entire home directory needed to be chmodded in order for the server to be able to access it.  Sorry for another worthless thread.

---


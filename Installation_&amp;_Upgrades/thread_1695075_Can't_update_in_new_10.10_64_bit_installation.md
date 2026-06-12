---
title: "Can't update in new 10.10 64 bit installation"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by Wtwine on 2011-02-25
Hi 

I have installed Ubuntu 10.10 64 bit on a new machine.
I tried unsuccessfully to update, both via update manager and sudo atp-get update && sudo apt get upgrade.

I get this error message at the end of update in terminal: 
"W: Bizarre Error - File size is not what the server reported 0 198"

Any ideas?  This is the first time I have installed 64 bit so maybe I am missing something.

Thanks
Wayne

---

### Post by oldos2er on 2011-02-25
Have you added any PPAs or other repositories? If so I'd try disabling them.

---

### Post by Wtwine on 2011-03-29
I changed the update server to main server and it sorted the problem

---


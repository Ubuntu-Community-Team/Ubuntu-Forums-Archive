---
title: "[SOLVED] problem with update &amp;amp; packages"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by lordbux on 2008-11-23
hi
all ...errrr i am having some trouble with the update manager and 
aptitude

i am getting the following errors when i try to update:::
-----------------
**W: GPG error: [http://deb.orangearchive.net](http://deb.orangearchive.net) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 768FA3D9E3E1A434** :confused:
---------------------

i get the same message when i reload the package list too...

i tried **apt-get update ** but with no change at all
...
pleas  help
thanx in advance:guitar:

---

### Post by Partyboi2 on 2008-11-24
Go [[COLOR=Blue]here[/COLOR]]("http://deb.orangearchive.net/orangeArchive.key") and copy and paste the contents into a text file and save it as what ever you like. Then open up Software Sources (System>Admin>Software Sources)  and go to "Authentications" tab and choose to import key file. Then navigate to the text file you saved and add it.

---

### Post by lordbux on 2008-11-24
> **Partyboi2 said:**
> Go [[COLOR=Blue]here[/COLOR]]("http://deb.orangearchive.net/orangeArchive.key") and copy and paste the contents into a text file and save it as what ever you like. Then open up Software Sources (System>Admin>Software Sources)  and go to "Authentications" tab and choose to import key file. Then navigate to the text file you saved and add it.



thank you dude.... keep it alive

open source live for ever

---


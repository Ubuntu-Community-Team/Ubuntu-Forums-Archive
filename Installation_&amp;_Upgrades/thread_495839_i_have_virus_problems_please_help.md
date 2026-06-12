---
title: "i have virus problems please help"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by Joe88 on 2007-07-08
i'm new to linux and only installed Ubuntu yesterday yet i already have 2 viruses despite having set up the firstarter firewall; the 2 viruses i have are called :

-appleshell.dll
-msvcr70.dll

I detected them with aegis but it failed to quarantine and delete them, so i installed Clam TK but when i tell it to scan my file system it only scans 4 files and then says the scan is complete - do you know why Clam TK is not working?

---

### Post by onero on 2007-07-08
I assume you're running WINE? Most probably the actual programs you're trying to run have viruses. In any case, AVG and Avast have Linux versions; you might want to try them out.

---

### Post by Nekiruhs on 2007-07-08
.dll s are Windows files. even under WINE windows viruses can't harm your system.

---

### Post by Gremlinzzz on 2007-07-08
The Msvcr70.dll file is a library file that provides several services in Works 7.0. This includes printing. Generally, ISP programs, such as EarthLink Accelerator require the services of the Msvcr70.dll file.Don't think you have any virus just a case of the dills.:lolflag:

---

### Post by Joe88 on 2007-07-08
I'm not using Wine but I am using cedega, i guess ageis is a rubbish linux virus scanner seeming as it thought those windows .dll were viruses :)

I would still like to be able to use Clam TK though, just in case a linux virus does get on my pc one day - so does anyone know why my Clam TK isn't scanning properly?

---

### Post by sarang on 2007-07-12
> **Nekiruhs said:**
> .dll s are Windows files. even under WINE windows viruses can't harm your system.

That depends on how you define harm. I have wine installed and it was infected by a variant of the Brontok virus. Granted it affected only my home directory, but it still was a nuisance because it made around 500 copies of itself! (This is because the newer version of wine integrates (links) the windows desktop to the actual ubuntu desktop, and the profile folder to the actual home folder. Thus, any virus that affects wine can get into your home directory.)

---

### Post by Gremlinzzz on 2007-07-12
You can get a  false positive with any virus scanner i got one with bitdefender when i was a xp windows user.
:guitar:

---


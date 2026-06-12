---
title: "update packages cannot be authenticated"
date: 2005-07-30
forum: Installation &amp; Upgrades
---

### Post by vinthund on 2005-07-30
hello,

I just installed ubuntu on new machine. Right from the start there is of course a lot to update. However, when I agree to update basic 56 packages synaptic tells me it cannot authenticate them. Do I need to import gpg key or something? I cannot fnd anything on this subject in ubuntuguide.

regards

---

### Post by Olrich on 2005-07-30
If you are downloading these updates from the Ubuntu repositories just ignore the messages.

---

### Post by vinthund on 2005-07-30
[QUOTE=Olrich]If you are downloading these updates from the Ubuntu repositories just ignore the messages.[/QUOTE]

I use Ubuntu repos and Backports (mirrormax).

But anyway, why are those warnings there?

mv

---

### Post by Xian on 2005-07-30
[QUOTE=vinthund]I use Ubuntu repos and Backports (mirrormax).

But anyway, why are those warnings there?[/QUOTE]
The warnings exist to inform the user of packages that are not officially approved.
However, backports has been adopted so those should be safe.

I imagine this will all be resolved soon as the development continues.

But in the meantime, just open or create a text file named /ect/apt/apt.conf.
Place in that file the text listed below and save.

You should stop getting those warnings.

```
APT::Get::AllowUnauthenticated 1 ;
```

---


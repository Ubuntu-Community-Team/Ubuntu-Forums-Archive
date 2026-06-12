---
title: "How do I fix a broken package?"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by Daremo_06 on 2010-02-25
Alright maybe I posted my problem in the wrong forum, but I need to fix this because I can't update other things like JDK because of the dependancies.

[http://ubuntuforums.org/showthread.php?t=1415378](http://ubuntuforums.org/showthread.php?t=1415378)

That's my original post.

Should I just uninstall FF and then run the update?  If I remove FF, will I lose favorites ect?

---

### Post by northrup on 2010-02-25
Have you tried booting your kernel in recovery mode (accessible from the GRUB menu) and selecting the "Fix Broken Packages" (I think that's what it's called) option in the recovery menu?

---

### Post by lrcaballero on 2010-02-25
Do the following:
System/Administration/Synaptic package manager
on the left hand side select [COLOR="Navy"]Broken[/COLOR]and you should be able to see your broken package and just follow through to fix it.

Luis

---

### Post by Daremo_06 on 2010-02-25
> **northrup said:**
> Have you tried booting your kernel in recovery mode (accessible from the GRUB menu) and selecting the "Fix Broken Packages" (I think that's what it's called) option in the recovery menu?

Thanks that worked great!

---

### Post by Daremo_06 on 2010-02-25
> **lrcaballero said:**
> Do the following:
System/Administration/Synaptic package manager
on the left hand side select [COLOR="Navy"]Broken[/COLOR]and you should be able to see your broken package and just follow through to fix it.

Luis

Well, I had posted previously (see the link i had included) that I had already tried that and it didn't work.

---


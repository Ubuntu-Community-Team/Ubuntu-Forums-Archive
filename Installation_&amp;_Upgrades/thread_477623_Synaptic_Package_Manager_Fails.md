---
title: "Synaptic Package Manager Fails"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by pfgandjsg on 2007-06-18
System 7.04
I attempted to install "virtualbox" , a third party provider on my just installed Feisty 7.04.  The debian installer said all dependencies were available.  The install never finished.  I finally killed the install by using the "quit" box on the install.  I now can not use the "Snaptic Package Manager".

The error is:
E: The package virtualbox needs to be reinstalled but I can't find an archive for it.

Thank you in advance for any help.

John  :D

---

### Post by pfgandjsg on 2007-06-18
Found the same problem and answers in general problems post.

Thanks  :popcorn:

---

### Post by Pumalite on 2007-06-18
> **pfgandjsg said:**
> Found the same problem and answers in general problems post.

Thanks  :popcorn:

Could you share the link so we can all benefit from it?. Thank you.

---

### Post by thegitksan on 2007-06-30
Actually, same problem here too. Tried installing a generic winmodem driver, it failed to install, and now it keeps asking for the old archive. Also says it cannot find the archive please re-install. 

Synaptic remains obstinately unpopulated by *anything*, preferring to repeat this cryptic message. 

Doing a serarch on the local Help function yields nothing. Doing a search using error messages yields nothing at Ubuntu either, tho perhaps I just do not know where to look.

Yes, a link to the right place might help me too.

Thanks,
Russ

---

### Post by forestpixie on 2007-06-30
this might help you - it helped me

sudo dpkg --remove --force-remove-reinstreq <package name>

---

### Post by thegitksan on 2007-06-30
Thanks, that turned out to be part of the answer for me. The first part was deleting the files under the <something>/apt/   folder with the name of the offending partially installed application. Then followed with the string as you've typed it there, and it all worked.

Happiness. Thanks all, I'll post my exact steps in a while for future reference.

---


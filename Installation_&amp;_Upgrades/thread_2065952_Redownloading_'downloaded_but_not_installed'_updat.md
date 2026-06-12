---
title: "Redownloading 'downloaded but not installed' updates in Update Manager"
date: 2012-10-03
forum: Installation &amp; Upgrades
---

### Post by GammaPoint on 2012-10-03
Hi, I get updates from a PPA which updates the Java software on my computer (webupd8team-java). A couple weeks ago they sent out an update, which I downloaded and began to install. However, I must have double clicked something or not paid attention and I didn't accept the license agreement before continuing. This caused the update to fail. However, when I try to go back through the process to accept the agreement it just begins AFTER the location where I would have accepted the agreement, and just fails again. 

What is the best way for me to perhaps delete the information I've already downloaded in Update Manager, such that the update can be redownloaded and I can go through the process on an unadulterated copy?

Thanks,
GP

---

### Post by raja.genupula on 2012-10-03
what ever you have downloaded they will be at 
```
/var/cache/apt/archives/
``` location

---

### Post by GammaPoint on 2012-10-03
> **raja.genupula said:**
> what ever you have downloaded they will be at 
```
/var/cache/apt/archives/
``` location

Found it, thanks. If I delete those *.deb files, which there are 4 (2 of which were downloaded the same day and are most recent), will it work? Or is the information that it was downloaded actually stored in another file, and thus it needs to be edited as well?

---

### Post by raja.genupula on 2012-10-03
> **GammaPoint said:**
> Found it, thanks. If I delete those *.deb files, which there are 4 (2 of which were downloaded the same day and are most recent), will it work? Or is the information that it was downloaded actually stored in another file, and thus it needs to be edited as well?

If you remove them  like that , then again you have to download them .

if you have install them then you have to uninstall them to move from starting point .

---

### Post by GammaPoint on 2012-10-03
Hmm, deleted all the ones I saw (especially including the 2 that were listed in the new update), and restarted the computer. A new *deb file was downloaded, but it still knew that I had at one point not accepted the license agreement. So this information must be stored elsewhere....

If anyone knows, please let me know.

---

### Post by raja.genupula on 2012-10-03
remove the webupd8 jv completely and re install them . that can help you .

---

### Post by GammaPoint on 2012-10-03
> **raja.genupula said:**
> remove the webupd8 jv completely and re install them . that can help you .

Yeah, that would probably work, although I hate to mess with the Java stuff since it always seems so messy. Perhaps if I simply wait to the next release and update this issue will be fixed in the process.

Btw, someone asked about the license agreement (but then might have deleted their post). This is the first thing I see when trying to update the package:

[IMG]http://i45.tinypic.com/rwtmpj.png[/IMG]

---

### Post by raja.genupula on 2012-10-03
that was me actually :P .

have you tried to do them from terminal ?

---

### Post by GammaPoint on 2012-10-03
> **raja.genupula said:**
> 
have you tried to do them from terminal ?

No, although I just did. apt-get update and then apt-get upgrade allowed me to accept the license agreement in the terminal. Thanks, it appeared to work :)

---

### Post by raja.genupula on 2012-10-03
you mean your issue got solved ? 

if so please mark your thread as solved from thread tools

---


---
title: "java update error"
date: 2012-09-10
forum: Installation &amp; Upgrades
---

### Post by c2tarun on 2012-09-10
Hi friends,
When I update my machine an oracle jdk7 update gives an error.
Here is the screenshot of the error: [http://imagebin.org/227848](http://imagebin.org/227848)
Can anyone please help me in fixing this issue?

---

### Post by veroslav on 2012-09-10
I had the same problem and I went to the deb cache and just installed the update manually from there.

Regards,
Veroslav

---

### Post by c2tarun on 2012-09-10
> **veroslav said:**
> I had the same problem and I went to the deb cache and just installed the update manually from there.
 
Regards,
Veroslav
 
Sorry I didn't get what you are trying to say. Are you saying to go to /var/cache/apt/archive and install deb from there by dpkg --install *java*.deb?

---

### Post by sammiev on 2012-09-10
I prefer the [old fashion]("https://sites.google.com/site/easylinuxtipsproject/java") way.

---

### Post by QIII on 2012-09-10
Actually, the very best way to do this is a way that will keep Java updated as Oracle releases updates, without having to do anything more than run your normal Ubuntu updates.

In the wiki in my signature, under Oracle Java 7, in the "Command line methods", see the link "Using webupd8.org's strikingly simple method."

Three commands in the terminal, and Oracle Java 7 is done, installed, set as your default, the browser plugin is installed and when Oracle comes out with their next update, you won't have to do a thing except say "yes".

No watching for the latest update.  No uninstalling or removing directories.

Muon is a PITA for many people, and this may be one of the cases.  I never use it on my KDE machines.

---


---
title: "No idea what I'm doing wrong on the Gutsy upgrade"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Marty McFly on 2007-10-20
I went through the update manager to upgrade to Gutsy and went through a few steps and it asked me to put in the Gutsy i386 CD.  So I backed out, downloaded the iso, extracted and burned to a CD.  I went through the process all over again and now it won't accept the cd and just keeps asking me to insert it when it's already in there.

Any ideas or is there another way to do this?

---

### Post by mlind on 2007-10-20
update-manager asked you to put in Gutsy cd ? That shouldn't happen as you're upgrading by downloading packages from the web.

If you have any cdrom entries in your /etc/apt/sources.list, comment those out or remove them.

Could you post step by step commands what you exactly did and what the messages from update-manager where.

---


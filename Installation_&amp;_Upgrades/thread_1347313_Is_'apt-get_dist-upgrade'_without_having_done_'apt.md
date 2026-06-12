---
title: "Is 'apt-get dist-upgrade' without having done 'apt-get update' dangerous?"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by tbessie on 2009-12-06
I just ran apt-get dist-upgrade, and got some errors in the middle of downloading packages, as some pieces of those packages could not be found.

I then ran apt-get update, and then re-ran apt-get dist-upgrade, and it *appeared* to restart where the error had occurred.

Can this be depended upon, or is it possible that doing this can cause partial package installation or a broken package state on my system?

I am running Ubuntu Server 9.10.

- Tim

---

### Post by louieb on 2009-12-06
Common sense tells me the results will be unpredictable. You might get away with it - but then again you might not. 

BTW: did you get the warning to use safe-upgrade instead of dist-upgrade?

---

### Post by tbessie on 2009-12-06
> **louieb said:**
> Common sense tells me the results will be unpredictable. You might get away with it - but then again you might not. 

BTW: did you get the warning to use safe-upgrade instead of dist-upgrade?

Hmm, I don't recall seeing that warning, no, though it may have scrolled past me.  What is the difference?

- Tim

---


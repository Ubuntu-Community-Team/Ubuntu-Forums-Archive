---
title: "Update errors"
date: 2019-02-14
forum: Installation &amp; Upgrades
---

### Post by Alexander_O on 2019-02-14
Hi people,

since I installed several file synchronization programs (grsync, synkron) I get some errors when I do 'apt-get update':

[https://pastebin.com/jA3Asdb0](https://pastebin.com/jA3Asdb0)


Could you please help me to solve them? Do I need to remove the repository 'hanipouspilot' for the first error? What's about the other ones?

Thank you in advance.


Best regards
Alex

---

### Post by #&amp;thj^% on 2019-02-14
Yes remove it>> it hasn't had support since 16.04, and this one also "http://archive.getdeb.net/ubuntu/dists/zesty-getdeb" there is no repo for bionic, hence your error message.

---

### Post by #&amp;thj^% on 2019-02-14
> **1fallen said:**
> Yes remove it>> it hasn't had support since 16.04, and this one also "http://archive.getdeb.net/ubuntu/dists/zesty-getdeb" there is no repo for bionic, hence your error message.

Might be best to remove both PPA's with ppa-purge: [http://manpages.ubuntu.com/manpages/bionic/man1/ppa-purge.1.html](http://manpages.ubuntu.com/manpages/bionic/man1/ppa-purge.1.html)

EDIT: I have no idea why this edit created a new post.:confused:

---

### Post by Alexander_O on 2019-02-14
Thank you very much! It worked fine for me. Now everything goes right with the update. :)

---


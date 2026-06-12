---
title: "Repositories not listing Bacula for download."
date: 2024-09-26
forum: Installation &amp; Upgrades
---

### Post by maintech123 on 2024-09-26
There is an issue that is confusing to me. On my Linux mint it lists all that are version 13.0.4-1 build 3. This is a good thing. On a different Linux mint it only lists bacula-doc 9.6.7.1. And to add to my confusion,my Ubuntu 22.04.5 has the same issue as the one Linix Mint.because it only lists the bacula.doc. It sounds like a repository issue to me but after 12 straight hours of searching, testing, looking for related issues on the internet, I have found nothing of help. I could most likely build a bacula setup. I really would rather not because I have read how complicated the build is for bacula. If anyone has any clear thoughts on 1) What is actually happening  2) Why it is happening 3) What I can do to correct it. I would be in debt to the one who can answer those questions.

---

### Post by ActionParsnip on 2024-09-27
Can this be moved to Mint support please

---

### Post by deadflowr on 2024-09-27
For 22.04 looks like it's stuck in -proposed.
[https://launchpad.net/ubuntu/+source/bacula](https://launchpad.net/ubuntu/+source/bacula)
???? Why.? Don't know.

You could try to enable proposed, install and then disable proposed.
Or you can setup a pin priority for it
See: [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

> Can this be moved to Mint support please
I'm hesitant to move it since the OP is using both Mint and Ubuntu and the issue affects both.

---


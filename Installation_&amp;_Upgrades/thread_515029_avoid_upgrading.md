---
title: "avoid upgrading"
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by tall-male on 2007-08-01
When a new Ubuntu release arrives update manager (when started) will automaticly notice and ask to upgrade.

Building a Ubuntu PC for my father (74 years old) I made a configuration quite safe where he's not being able to do any harm. Just read and write his email, do some work using Open Office  and visit some webpages. The only admin-task heill be able to do is do some updates, allthough he's not member of the admin group! (worked that out using sudo!)

What I don't want him to deal with, is a new Ubuntu _release_. Just stick to Feisty as long as it is supported. How can ** avoid** the question in Update Manager  to upgrade?

---

### Post by devanity on 2007-08-01
Try this:

System -> Administration -> Software Sources -> Updates -> uncheck pre-released updates, unsupported updates and possibly recommended updates, so it will only download security updates.

---


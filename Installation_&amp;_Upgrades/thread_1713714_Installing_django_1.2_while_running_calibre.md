---
title: "Installing django 1.2 while running calibre"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by mntnoe on 2011-03-24
I use calibre for my ebook reader, which depends on django (provided in the repository as python-django, v1.1). I also develop in django, so I want to use the newest revision of the django 1.2 branch.

My question is: What is the best way to install both django 1.2 and calibre?

I could make the package manager ignore calibre's dependency on 'python-django' and install django 1.2 manually, but then, won't the package manager try to install the missing dependency when updating?

Another way is to create a deb package replacing python-django. How to do that?

I would like to avoid using a 3rd party repository, as I need to control when to upgrade django.

---

### Post by tannerwatson on 2012-03-25
I've got the same sort of problem. What did you end up doing to solve the problem?

---

### Post by mntnoe on 2012-03-25
Actually I stopped using calibre and installed django manually :-(

---


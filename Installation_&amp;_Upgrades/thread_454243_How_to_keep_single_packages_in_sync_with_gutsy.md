---
title: "How to keep single packages in sync with gutsy?"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by alanfranz on 2007-05-25
Hello, I'm not really an apt-get/dpkg expert, but I have a request. I'm using an i386 Feisty Fawn system.

I have some packages (with no strict dependencies, e.g. they depend on very little on the system, and they're not really a dependency of other packages) I'd like to keep in sync with gutsy, since I'd prefer them to be more close to the latest version. Most of them are plain, no-extension Python packages which just depend on the python interpreter itself.

My initial idea would have been to setup a mini-local repo which would periodically be updated (via rsync or sth like that), but I wonder if there's any easier way to go.

---


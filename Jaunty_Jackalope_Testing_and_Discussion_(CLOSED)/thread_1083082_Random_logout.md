---
title: "Random logout?"
date: 2009-02-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by iPodAddict181 on 2009-02-28
I have just installed 9.04 and it logged me out randomly. I logged back in and now the software manager is corrupted.

> Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness for the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I know what to do, but can anyone explain to me why this happened?

---


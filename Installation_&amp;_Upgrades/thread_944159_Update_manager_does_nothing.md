---
title: "Update manager does nothing"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by Koterpillar on 2008-10-11
When I start Update Manager, it promptly displays all available updates. After clicking on Install, console (yes, I'm running it from console) displays this:
```
Internal Error: filter name is longer than 55 chars!? Will be truncated.Please reporttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttt
nternal Error: filter name is longer than 55 chars!? Will be truncated.Please reporttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttt
```
I am prompted for root password, but then I only get "Reading state information" window and... back to the updates.

However, "sudo apt-get upgrade" always works as expected. How to fix update-manager in this case?

Small print: Ubuntu 8.04.1, latest updates, x64.

---


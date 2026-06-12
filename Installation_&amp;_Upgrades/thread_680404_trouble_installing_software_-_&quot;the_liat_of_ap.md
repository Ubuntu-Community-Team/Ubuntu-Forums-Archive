---
title: "trouble installing software - &quot;the liat of applications is not available&quot;"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by bruce11382 on 2008-01-27
I'm new to Linux and Ubuntu, so I hope this question isn't too basic for the forum.

I can't seem to install new software using either the Add/Remove feature under the Applications menu or the Synaptic package manager. I've tried installing numerous applications, and I always get the same message:

"The list of applications is not available. Click on 'Reload' to load it. To reload the list you need a working internet connection"

I click the refresh button, and a window pops up about refreshing the repository, but that's it. My internet connection is strong, so I doubt that's the problem.

Any advice would be greatly appreciated. Thank you in advance.

Bruce

---

### Post by taurus on 2008-01-27
Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and put a check mark in front of all the lines except the last one, Source code and the Cdrom in the bottom window.  Then, Close it and press Refresh.  Now, see if you can install other apps either with synaptic or Add/Remove.

---

### Post by yabbadabbadont on 2008-01-27
Please post the contents of the file /etc/apt/sources.list

Edit: What taurus said.  :D

---

### Post by highfrontier on 2008-01-28
Thanks Taurus.. I had the same problem, and your advice solved it

---

### Post by bruce11382 on 2008-01-29
Thank you very much, it worked. Forums like this make the switch from Windows so much easier.

Ubuntu- what a great concept

---


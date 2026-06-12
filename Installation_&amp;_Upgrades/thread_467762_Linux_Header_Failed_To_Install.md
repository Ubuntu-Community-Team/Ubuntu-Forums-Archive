---
title: "Linux Header Failed To Install"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by rykel on 2007-06-08
Hi all,

The latest upgrades have failed on my system... (see attached screenshot of the error message)

Am I the only one, or is this a major problem?

I am on Dapper, btw...

---

### Post by viciouslime on 2007-06-08
Try opening a terminal and typing "sudo apt-get install -f". Then try the update again.

---

### Post by rykel on 2007-06-11
> **viciouslime said:**
> Try opening a terminal and typing "sudo apt-get install -f". Then try the update again.

hey bud,

i tried "sudo apt-get install/update/upgrade/dist-upgrade -f" and got the same error message...

what else should i do?   :(

---

### Post by rykel on 2007-06-11
OK, problem solved!

I simply cleared the Synaptics cache and redownload the files again.

---


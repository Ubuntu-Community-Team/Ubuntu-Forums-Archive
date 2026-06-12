---
title: "need commands for update in terminal(update problem)"
date: 2014-06-06
forum: Installation &amp; Upgrades
---

### Post by taenbolle on 2014-06-06
i installed ubuntu 14.04 dual boot with windows 8.1.
the instalation seemd to go fine , but when it was complete and everything seemd to go fine, it was all just laggy.(as i am writing thi, the text akes about 1 sec to show up)
i tried update from update manager, and i do all things all that is i should do(restart).
but when i am back and go in terminal there it is the same update again.
i know the 'sudo apt-get update' but i also need to install the updates. so i hope the update maybe will solve my problem.
or is the another soulition?
i am using a intel 4430 so there can so no problem wtih the age the motherboard.

---

### Post by Frogs Hair on 2014-06-06
Hello taenbolle

Check for updates. ```
sudo apt-get update
``` The following will upgrade installed packages . ```
sudo apt-get upgrade 
```

---

### Post by Rob Sayer on 2014-06-07
sudo apt-get upgrade will update existing packages but not *replace* them.  This will usually happen if the update includes a new version of the kernel.  In which case you run:

```
sudo apt-get dist-upgrade
```

I usually do updates in terminal and have this line in my notes program:

```
sudo apt-get update && sudo apt-get upgrade
```

which I just copy and paste into terminal.

You should also update before installing software with apt-get update, or with the reload button in synaptic package manager, which is how I install programs if I'm not using the terminal.

I can't offer much advice about ubuntu update manager or sofware center.  Haven't used either in some time.

---


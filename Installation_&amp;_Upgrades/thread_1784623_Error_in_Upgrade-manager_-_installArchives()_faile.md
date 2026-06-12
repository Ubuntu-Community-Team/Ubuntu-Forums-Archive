---
title: "Error in Upgrade-manager - installArchives() failed:"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by Rincewind42 on 2011-06-17
When I try to install my systems updates using the upgrade-manager, I get the error "installArchives() failed: ". There is no other details given. Can anyone think what the solution may be?

I am using Ubuntu 11.4. I have already tried doing
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```
This didn't fix anything.

---

### Post by bapoumba on 2011-06-18
Have you been installing some package before you get the error ?
It is quite curious the error message does not point to a specific package causing problem. See here for ex: [http://ubuntuforums.org/showthread.php?t=1593717](http://ubuntuforums.org/showthread.php?t=1593717)

---

### Post by Rincewind42 on 2011-06-19
The only installed packages would have been from the previous update the week before. When searching the other threads, there is usually more errors in the report after this one but I'm just getting one line with no detail.

---

### Post by bapoumba on 2011-06-19
I also have been looking around and this error is mainly found when installing proprietary wireless or video drivers.
You can have a look at this older [bug]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/756204") that points to he first idea I had: something must have happened before you get this error. Without additional info, it is going to be difficult to help you..

---

### Post by Rincewind42 on 2011-06-24
Decided the fastest way to fix this was just to reinstall Ubuntu. It may not be the most elegant solution, in fact it's not really a solution at all, but I'm back to a stable working system in a relatively short time.

---

### Post by Rubi1200 on 2011-06-24
I am glad you got this sorted out in the end.

I am sure bapoumba would be happy if you marked this Solved using the Thread Tools near the top of the page.

---

### Post by bapoumba on 2011-06-26
Thanks for the thread title :)

I am also glad you solved your issue. Reinstalling is rarely necessary. Rarely does not mean never. Sorry I could not help you better, having a functional install is sometimes more important than applying an elegant fix. Have fun!

---


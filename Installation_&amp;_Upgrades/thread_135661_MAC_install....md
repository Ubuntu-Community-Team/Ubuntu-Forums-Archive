---
title: "MAC install..."
date: 2006-02-24
forum: Installation &amp; Upgrades
---

### Post by maxmiles on 2006-02-24
Hi, I'm new to linux and want to install ubuntu on my iBook. I'm afraid of the install wiping out everything else on the laptop's two partitions. What can I do to ensure the install 1) only installs on one partition, and 2) doesn't delete data on the other partition? 

any help would be great, 
~max

---

### Post by engla on 2006-02-24
Hello max
It's not a bad idea to run ubuntu on your iBook you'll find lots of pros and hopefully enough for you to use ubuntu more than os x.

This is what I did for a clean install. It should work (modified) for you:
I made two partitions in OSX, the first one I made "Free space" (to be Ubuntu later on) and the second one I installed OS X on.
*You should instead *use the disk utility to take your preferred Ubuntu partition and reformat it as free space (taking care to save the other partition, of course).

After this, I popped in the Ubuntu CD. Make sure you install Ubuntu Breezy 5.10, the stable version; if you use Dapper (for example) there can still be bugs that are very harmful to your data.

Commence the installation. When you get to the partitioning step, select "**Use largest free space**". this should make sure it doesn't tamper with any of the other partitions on the disk.
If you have a hard time identifying your partitions to really make sure which is which, it could be handy to have written down the exact sizes of them to check with.

Good luck.

---

### Post by maxmiles on 2006-02-24
thanks engla, i'll reformat the partition and give this a try.
~m

---


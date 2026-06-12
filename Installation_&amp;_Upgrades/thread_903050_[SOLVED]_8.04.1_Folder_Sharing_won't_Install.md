---
title: "[SOLVED] 8.04.1 Folder Sharing won't Install"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by mtwood on 2008-08-27
So here's the story, I can't enable folder sharing on Ubuntu 8.04.1. I right click a folder in /home/myuser directory, sharing options, check share this folder, pop-up "Sharing service not installed", click Install Service, Synaptic Package Manager asks for my password, then BAM! "Could not apply changes. Fix broken packages first". 

So I go to System -> Administration -> Synaptic Package Manager -> Edit -> Fix Broken Packages. Feedback in lower left corner reads "Successfully fixed dependency problems". But I repeat the process above with no success.

I tried checking for updates from the console,

```
 sudo apt-get -f install

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

But no luck.  Any ideas? I know this Right-click folder business is new for 8.04, did somebody break something with this new feature?

---

### Post by iaculallad on 2008-08-27
Try:

```
sudo dpkg --configure -a
sudo apt-get update && sudo apt-get upgrade
```

If all works well, try reinstalling the file sharing services.

---

### Post by mtwood on 2008-08-28
Thanks for the quick reply... I ran the commads and all seems to update okay, but after that, I try to enable folder sharing (as described above) , but the result is the same. . "Could not apply changes. Fix broken packages first"

Any good way to see what the "broken package" is?

---

### Post by mtwood on 2008-08-30
This is still a problem. Are there any troubeshooting steps that I can try?

---

### Post by Partyboi2 on 2008-08-30
Deleted

---

### Post by mtwood on 2008-08-30
This [thread]("http://ubuntuforums.org/showthread.php?t=899096") helped me out. samba-common was one version higher than the samba that was going to be installed. I forced removed samba-common, and replaced it with the next lower version. This broke wine and winbind, but I'll deal with that later.  Thanks for the help iaculallad.

---


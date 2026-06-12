---
title: "Ubuntu 11.10 not showing up in update-manager"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by GammaPoint on 2011-10-13
Hi everyone,

Last night I upgraded to 11.04. As I mentioned in another thread ([http://ubuntuforums.org/showthread.php?p=11311404#post11311404](http://ubuntuforums.org/showthread.php?p=11311404#post11311404)) I was unable to do this in a normal, clean way because I was always getting "Could not download the release notes" (I had been trying for weeks with different servers). Anyway, I got around it by running the command 

```
sudo sed -i 's/maverick/natty/' /etc/apt/sources.list
```

Then the next time I opened the update-manager, it told me I could do a "partial upgrade", so I went ahead and did that since I had no other idea of what to try (I know now that one is supposed to be wary of 'partial upgrades'). 

Anyway, now that I'm in 11.04 and I run update-manager (or even update-manager -d) I don't get anything that tells me that 11.10 is out. What can I do to see that? And does anyone know what the root problem of all these troubles I'm having is?

Thanks for the help!

---

### Post by zvacet on 2011-10-13
Is your Natty up-to-date?

```
sudo apt-get update && sudo apt-get upgrade
```

After that try to upgrade to the next release.

---


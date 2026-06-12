---
title: "Broken Packages When Updating, or Installing anything.."
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by kilmargames on 2011-01-07
When I try to update my packages, or install new packages, I get this error:

"E: /var/cache/apt/archives/libglib2.0-0_2.26.1-0ubuntu1_amd64.deb: subprocess new post-removal script returned error exit status 1"

I tried the "sudo apt-get install -f" but it didn't work.

I'm running 10.10, on a Asus laptop.
Please ask if you need anymore information

---

### Post by marl30 on 2011-01-07
> **kilmargames said:**
> When I try to update my packages, or install new packages, I get this error:

"E: /var/cache/apt/archives/libglib2.0-0_2.26.1-0ubuntu1_amd64.deb:  subprocess new post-removal script returned error exit status 1"

I tried the "sudo apt-get install -f" but it didn't work.

I'm running 10.10, on a Asus laptop.
Please ask if you need anymore information

If you can still open Synaptic Package manager, there is menu under  custom filter for fixing broken packages without the use of the  terminal. If that doesn't work, I suggest you log out and log into  command area and use this command ```
sudo apt-get update &&  sudo apt-get upgrade -y
```

---

### Post by kilmargames on 2011-01-07
Neither worked. It did say it failed to get packages from the cd even though its mounted and in the cd drive... :(

---

### Post by kilmargames on 2011-01-09
Um... Anyone? I know I'm double posting but... Come on... Its been more than a day...

---


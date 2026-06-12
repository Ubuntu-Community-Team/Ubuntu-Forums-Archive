---
title: "Dansguardian error during installs"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by al_scott on 2007-05-05
I upgraded to Feisty from Edgy, where I was running Dansguardian and Tinyproxy to filter web traffic.

During the upgrade, I got a Dansguardian error - sorry, I can't remember what it was.

Since then, whenever I install any software, I get an error like this...
> E: dansguardian: subprocess post-installation script returned error exit status 1

It doesn't affect  the install though.

I've removed Dansguardian and Tinyproxy, then reinstalled (lots of times), but I still can't get rid of the error message.

Dansguardian still works OK by the way.

Any ideas how to fix this??

---

### Post by pilpi on 2007-05-08
I'm not sure but I think I had the same problem and it had to do with the dansguardian package depending on the clamav package. I think doing 'sudo apt-get install clamav' fixed this. Maybe. :)

---

### Post by al_scott on 2007-05-08
Pilpi, you're right -  it's caused by clamav.

I initially looked in Synaptic and ClamAV is already installed. 
I ininstalled clamav, dansguardian plus the clam lib files associated with it, then re-installed clamav and dansguardian and now everything is OK.

Many thanks for your help.

---


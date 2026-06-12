---
title: "Synaptic and upgrade-manager failure"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by gambang07 on 2011-03-27
1. Update-manager panel icon changes into do-not-enter traffic sign.
2. If you want to re-install Update-manager using Synaptic, then Synaptic opens for a while and then closes by itself.

What should I do?

---

### Post by Sean Moran on 2011-03-27
> **gambang07 said:**
> 1. Update-manager panel icon changes into do-not-enter traffic sign.
2. If you want to re-install Update-manager using Synaptic, then Synaptic opens for a while and then closes by itself.

What should I do?

Just a rough guess, but it can't hurt what's already broken.  Try the terminal approach, with apt-get:

sudo apt-get remove update-manager   # this will take out what's not working (I hope)
sudo apt-get install update-manager      # hopefully, this will reinstall the update manager.

It does seem a little strange, as if there might be other things not quite right, Is synaptic working okay to install other packages?  That might point towards the problem being something wrong with just the update manager.

---

### Post by gambang07 on 2011-03-27
Thanks for your prompt response.

the result is like this:
Reading package lists....Done
Segmentation faulty tree....1%

More:
With Synaptic I cannot even keep it open let alone to install anything. It allows me to logon then it opens for a while and then closes.

Seemingly I need to reinstall. However, I'd better wait till the next release at the end of April....

---

### Post by Sean Moran on 2011-03-27
> **gambang07 said:**
> Thanks for your prompt response.

the result is like this:
Reading package lists....Done
Segmentation faulty tree....1%

More:
With Synaptic I cannot even keep it open let alone to install anything. It allows me to logon then it opens for a while and then closes.

Seemingly I need to reinstall. However, I'd better wait till the next release at the end of April....

I'm sorry that I've not had many problems with broken dependencies, so not sure exactly whether this will or won't fix that segmentation faulty tree problem.  I'm guessing it's related to broken dependencies in a major way, although it's beyond my level of expertise.  The apt-get command I hope might sort this out is:

sudo apt-get -f check

where the -f option is to 'fix' things and the check command is to 'check things'.  It won't hurt, but I can't tell you whether it will find the fault or not.  Unfortunately, I don't seem to have enough problems with my packages to really know the answer from experience.

---


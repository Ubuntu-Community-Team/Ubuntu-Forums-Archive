---
title: "Can't Install Applications"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by jslominski001 on 2007-12-19
When I go to 'Add/Remove' applications, and select to install an unchecked application, I always get a popup warning that says:

[COLOR="Red"]"The list of applications is not available. Click on 'Reload' to load it. To reload the list you need a working internet connection." [/COLOR] 

Even when I click reload, the same error occurs repeatedly.

Can someone help? Thanks!

---

### Post by Sef on 2007-12-19
Let's see if synaptic works.

System > Administration > Synaptic Package Manager

Just search for something you want to install, and see if you can install it.

If that doesn't work, then try this command:

Applications > Accessories > Terminal

Then type in this command:

```
sudo apt-get update
```

That simply updates your repositories.  If it works, then the backend is working, and the problem would be with the front end GUIs (Add/Remove and Synaptic.)

---


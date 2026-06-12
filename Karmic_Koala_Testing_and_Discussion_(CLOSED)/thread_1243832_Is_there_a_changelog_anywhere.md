---
title: "Is there a changelog anywhere?"
date: 2009-08-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bsmith1051 on 2009-08-18
I'm more concerned about this for the stable versions (e.g. 9.04) than the dev versions, but it's apropos for both...

Where can I find a changelog for all the Update Manager updates?  

On my 9.04 rig I'm suffering endless regressions on things (eg. USB compatibility, fast-user-switch).  I've tried to find info online about them but I must not know where to look.  I'm hoping that an official Ubuntu changelog will be a better source.

---

### Post by 23meg on 2009-08-18
> **bsmith1051 said:**
> 
Where can I find a changelog for all the Update Manager updates?  


[https://launchpad.net/ubuntu/+source/update-manager](https://launchpad.net/ubuntu/+source/update-manager)

---

### Post by nhasian on 2009-08-18
I believe that will only show you the changes for the application update-manager.  I think bsmith1051 wanted a list of all the programs that get updated on a daily bases.  unless I'm mistaken?

> **23meg said:**
> [https://launchpad.net/ubuntu/+source/update-manager](https://launchpad.net/ubuntu/+source/update-manager)

---

### Post by castrojo on 2009-08-19
Try these:

[https://lists.ubuntu.com/#Package+Upload+and+Automatic+Notification+Lists](https://lists.ubuntu.com/#Package+Upload+and+Automatic+Notification+Lists)

---

### Post by 23meg on 2009-08-19
> **nhasian said:**
> I believe that will only show you the changes for the application update-manager.  I think bsmith1051 wanted a list of all the programs that get updated on a daily bases.  unless I'm mistaken?

That's right; I misunderstood. In that case, /var/log/apt/term.log can help.

---

### Post by taavikko on 2009-08-19
One can also use 
```
aptitude changelog <package>
```
to view changes for a package

---

### Post by ssam on 2009-08-19
there are rss feeds with the changelog for each package upload.
[http://feeds.ubuntu-nl.org/KarmicChanges](http://feeds.ubuntu-nl.org/KarmicChanges)
(also [http://feeds.ubuntu-nl.org/JauntyChanges](http://feeds.ubuntu-nl.org/JauntyChanges) etc).

---

### Post by rajeev1204 on 2009-08-19
> **taavikko said:**
> One can also use 
```
aptitude changelog <package>
```
to view changes for a package

Or from synaptic>packages>download changelog.

---

### Post by bsmith1051 on 2009-08-21
> **whiprush said:**
> Try these:
[https://lists.ubuntu.com/#Package+Upload+and+Automatic+Notification+Lists](https://lists.ubuntu.com/#Package+Upload+and+Automatic+Notification+Lists)
Thanks, that's close to what I wanted.  I was hoping to find that same info but organized by Date Posted, e.g. a list of all changes in the 21 Aug 2009 updates (like I just installed this morning).

Also, unfortunately, I don't see any updates to the Fast User Switcher App (FUSA) which broke for me last week.  So I still have no idea what caused it to break, probably an incompatibility with some other module :( ...

---


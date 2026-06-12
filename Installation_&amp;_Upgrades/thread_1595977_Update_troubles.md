---
title: "Update troubles"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by willchurch on 2010-10-13
When i tried to upgrade my system, I got this:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 61E091672E206FF0

What does this mean? And how do I fix it?

---

### Post by willchurch on 2010-10-13
I have managed to solve this (apparently), but now i get this message:
"Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources."

Clicking on Details reveals:

"libnautilus-extension1 nautilus nautilus-data"

Now what is going on? Is this the same problem as before? And now what do I do?

---

### Post by standards on 2010-10-15
same problem!

i've googled for past solutions but none of them work, e.g. 

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D8D75E403EBCE749
```

 as it stands i can't update anything.

---

### Post by plucky on 2010-10-15
> **standards said:**
> same problem!

i've googled for past solutions but none of them work, e.g. 

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D8D75E403EBCE749
```

 as it stands i can't update anything.

Your command is incomplete.

See [https://answers.launchpad.net/ubuntu/+source/update-manager/+question/59304](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/59304)

Or 

Disable the Launchpad PPAs in Software Sources and reload

Good Luck

---


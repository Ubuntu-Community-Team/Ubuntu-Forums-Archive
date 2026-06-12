---
title: "Xubuntu Restricted Extras"
date: 2017-01-01
forum: Installation &amp; Upgrades
---

### Post by Malacath on 2017-01-01
When installing Xubuntu 16.04.1 LTS I skipped installing the restricted extras.

How to I install then now?

I can't find them in the software centre.

---

### Post by Crimple on 2017-01-01
Install Synaptic package manager from the software centre and use it to install the restricted extras.
You can also install from terminal 
```
sudo apt-get install xubuntu-restricted-extras
```

but you'll probably find Synaptic useful in the future.

---

### Post by howefield on 2017-01-01
> **Malacath said:**
> When installing Xubuntu 16.04.1 LTS I skipped installing the restricted extras.

How to I install then now?

I can't find them in the software centre.

If you don't mind using the terminal..

```
sudo apt install xubuntu-restricted-extras
```

By the way, the installation procedure doesn't install xubuntu-restricted-extras, but rather xubuntu-restricted-addons which is similar but is not the same package.

---

### Post by Crimple on 2017-01-01
@howefield

Didn't see your post while I was editing mine, sorry.

---

### Post by bearlake on 2017-01-01
Make sure you checkmark "Canonical Partners"
Software packaged by Canonical for their partners.

---

### Post by howefield on 2017-01-01
> **Crimple said:**
> @howefield

Didn't see your post while I was editing mine, sorry.

Never a problem :)

> **bearlake said:**
> Make sure you checkmark "Canonical Partners"
Software packaged by Canonical for their partners.

Why ?

---

### Post by Malacath on 2017-01-01
Thanks guys.

I downloaded Synaptic and installed the restricted extras using that.

---


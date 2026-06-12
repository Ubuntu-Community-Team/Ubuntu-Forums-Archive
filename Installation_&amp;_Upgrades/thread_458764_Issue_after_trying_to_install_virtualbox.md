---
title: "Issue after trying to install virtualbox"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by linax on 2007-05-30
Hi,

I had downloaded virtualbox installation file to my hard drive from the website. I had initiated the installation. But my laptop crashed during the process.
Now , whenever i start synaptic package manager, i get the following error.

E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

How do i get rid of this?

Thanks upfront,

Linax

---

### Post by linax on 2007-05-30
Even though the error says archive file not found. it is still available at the same place.

---

### Post by bodhi.zazen on 2007-05-30
The only way I know of to fix this problem is to re-install virtualbox.

VirtualBox must be installed from the command line; *This is a change

```
sudo dpkg -i /path_to/VirtualBox-xyz.deb
```

If you get an error message with the command, delete and re-download the virtualbox package.

---


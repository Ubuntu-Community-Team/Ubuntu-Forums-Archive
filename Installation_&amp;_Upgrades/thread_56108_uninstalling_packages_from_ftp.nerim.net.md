---
title: "uninstalling packages from ftp.nerim.net"
date: 2005-08-11
forum: Installation &amp; Upgrades
---

### Post by Heretic09 on 2005-08-11
I want to know what packages i've installed from ftp.nerm.net. I know i've installed a few but when I try this:

apt-cache policy $(dpkg --get-selections| awk '{print $1}') | grep -B5 ftp.nerim.

I don't get anything. Is there an easy way via  synaptic or command line I can get apt to list those packages?

---

### Post by Heretic09 on 2005-08-11
Anyone?

---

### Post by rama on 2005-08-12
[QUOTE=Heretic09]Anyone?[/QUOTE]
 I m not sure if this is the case and I must warn you that I am a Linux noob, but I think that this repository is not available any more. 
I was constantly getting errors from synaptic that it counld not locate it, so I removed it from my repos list.

Hope I 've been helpfull!

---

### Post by Heretic09 on 2005-08-12
Yeah i've already removed the name from my sources.list. I just want to know what packages i've installed from there. Any one know of any way of telling what repository an installed package came from?

---


---
title: "Customizing Ubuntu packages"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by Orbit45244 on 2007-03-17
I am making a new technology for a small group of users on the internet. This technology uses apt. All I need Ubuntu for in this case is using synaptic because it doesn't work with cygwin. So what I would like to do is slim down the Ubuntu 6.10 distro to be smaller and easier to download. This new distro will be run in a virtualization environment. The only programs I need the distro to run are samba, smbfs, all package programs (apt-get, dpkg, dselect, etc.), and synaptic. I would also like the distro to run the Update Manager, but that is not a requirement. So I was wondering what packages I would keep and what packages I would remove from Ubuntu to make it smaller, while still keeping the above functionality.

---

### Post by kerry_s on 2007-03-17
I think you should start the other way around. Do a server install and only add what you need. The server can also be trimmed further.

Here's the mini.iso's to play with. I'm sure you can easily unpack it modify the apt-get install to install only what you want.

Edgy-> [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso)

Feisty-> [http://ubuntu.mirror.frontiernet.net/ubuntu/dists/feisty/main/installer-i386/20061102ubuntu14/images/netboot/mini.iso](http://ubuntu.mirror.frontiernet.net/ubuntu/dists/feisty/main/installer-i386/20061102ubuntu14/images/netboot/mini.iso)

---


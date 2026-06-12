---
title: "No kickstart support in desktop initrd install iso"
date: 2015-04-23
forum: Installation &amp; Upgrades
---

### Post by frackers2 on 2015-04-23
Greetings

I've been trying to automate a desktop install using kickstart but after many failures I had a look inside the initrd file on the iso image and compared it to the ubuntu-server version and they are totally different. As far as I can see there is no kickstart support in the desktop version.

Can someone confirm this is true and if so what changes are going to be made to [https://help.ubuntu.com/community/KickstartCompatibility](https://help.ubuntu.com/community/KickstartCompatibility) to indicate that is is no longer supported with Casper?

My preference for these desktops is a very slim one - Lubuntu or something very similar. Presumably I can simulate the install by using ubuntu-server and then install @lubuntu-core and @lubuntu-desktop but it would be nice if these issues were documented (and it would have saved me 4 days work!!).

Cheers

---

### Post by ian-weisser on 2015-04-23
That seems like a bug. Please report it.
I don't recall any discussion of dropping kickstart support.

---

### Post by frackers2 on 2015-04-24
I've taken the 14.04 server iso, junked the squashfs filesystem and substituted the one from Lubuntu 14.04LTS into it (along with its associated manifest etc), added the changes to syslinux config for kickstart and the ks file and rebuilt the checksums. 

It all installs nicely so I just have to fine tune the %post section of the ks file and build a local cache of the updates that will be required and then I can start reproducing boxes the way **I** want them :)

I've a bit more analysis of the issues in the initrd to do before raising a Launchpad bug!

---


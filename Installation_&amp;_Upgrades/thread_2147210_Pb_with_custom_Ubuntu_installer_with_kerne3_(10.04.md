---
title: "Pb with custom Ubuntu installer with kerne3 (10.04 LTS lucid)"
date: 2013-05-21
forum: Installation &amp; Upgrades
---

### Post by Pbas on 2013-05-21
Hi, I need help to finalize my install CD of Ubuntu/lucid with a custom installer with kernel 3:
 I generate the initrd.gz/vmlinuz and put in the ubuntu-server CD but my install stop after the network configuration (it is not a core dump but a return to main menu installer without partionning entry etc..), any ideas?

NB: the net install working like a charm.

NB2: The install log indicate ... nothing wrong...

NB3: I read this [http://meetings-archive.debian.net/pub/debian-meetings/2006/debconf6/slides/Debian_installer_workshop-Frans_Pop/paper/index.html#id2534366](http://meetings-archive.debian.net/pub/debian-meetings/2006/debconf6/slides/Debian_installer_workshop-Frans_Pop/paper/index.html#id2534366) and I think the "stage 4" doesn't start.

 thxs

---

### Post by ajgreeny on 2013-05-21
Is this a server installation supported till 2015 or the desktop version, as the gnome version of Lucid 10.04 has recently (May 9) lost all support, and the repositories have moved.

To save a lot of likely problems I suggest you start again with a fully supported version, Xubuntu 12.04 now being my chosen OS in order to avoid unity, which just does not work well for me.

---

### Post by Pbas on 2013-05-21
I know that but I can't choose ubuntu version... I must use lucid because we have specific  packages working only on this version.

---

### Post by ajgreeny on 2013-05-21
It may help if you use the new EOL (end-of-life) repos which you can find out about at [https://help.ubuntu.com/community/EOLUpgrades#Upgrade](https://help.ubuntu.com/community/EOLUpgrades#Upgrade)

You will get no more updates or security fixes, though I presume you will still be able to add packages that are in those EOL repos.

PS:
I've just looked and seen that Lucid is not mentioned, maybe because it is all too recent, but this may still give you the basic idea of how you can proceed.

---


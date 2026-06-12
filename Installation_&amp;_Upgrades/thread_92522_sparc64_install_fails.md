---
title: "sparc64 install fails"
date: 2005-11-19
forum: Installation &amp; Upgrades
---

### Post by syrphid on 2005-11-19
I'm trying to netinstall on a Sun Ultra10 starting from the mini-CD. 
After configuring eth0 manually, the base system is downloaded and installed OK,
so the network connection is working.

Then apt tries to download stuff, but can't resolve the archive address because the network connection has now failed, so I'm missing 846 packages.

Using the console in the base system I can't ping my router.

lspci | grep Eth has the ethernet controller identified

mii-tool doesn't work, maybe not supported?

ifconfig eth0 shows the lines   inet addr:   and inet6 addr:  missing.

route -n  has no numerical entries for Destination, Gateway etc.

/etc/network/interfaces has all the IP numbers right though.

What do I need to do to get the routing set up, and then will all be well if I just
run apt-get update?

thanks..

---

### Post by Chayak on 2005-11-19
I don't have any experience with sparc64s but I haven't seen anything for Ubuntu on that processor.  The only official ones I'm aware of is X86, PPC, and AMD64.  Are you doing a debian install?
EDIT: Just checked to be sure.  Ubutnu doesn't have a sparc64 port so it sounds like you're trying to do a debian install.

---

### Post by syrphid on 2005-11-20
[QUOTE=Chayak]I don't have any experience with sparc64s but I haven't seen anything for Ubuntu on that processor.  The only official ones I'm aware of is X86, PPC, and AMD64.  Are you doing a debian install?
EDIT: Just checked to be sure.  Ubutnu doesn't have a sparc64 port so it sounds like you're trying to do a debian install.[/QUOTE]

Hi
   I'm using a port that I got from
//ports.ubuntu.com/ubuntu-ports/dists/breezy/main/installer-sparc/current/images/

Does that sound official? Anyhow, I'm pleased to get anything more up to date than old SUSE 7.3. 
The fact remains, it attempts to fetch stuff from //uk.archive.ubuntu.com, and the sparc stuff is there, but the operation fails every time as described.

Help welcome!

---

### Post by syrphid on 2005-11-23
I'm answering my own question here, in case anyone else gets stuck the same way!

"auto eth0"   [without the " "] was missing from the end of /etc/network/interfaces

Had to read a lot of  taxing stuff to discover this, which I'd hoped to avoid by installing ubuntu! Still, bound to come in useful sometime.

---


---
title: "Wonderful NDiswrapper, what happened to you?"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by TheIdiotThatIsMe on 2005-10-14
Just upgraded to Breezy, and the one single package I hope wouldnt get messed up did, ndiswrapper. I get the error described in the stickied post above, the fatal error operation (or permission, I dont remember) denied. Anyways, I tried what he said and it didn't work at all. I was going to recompile ndiswrapper, but wont let me due to missing dependencies including gcc 3.4 and some header junk. Since I upgraded over the internet, I dont have the Kubuntu cd. It tries to download the packages through the internet when using kynaptic, which obviously doesn't work.

In short:
Ndiswrapper got messed up
ndiswrapper needs dependent packages
packages are on net
Need ndiswrapper to connect to the net.

Someone please help!?

---

### Post by blujay on 2005-10-14
Simplest way: Use the computer you are on now to download the deb packages and copy them to something, then copy them to the Ubuntu PC and "sudo dpkg -i *" in the directory the debs are in.

There are also other apt tools that can do it, but that's probably the simplest way.

---

### Post by TheIdiotThatIsMe on 2005-10-14
[QUOTE=blujay]Simplest way: Use the computer you are on now to download the deb packages and copy them to something, then copy them to the Ubuntu PC and "sudo dpkg -i *" in the directory the debs are in.

There are also other apt tools that can do it, but that's probably the simplest way.[/QUOTE]

Well what's really interesting is that I just booted up into my old kernel (still Breezy Badger though) and it loads up the module fine. I really dont want to have to recompile ndiswrapper though, because it was a pain in the butt the first 4 times (yeah it gets broken a lot with me). Is there anything else I can do?

---

### Post by TheIdiotThatIsMe on 2005-10-14
Alrighty I got it working. When I booted up into my old kernel I downloaded some three ndiswrapper related packages (ndiswrapper-util, ndiswrapper-source, and ndisgtk) and when I rebooted into the new kernel I was able to modprobe ndiswrapper without any problems or config.

---


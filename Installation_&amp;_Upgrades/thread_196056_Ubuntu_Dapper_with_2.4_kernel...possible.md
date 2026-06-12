---
title: "Ubuntu Dapper with 2.4 kernel...possible?"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by GCR on 2006-06-13
Hey! I have een wanting to try Ubuntu for quite aqhile, but I have a problem that keeps me from joining the ride. Apparently my integrated NIC(an intel 845 chipset) and a subsequent NIC(Realtek 8139), are not compatible with any distro that has a 2.6.xx kernel. So I infer it is a bug or some other problem related with the hardware. Ive tried, gentoo, SuSE, Ubuntu, Slackware(with 2.6 kernel), and none seem to work(the network, rets is fine).

So, I ask, is there any way to install Ubuntu using a 2.4 kernel?

Or if people have experienced problems with the NICs stated above, any idea how to solve them? Drivers chosen by the system are e100 for the Intel NIC and 8139too for RTL 8139(they both work well with 2.4 kernels on other distros).

Thanks for the help!

---

### Post by linuchsan on 2006-06-13
apt-cache search kernel-image

---

### Post by GCR on 2006-06-14
I tried the command, it outputs "alsa-base"...but what should I do? Im an Ubuntu/Debian noob dso sorry if this sounds stupid.

Thanks for the help!

---

### Post by GCR on 2006-06-15
any help?

---

### Post by grexk on 2006-06-16
apt-cache search kernel*. Hope this helps.

---

### Post by Gustav on 2006-06-16
there is no prepackaged 2.4 kernel in the dapper repos so you'll have to get it some other way (e.g. compile it yourself)

---

### Post by GCR on 2006-06-16
one quick question...does previous versions of Ubuntu feature any 2.4 kernels?

---

### Post by Gustav on 2006-06-16
nope

---

### Post by GCR on 2006-06-16
oh well, Ill compile a 2.4.32 kernel I guess. If not then Ill have to settle for my good ol Slackware.

Thanks anyways for the help!

---

### Post by ubnoobie on 2006-06-17
2.4.xx kernel is in universe

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=kernel-&searchon=names&subword=1&version=dapper&release=universe](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=kernel-&searchon=names&subword=1&version=dapper&release=universe)


fwiw: all my nic's at home are realtek 8139c or 8139d ('cept for one onboard via rhine ii); they all work fine on 2.6 series kernel... and although i don't have one at present, i've not had any problems installing to a 845g-based intel-made motherboard with an actual intel ethernet controller onboard.

---

### Post by Gustav on 2006-06-18
Oh, there they were.

Sorry I said there weren't any (I thought they would be called linux-image like the 2.6 kernels)

(This is the second time in a week that I provide false information, I should really check that I know what I'm talking about before I answer)

---


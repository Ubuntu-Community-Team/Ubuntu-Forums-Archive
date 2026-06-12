---
title: "keychain needs ssh-askpass"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by grepper on 2005-10-14
Hi,

after upgrading to breezy keychain dosn't work anymore. When I try to start it I get the following error:
```

 * Found existing ssh-agent (9314)
 * Found existing gpg-agent (9334)
 * Adding 1 ssh key(s)...
ssh_askpass: exec(/usr/bin/ssh-askpass): No such file or directory
 * Error: Problem adding; giving up

```

Any suggestions? Is the openssh-client really installed without ssk-askpass?

cu, grepper

---

### Post by zojas on 2006-10-22
I'm getting this problem too (I was already running dapper, but I just did a dist-upgrade to get kde 3.5.5)

anyway, on my other dapper system (which I haven't updated in a couple weeks), I found that ssh-askpass came from the package ssh-askpass-gnome, version 1:4.2p1-7ubuntu3.1.

and on my now broken system, I don't have that package installed at all.

---

### Post by zojas on 2006-10-22
I installed the ssh-askpass package and now it works again. probably could have installed ssh-askpass-gnome again (it's still in the package list) but I figured if it got removed, there must be a reason. :)

---


---
title: "iscsi support in Ubuntu 8 server"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by laniohma on 2008-04-30
The readme states that iscsi support is included in the latest Ubuntu release and should be in place when the argument: "iscsi=true" is passed to the kernel during installation.

My question: If I did not do the above; what are the steps or instructions to enable iscsi support POST-installation?

I have a number of 7.0.4 server boxes which I want to perform a network upgrade.

I am looking for documentation on using "iscsi=true" during the network upgrade to enable the feature in my upgraded hosts. 

Also I do require a network upgrade as the graphical environment is not desireable for my hosts.

I cannot locate much documentation on the new server version except the upgrade paths.

Any help is appreciated.


It would be awesome if the doco was available & showed how to do both targets & initiators with server 8.0.4

---

### Post by mrprefect on 2008-05-08
I too would much appreciate some more documentation on this

---

### Post by tallsky on 2008-06-30
I've seen this time and time again.
"We've implemented something important!"
And then, not so much as a hint on access methods.

---

### Post by tallsky on 2008-06-30
Release notes says they now support the open-iscsi package as a maintained option.

But previous beta release notes more explicitly state it as kernel support.
IDK.

I guess this is the best available as far as instructions on setting it up:

[http://www.cyberciti.biz/faq/howto-setup-debian-ubuntu-linux-iscsi-initiator/](http://www.cyberciti.biz/faq/howto-setup-debian-ubuntu-linux-iscsi-initiator/)

---


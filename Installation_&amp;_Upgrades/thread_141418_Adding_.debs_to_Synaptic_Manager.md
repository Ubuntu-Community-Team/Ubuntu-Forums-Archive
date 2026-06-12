---
title: "Adding .debs to Synaptic Manager"
date: 2006-03-08
forum: Installation &amp; Upgrades
---

### Post by Merlin_Guy on 2006-03-08
I like Breezy but it doesn't have the lib***-dev packages that I need to compile applications like PostgreSQL.  Can anyone give me instructions on how to add *.deb locations from their packages.ubuntu.com/breezy location into my Synaptic manager???  I am hoping that if I use Synaptic I won't end up with the broken packages like when I use dpkg -i.

Thanks.

---

### Post by linear on 2006-03-08
I think you're asking: "How do I add repositories?" If so, see [here]("https://wiki.ubuntu.com/AddingRepositoriesHowto").

---

### Post by Merlin_Guy on 2006-03-08
Thanks man.

I added the Hoary repositories into my Synaptic Manager and then installed the *-dev packages that I needed.

Worked like a charm... :-D

---

### Post by engla on 2006-03-08
Be careful about that though, you should only use Breezy repositories for Breezy.

And also, regarding "not being as risky as dpkg  -i", I see no difference -- you take something external and install it to your system; both are comparably risky.

---

### Post by Merlin_Guy on 2006-03-09
Understood.  While the Breezy package archive has the libreadline5-dev and libncurses-dev packages, they aren't included in the 'Breezy main restricted' distro.  

I really don't understand why since many third party applications depend on symbolic links and header files that the lib*-dev packages provide.

---


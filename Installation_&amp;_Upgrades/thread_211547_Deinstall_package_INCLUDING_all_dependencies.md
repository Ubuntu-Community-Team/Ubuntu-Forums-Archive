---
title: "Deinstall package *INCLUDING* all dependencies"
date: 2006-07-08
forum: Installation &amp; Upgrades
---

### Post by A.Skwar on 2006-07-08
Hi!

I just installed mplayer on Dapper. Synaptic told me, that some additional packages need to be installed to satisfy the dependencies. Thus, I installed those as well; packages like liblame0, libungif4g and some more, which I forgot.

And the "forgot" is the reason why I'm asking now  :)  I'd like to deinstall mplayer *including* all the depencies which were installed to meet those requirements.

How would I do this?

On Gentoo, I'd (more or less) do it that way, that I'd now do a "emerge --depclean --pretend" and record the result. "--depclean" shows those packages, which were "once upon a time" installed as a dependency of some other package but are no longer required by any installed package. Well... After I run the "emerge --depclean --pretend", I'd deinstall mplayer and run "emerge --depclean --pretend" once more. Any new package must've been installed to satisfy dependencies of mplayer.

Surely I can do something like that with Debian (Ubuntu) as well, can't I? How?

Thanks,

Alexander

---

### Post by kewldude606 on 2006-07-08
Uninstall mplayer, then install deborphan.  Run deborphan at the command line and uninstall all of those apps.

In the future, use aptitude.  It rememebers what dependencies it installed for an application.

---

### Post by aysiu on 2006-07-08
I'm with kewldude606 on this one. If removing the dependencies is important to you, don't use Synaptic to install packages.

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---


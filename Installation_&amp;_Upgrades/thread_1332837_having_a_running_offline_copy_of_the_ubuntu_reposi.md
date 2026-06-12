---
title: "having a running offline copy of the ubuntu repository server"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by Miki800 on 2009-11-20
I need an offline copy of the entire ubutnu repositories server
for jaunty especially but for all others as well would be perfect.

I need a copy of everything under [http://archive.ubuntu.com/ubuntu/dists/*jaunty](http://archive.ubuntu.com/ubuntu/dists/*jaunty)

and I need it in a way that will work with apt-get / synaptic.

I need to install it in a network that is not connected to the internet

are there somewhere DVDs to download of such data?
is it bundled with a server of just what I'm looking for?

what exactly do I do to accomplish that?

thanks ahead for any relevant help

---

### Post by mac9416 on 2009-11-20
Hey, Miki800,

One option is to buy the repositories on DVD. You can get them here: [http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html)
That is the repo for 9.10, but perhaps they have 9.04 repos too. Also, that link is to the 32-bit repos, though they do have the 64-bit versions.

Another option is to mirror the repos using [apt-mirror]("http://apt-mirror.sourceforge.net/"). That takes a little doing, but it may be worth it for you. You will have to set up the server to hold the repos yourself, but it's not too hard using [Ubuntu Server Edition]("http://www.ubuntu.com/products/whatisubuntu/serveredition").

If you only need to get a few packages to install offline, I would suggest using [Keryx]("http://keryxproject.org"). Once you get the debs with Keryx, you can install them with the help of [APTOnCD]("http://aptoncd.sourceforge.net/"), or make a repo with them using Keryx's LocalRepo-Add.py script (you can ask for instructions on how to use the script on the [Keryx forums]("http://keryxproject.org/forums/") since there currently isn't a howto).

I hope you find that info helpful!

---


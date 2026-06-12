---
title: "Problem with apt-mirror"
date: 2011-03-17
forum: Installation &amp; Upgrades
---

### Post by venomsm on 2011-03-17
I have a apt-mirror repository with contain all packages from BR repository of ubuntu and canonical partners. My repository only have official repositorys and never have a problem about 1 year.

Making some daily updates happened some problem i do not know.

Now, when i execute apt-get update in clients, i receive some errors like this:

W: Failed to fetch [http://ubuntu/ubuntu/dists/lucid-updates/main/binary-i386/Packages.bz2](http://ubuntu/ubuntu/dists/lucid-updates/main/binary-i386/Packages.bz2) hash sum incorreto

ubuntu = ip(dns) of my local repository

If i delete PUBKEY and add again with commands below works.

gpg --keyserver subkeys.pgp.net --recv KEY
gpg --export --armor KEY | sudo apt-key add -

But, execute this procces don't is easy for my people doesn't much of linux, and i don't know what is happing :(

Sorry for my bad english, i am a brazilian guy.

Thanks for help.

---

### Post by Hakunka-Matata on 2011-03-17
maybe changing your repository source website.  click the down arrow to see other mirror sites to use.  Excuse me if you have already tried this.

---

### Post by venomsm on 2011-03-17
My problem is in the local repository, i have all oficial packages downloaded in my local server.

---


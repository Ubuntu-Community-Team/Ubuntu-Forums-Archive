---
title: "Package is in a very bad inconsistent state language-pack-en"
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by cblanquer on 2011-06-13
I am running Kubuntu 11.04 on an XS35G.
Some days ago I began getting this error when performing the packages update OR when executing "":

> dpkg: error processing language-pack-en (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 language-pack-en
E: Sub-process /usr/bin/dpkg returned an error code (1)



I have tried several commands in order to get it back to a state I can continue using aptitude but none results in a solution (I do not list them in the order applied and some were executed several times):

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get remove language-pack-en-base language-pack-en language-pack-kde-en
sudo apt-get --reinstall install language-pack-en

I usually get an error message and a recommendation to execute "sudo apt-get -f install" which I already did, resulting in the error message that I posted.
(I searched the forum and googled, without success)
Currently my system does not accept any package update.
=> Any clue about how to solve this?

---


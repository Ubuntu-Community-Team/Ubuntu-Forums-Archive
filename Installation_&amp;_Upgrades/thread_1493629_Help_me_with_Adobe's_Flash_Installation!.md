---
title: "Help me with Adobe's Flash Installation!"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by Saurabhdua on 2010-05-26
Hello There!:popcorn:

Probably my 4th or 5th day with 'Brand New'=Ubuntu 10.04.Browser is very much light & hence do not allow me to browse the Web in totality!

'Missing Plug ins' are rampant in almost 4 out of 6 pages I browse!

"Update your client" do takes me to the attached screenshot but the Drop-down DO NOT lists any option intended for 10.04. Should I choose .deb for 8.04?

Want a 'No-Frills' kind of installation unlike that to .tar...etc.etc.

Help will be appreciated!:confused:

---

### Post by dino99 on 2010-05-26
add "medibuntu" repo:

into a console, copy/paste line by line

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get -q update
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring
sudo apt-get -q update

then into synaptic repo, enable "canonical partner" repo and update

then install flashplugin-installer

same thing with w32codecs

sudo apt-get install -f

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---


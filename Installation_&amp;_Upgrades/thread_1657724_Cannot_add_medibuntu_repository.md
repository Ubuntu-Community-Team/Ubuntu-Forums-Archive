---
title: "Cannot add medibuntu repository"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by slashwannabe94 on 2011-01-01
Hello everyone, i recently installed Ubuntu 10.4 LTS onto my new machine and when i tried to add the medibuntu repository using the 

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

command i receive this error... can anyone help? 

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>

Please help

Thanks, 

SlashWannabe94

---

### Post by jcolyn on 2011-01-01
You should contact Medibuntu at [EMAIL="admin@lists.medibuntu.org"]admin@lists.medibuntu.org[/EMAIL] and ask if their Lucid key has expired or you could try again later since they sometimes go down for varying times.

I know their Maverick key is good since I just installed it this morning..

You might also go here and do a copy/paste to be sure what you entered is correct [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---


---
title: "Problem with update manager"
date: 2013-03-01
forum: Installation &amp; Upgrades
---

### Post by DorianOriental on 2013-03-01
Hello there!
I've got a problem with the update manager, which doesn't open.
When I try to launch it the following error show up:

```
[COLOR=#101010][FONT=Ubuntu]E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.[/FONT][/COLOR]
```

[FONT=Ubuntu][COLOR=#101010]Can anybody give me a little help with that?
Thanks [/COLOR][/FONT]:)

---

### Post by dino99 on 2013-03-01
Update-manager is not the best piece of cake; use synaptic instead, or apt-get

sudo apt-get install synaptic
sudo apt-get update
sudo apt-get upgrade

---

### Post by DorianOriental on 2013-03-01
The first one gives me this:

Lettura elenco dei pacchetti... ErroreE: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal_main_i18n_Translation-en
E: L'elenco dei pacchetti o il file di stato non può essere letto o aperto.

I'm sorry for the language, it's italian.
I hope it doesn't create any problem!

---

### Post by plucky on 2013-03-01
> **DorianOriental said:**
> The first one gives me this:

Lettura elenco dei pacchetti... ErroreE: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal_main_i18n_Translation-en
E: L'elenco dei pacchetti o il file di stato non può essere letto o aperto.

I'm sorry for the language, it's italian.
I hope it doesn't create any problem!

Try from a terminal ```
sudo rm /var/lib/apt/lists/* -vf
``` then run ```
sudo apt-get update
``` to reload the list files.

Good Luck

---


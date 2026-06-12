---
title: "apt-get error... now i can't install!"
date: 2004-12-01
forum: Installation &amp; Upgrades
---

### Post by zeno on 2004-12-01
Hi all!
i have a big problem with apt-get:
i've tried to install a package for my laser printer (brother-MFC9880) with apt-get. It was a .deb package. Unfortunately apt-get didn't recognize this package (downladed from the official brother-linux website) and now when i try to install or remove any other ubuntu-package i read this error:

E: Il pacchetto mfc9880lpr deve essere reinstallato, ma non si riesce a trovare un archivio per esso.
Translation: Package mfc9880lpr needs to be reinstalled, but i don't find a archive for it.

After this message apt-get doesn't nothing... the shell comes back. I've tried to use all the options mentioned in the apt-get manual but the problem is ever here.
Please help me because i can't install more packages and i can't upgrade my ubuntu! :cry:

Tnx so much,
zeno - Italy

---

### Post by adbak on 2004-12-01
Non lo so come installare un pacchete per apt-get, ma prove installare usando il CLI.

[code]dpkg -i <nome del pacchete>.deb[code]

Dopo questo, lo dovrebbe essere installato.

How'd I do with my Italian?  I'm only in a 200-level class at college right now.

PS. I don't know if commands change depending on the language you use....

Buona fortuna!

---

### Post by zeno on 2004-12-02
[QUOTE=adbak]Non lo so come installare un pacchete per apt-get, ma prove installare usando il CLI.

[code]dpkg -i <nome del pacchete>.deb[code]

Dopo questo, lo dovrebbe essere installato.

How'd I do with my Italian?  I'm only in a 200-level class at college right now.
[/QUOTE]
Mmmmm... i think u speek a good italian and italian is a very hard language ! ;)

Tnx for your help but the problem is not "how-to install .deb package" but "How-to install .deb package when the error "package -foo- needs to be reinstalled, but i don't find the archive" has occurred - apt-crash".
I'm desperate... i cant' upgrade my ubuntu because of this lpr-driver that blocked the apt-get tool.
Even dpkg gives the same error of ap-get. I don't understand!

If u want to practice with italian send me a PM in italian... of course... i will answer in italian if u want.

Bye,
zeno

p.s.: remember that "pacchetto" is package and not "pacchete" :)

---

### Post by az on 2004-12-02
sudo dpkg -r mfc9880lpr

or

sudo apt-get remove --purge mfc9880lpr

Ciao!

---

### Post by zeno on 2004-12-02
[QUOTE=azz]sudo dpkg -r mfc9880lpr

or

sudo apt-get remove --purge mfc9880lpr

Ciao![/QUOTE]

I've tried with these 2 commands but the error is always the same.
I'm thinking about a reinstall of the entire o.s.... this seems to be the only one solution. No solutions from man pages, no solutions in this forum, no solution in the newsgroup... it's a strange problem!

Bye,
zeno

---


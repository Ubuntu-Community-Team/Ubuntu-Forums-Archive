---
title: "wine does not seem to install properly"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by dryder on 2007-07-01
feisty

Hi,

I installed wine on Edgy without a problem but on feisty I am having some difficulties. I have searched extensively but nothing seems to relate to anything I can relate to.

I need to install a windows program that I know runs in Edgy under wine.

1.
I choose wine and wine-dev from synaptic.
It appears to install OK and the .wine folder with contents is in my home folder.

2.
But there is no "Install with wine" option when I left click the .exe nor does wine appear under "choose another program" for installing.

3.
The program I want to install needs IE(4 or later). I install ie2linux but that does seem to be recognized as installed by wine.

Can anybody help me please?
David

---

### Post by ubuntu.daemon on 2007-07-02
Have you ever tried apt-get install wine  ??

And your gonna want the unstable, should be into something lik8 wine-0.38 now i think.  And if anything check winehq.com that shoul get you a jump start

---

### Post by Motoxrdude on 2007-07-02
Right click on the exe and select "open with other application>>use custom command" and type wine.

---


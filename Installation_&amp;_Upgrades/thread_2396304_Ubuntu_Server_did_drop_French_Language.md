---
title: "Ubuntu Server did drop French Language"
date: 2018-07-13
forum: Installation &amp; Upgrades
---

### Post by a-1enoit-n on 2018-07-13
Hi,

Such a shame, will trying installing 18.04 for the first time this morning and just realize Ubuntu did not offer french as supported language on installation.

I was using Ubuntu server since 10.04, but I want it in french, Do I have to move on Debian or Centos as they are still installable in french.

Trying to fill an issue on Launchpad trhow me an error and talking with Canonical support, he told me "French is still free", but it is not available

Fix-it or please WRITE IN BOLD "NE FRENCH SUPPORT"

Thank you

---

### Post by #&amp;thj^% on 2018-07-13
That's odd it shows here: [https://packages.ubuntu.com/search?keywords=language-pack-fr](https://packages.ubuntu.com/search?keywords=language-pack-fr)
```
apt search language-pack-fr
Sorting... Done
Full Text Search... Done
language-pack-fr/bionic,bionic 1:18.04+20180423 all
  translation updates for language French

language-pack-fr-base/bionic,bionic 1:18.04+20180423 all
  translations for language French

```

---

### Post by PaulW2U on 2018-07-15
> **a-1enoit-n said:**
> Trying to fill an issue on Launchpad trhow me an error and talking with Canonical support, he told me "French is still free", but it is not available

Fix-it or please WRITE IN BOLD "NE FRENCH SUPPORT"
I'm assuming you installed using the "new" installer and the [COLOR="#000080"]ubuntu-18.04-live-server-amd64.iso[/COLOR]?

I installed into a VM and although I opted to install using the French language it seem that the subsequent language options offered are very limited as my first screenshot shows. I continued in English and was offered a French keyboard layout. The resulting installation was of course in English but unusable by me due to the non-English keyboard layout.

A bug needs to be reported against the **subiquity** package.

If you use the alternative installer and the [COLOR="#000080"]ubuntu-18.04-server-amd64.iso[/COLOR] image you will no doubt see an installer that you are much more familiar with. It does allow an installation in French. See my second screenshot. You can download the alternative installer from [http://cdimage.ubuntu.com/releases/18.04/release/](http://cdimage.ubuntu.com/releases/18.04/release/).

And yes it does take a while to find if you first go the the Ubuntu Server's home page - [https://www.ubuntu.com/server](https://www.ubuntu.com/server). Hope that helps.

---


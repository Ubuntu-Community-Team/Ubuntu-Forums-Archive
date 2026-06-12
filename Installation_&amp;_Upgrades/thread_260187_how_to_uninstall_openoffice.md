---
title: "how to uninstall openoffice"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by bikeman123 on 2006-09-18
can someone provide step by step details as to how i can uninstall openoffice please.

I have tried using the synaptic package manager but it says that ubuntu desktop is a dependant.

can i remove open office and keep a working system?

---

### Post by linear on 2006-09-18
You were on the right track with Synaptic. Just let it uninstall ubuntu-desktop, which is just a meta package (only function is to depend on other things). Removing it won't harm anything.

---

### Post by trebler on 2006-12-12
yes I would like to know this too..... and yes its a me too post.

Can anyone please advise how to uninstall Open Pffice while retaining XWindows and desktop etc.

Is there a way to remove it without removing the dependencies.

Oh - X windows is a must.....but we need to lean it up a fair bit and too much junk is installed by default with these things... 

so please don't reply if you cannot address my question directly or specifically.

Thanks
treb

---

### Post by aysiu on 2006-12-12
Removing OpenOffice shouldn't remove X. It should, however, removed *ubuntu-desktop*, which is fine, because *ubuntu-desktop* is simply defined as "the default set of applications that make up Ubuntu." Once you remove one of those default applications, you no longer have *ubuntu-desktop*.

---

### Post by andreas64 on 2006-12-14
Hi

'sudo apt-get remove openoffice*' should work fine

Andreas

---

### Post by maxownz on 2008-01-28
> **andreas64 said:**
> Hi

'sudo apt-get remove openoffice*' should work fine

Andreas

```
maxownz@maxownz-ubuntu:~$ sudo apt-get remove openoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openoffice
maxownz@maxownz-ubuntu:~$ 

```

Didn't work for me :(

---

### Post by randomjohn on 2008-01-28
you didn't put the asterisk in the command like the previous poster said.  you need the wildcard to catch all the openoffice stuff.

the command is

sudo apt-get remove openoffice*

---

### Post by randomjohn on 2008-01-28
btw, I'm trying to uninstall it too (I should have just installed server edition in the first place) and came across this command
[LIST]
[*][COLOR=red][FONT=monospace]sudo apt-get -y remove openoffice.org  openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer[/FONT][/COLOR][/LIST]and you won't remove the virtual package ubuntu-desktop so you won't have to reinstall gdm or X or whatever

---

### Post by NoobieDoobieDo on 2008-05-24
> root@take-back-the-night# *apt-get remove openoffice**
"After this operation, 332MB disk scape will be freed."

**WOW!  That seems a bit excessive!**

Thanks for the tip, I also wasn't sure if "ubuntu-desktop" was safe to remove.  They make it sound like a VERY important package!

Note : GDM reloaded while I was removing OpenOffice so you might want to do it from the command line?

*Reloading GNOME Display Manager configure
*Changes will take effect when all current X sessions have ended [ OK ]

ps. Got an error :

Removing ispell ..

///usr/share/gnome/help/blackjack/el/blackjack.xml:402: parser error : Entity 'B(diamond symbol)(diamond symbol)(diamond symbol)(diamond symbol)' not defined
<para><guimenuitem>(more strange chars)&B;</gui

---


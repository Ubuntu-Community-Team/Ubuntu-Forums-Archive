---
title: "I've Done Something Silly with Sources"
date: 2012-09-04
forum: Installation &amp; Upgrades
---

### Post by yizrahomme on 2012-09-04
Hi,

I seem to have inadvertantly removed 'source code' or something.

Here's what I did.  I was trying to install 'Sound Convertor' from software-center, as a friend had asked me to convert some m4a into MP3.  I couldn't install it, as there was a warning about 'packets', so I went into software-center, and did Edit - Sources.

To cut a long story short, I screwed up, and now can't install anything.  Mea culpa.  Also, there's a red triangle with an exclamation mark at the top of the screen.

Can anyone help me to get it back?  Oh, and I'm in the UK, FYI.

Thanks.

---

### Post by elliotbeken on 2012-09-04
What release of ubuntu is it (e.g. ubuntu 11.04 32bit)...

You could just get someone elses sources and copy them into yours.

Then run:
sudo apt-get update

---

### Post by yizrahomme on 2012-09-04
> **elliotbeken said:**
> What release of ubuntu is it (e.g. ubuntu 11.04 32bit)...

You could just get someone elses sources and copy them into yours.

Then run:
sudo apt-get update

Thanks for the reply.

12.04 LTS.

EDIT: 32 bit.

How do I get someone else's sources?

---

### Post by wojox on 2012-09-04
Try this:
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.backup
sudo apt-get update
```

---

### Post by yizrahomme on 2012-09-04
> **wojox said:**
> Try this:
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.backup
sudo apt-get update
```

Hmm, well that's a bit better, thanks for that.  I still can't install Sound Convertor, the message being: *Depends  python-gnome2* but it won't be installed and *Depends: python-glade2 but it won't be installed.*

---

### Post by wojox on 2012-09-04
Do you have Restricted Extras installed?
```
sudo apt-get update; sudo apt-get install ubuntu-restricted-extras
sudo apt-get install soundconverter
```

Post back the errors.

---

### Post by yizrahomme on 2012-09-04
> **wojox said:**
> Do you have Restricted Extras installed?
```
sudo apt-get update; sudo apt-get install ubuntu-restricted-extras
sudo apt-get install soundconverter
```

Post back the errors.

Hi.  Here are the errors - in French.  I can translate them if you don't understand what they mean.

```
sudo apt-get install soundconverter
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Certains paquets ne peuvent être installés. Ceci peut signifier
que vous avez demandé l'impossible, ou bien, si vous utilisez
la distribution unstable, que certains paquets n'ont pas encore
été créés ou ne sont pas sortis d'Incoming.
L'information suivante devrait vous aider à résoudre la situation*: 

Les paquets suivants contiennent des dépendances non satisfaites*:
 soundconverter : Dépend: python-gnome2 mais il n'est pas installable
                  Dépend: python-glade2 mais il n'est pas installable
E: Impossible de corriger les problèmes, des paquets défectueux sont en mode «*garder en l'état*».
```

---


---
title: "[ubuntu] 16.10 Teamviewer messes up gscan2pdf"
date: 2016-10-30
forum: Installation &amp; Upgrades
---

### Post by mahjsa on 2016-10-30
Again, after upgrading to 16.10, I had installed gscan2pdf and got it working.
Now after that I installed Teamviewer (11.0.57095) and it completely messed up the gscan2pdf installation. When I try to install gscan2pdf I get the message that the package is broken, but no clear indication of what is wrong.
When I choose to repair gscan2pdf it just gets deleted.
Anyone an idea how to repair this broken package?

>>EDIT
Just tried apt-get -f install gscan2pdf; it gives following messages (I am sorry it&#347; in dutch)

```
apt-get -f install gscan2pdf
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De statusinformatie wordt gelezen... Klaar
Sommige pakketten konden niet geïnstalleerd worden. Dit kan betekenen
dat u om een onmogelijke situatie gevraagd heeft, of, indien u
de distributie 'unstable' gebruikt, dat sommige benodigde pakketten nog gemaakt moeten worden of uit 'Incoming' verwijderd werden.
De volgende informatie kan misschien helpen de situatie op te lossen:


De volgende pakketten hebben niet-voldane vereisten:
 gscan2pdf : Vereisten: libsane-perl (>= 0.05~0) maar het zal niet geïnstalleerd worden
             Vereisten: sane-utils (>= 1.0.17)
             Aanbevelingen: sane maar het zal niet geïnstalleerd worden
E: Kan problemen niet verhelpen, u houdt defecte pakketten vast.
```

It seems the installation of Teamviewer deleted libsane-perl and/or sane-utils but I don't know what went wrong.


So, I tried to install libsane-perl as proposed, because it seems to be missing, but then I get the message that it needs lib-sane.
Installing libsane seems to need libsane-common (=1.0.25+git20150528-1ubuntu2), but because of earlier problems with gscan2pdf and Canon MP560 I had to upgrade libsane-common to 1.0.26~git20151121-1.

---


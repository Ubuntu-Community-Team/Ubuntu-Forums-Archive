---
title: "Cant upgrade some packages on edgy"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by fabiomb on 2006-11-01
Finally i upgraded from Dapper to Edgy, a lot of problems (most of them you can see on this forum) but finally y make it!

but some packages are still "waiting" for something:

  hpijs libggi2 mplayer python-adns python-clientcookie python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools
  python-egenix-mxtools python-gadfly python-htmlgen python-htmltmpl python-imaging python-imaging-sane python-jabber python-kjbuckets
  python-ldap python-mysqldb python-pam python-pexpect python-pgsql python-pylibacl python-pyopenssl python-pyorbit python-pyxattr
  python-reportlab python-simpletal python-soappy python-sqlite python-syck python-twisted-conch python-twisted-core python-twisted-mail
  python-twisted-names python-twisted-news python-twisted-runner python-twisted-web python-twisted-words python-xml python-xmpp

all of them are in a strange state, my Kubuntu is in spanish  so:

```

fabio@WillyWonka:~$ sudo apt-get dist-upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo información de estado... Hecho
Calculando la actualización... Listo
Los siguientes paquetes se han retenido:
  hpijs libggi2 mplayer python-adns python-clientcookie python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools
  python-egenix-mxtools python-gadfly python-htmlgen python-htmltmpl python-imaging python-imaging-sane python-jabber python-kjbuckets
  python-ldap python-mysqldb python-pam python-pexpect python-pgsql python-pylibacl python-pyopenssl python-pyorbit python-pyxattr
  python-reportlab python-simpletal python-soappy python-sqlite python-syck python-twisted-conch python-twisted-core python-twisted-mail
  python-twisted-names python-twisted-news python-twisted-runner python-twisted-web python-twisted-words python-xml python-xmpp
0 actualizados, 0 se instalarán, 0 para eliminar y 40 no actualizados.


```


40 packages "retained" or whatever it means, wh0t? i must delete them? how i can finish my upgrade without reinstall all the damn distro?


sorry for my ugly english

(Edited Hoary to Dapper mistake)

---

### Post by PrinceArithon on 2006-11-01
The problem I think could be, because you upgraded from Hoary to Edgy, you should have upgraded to Dapper first and then went to Edgy.

No problem big guy your english is good.

---

### Post by fabiomb on 2006-11-01
sorry, was my mistake, i upgraded from DAPPER to EDGY :D but i have some problems with XORG, i don't know how i repaired the dependency-hell but the only packages remaining are them!

---


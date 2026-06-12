---
title: "delete /var/lib/ by mistake"
date: 2016-06-21
forum: Installation &amp; Upgrades
---

### Post by Karibot on 2016-06-21
hi everyone

i'm on ubuntu 14.04 TLS

i've by mistake deleted /var/lib/ and now, i can't install nothing on my ubuntu server (even apt-get upgrade gives me this error)

for now i get apache2 to work ! when i ask for a web page, i get the php source code unstead of loading the app (php not executing).
so, i run  : 
```

sudo apt-get install libapache2-mod-php5

```

and get back this message (sorry for the french language) :

```

dpkg: error processing package php5-cli (--configure):
 problèmes de dépendances - laissé non configuré
dpkg: des problèmes de dépendances empêchent la configuration de php5-readline :
 php5-readline dépend de phpapi-20121212 ; cependant :
  Le paquet phpapi-20121212 n'est pas installé.
  Le paquet php5-common qui fournit phpapi-20121212 n'est pas encore configuré.
 php5-readline dépend de php5-common (= 5.5.9+dfsg-1ubuntu4.17) ; cependant :
 Le paquet php5-common n'est pas encore configuré.
 php5-readline dépend de php5-cli (= 5.5.9+dfsg-1ubuntu4.17) ; cependant :
 Le paquet php5-cli n'est pas encore configuré.


Aucun rapport « apport » n'a été créé car le message d'erreur indique une erreur consécutive à un échec précédent.
                                                                                                                  Aucun rapport « apport » n'a été créé car le message d'erreur indique une erreur consécutive à un échec précédent.
                     Aucun rapport « apport » écrit car MaxReports a déjà été atteint
                                                                                     dpkg: error processing package php5-readline (--configure):
 problèmes de dépendances - laissé non configuré
dpkg: des problèmes de dépendances empêchent la configuration de libapache2-mod-php5 :
 libapache2-mod-php5 dépend de php5-common (= 5.5.9+dfsg-1ubuntu4.17) ; cependant :
 Le paquet php5-common n'est pas encore configuré.


dpkg: error processing package libapache2-mod-php5 (--configure):
 problèmes de dépendances - laissé non configuré
Des erreurs ont été rencontrées pendant l'exécution :
 php5-common
 php5-cli
 php5-readline
 libapache2-mod-php5
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

what is happening behind the scene is that some package still broken so it can't restore/configure them.

i have tryed a lot of things to try to restore such as :
```

sudo apt[COLOR=#FF0080]**-**[/COLOR][COLOR=#00008B]**get**[/COLOR] update
sudo apt[COLOR=#FF0080]**-**[/COLOR][COLOR=#00008B]**get**[/COLOR] clean
sudo apt[COLOR=#FF0080]**-**[/COLOR][COLOR=#00008B]**get**[/COLOR] autoremove
sudo apt[COLOR=#FF0080]**-**[/COLOR][COLOR=#00008B]**get**[/COLOR] update [COLOR=#FF0080]**&&**[/COLOR] sudo apt[COLOR=#FF0080]**-**[/COLOR][COLOR=#00008B]**get**[/COLOR] upgrade
sudo dpkg [COLOR=#FF0080]**--**[/COLOR]configure [COLOR=#FF0080]**-**[/COLOR]a
sudo apt[COLOR=#FF0080]**-**[/COLOR][COLOR=#00008B]**get**[/COLOR] install [COLOR=#FF0080]**-**[/COLOR]f
```

but it dosen't work.


thank you for your help

---

### Post by Impavidus on 2016-06-21
Better not make that kind of mistake.

/var/lib contains a lot of vital files for many programs, including files necessary for apt-get and dpkg to work. You not only broke some software packages, but broke the software to repair them too. I think the quickest solution is reinstalling.

---

### Post by Karibot on 2016-06-21
thanks for you quick response. i guess there is something to do to repair things :)

---


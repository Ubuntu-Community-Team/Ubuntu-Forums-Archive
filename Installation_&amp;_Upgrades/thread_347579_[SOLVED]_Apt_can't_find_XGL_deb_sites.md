---
title: "[SOLVED] Apt can't find XGL deb sites"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by unconcrete on 2007-01-27
Hi all,
I'm tring to install Xgl on my Dapper Drake computer. 
On the basis fo instructions found on the Beekroid website [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/)
I have added the following statements to my sources.list:
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main
deb [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main 
Then I've tried to install the keys typing so in a Terminal:
wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -
wget [http://media.blutkind.org/xgl/quinn.key.asc](http://media.blutkind.org/xgl/quinn.key.asc) -O - | sudo apt-key add -
wget [http://compiz-mirror.lupine.me.uk/quinn.key.asc](http://compiz-mirror.lupine.me.uk/quinn.key.asc) -O - | sudo apt-key add -
wget [http://ubuntu.compiz.net/quinn.key.asc](http://ubuntu.compiz.net/quinn.key.asc) -O - | sudo apt-key add -
The result is very unplesant. No server has been found and I can't install Xgl an Compiz. 
These are the warnings of the Terminal:
-------------------------------------------------------------------
pppmax02@peregonet:~$ sudo apt-get update
Err [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release.gpg
  Impossibile connettersi a xgl.compiz.info:80 (195.14.0.203). - connect (111 Connection refused)
Err [http://media.blutkind.org](http://media.blutkind.org) dapper Release.gpg
  Impossibile connettersi a media.blutkind.org:80 (216.55.142.216). - connect (111 Connection refused)
Err [http://compiz-mirror.lupine.me.uk](http://compiz-mirror.lupine.me.uk) dapper Release.gpg Impossibile risolvere 'compiz-mirror.lupine.me.uk'
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper/main Packages
...
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
...
Ign [http://compiz-mirror.lupine.me.uk](http://compiz-mirror.lupine.me.uk) dapper Release
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Ign [http://compiz-mirror.lupine.me.uk](http://compiz-mirror.lupine.me.uk) dapper/main Packages
Err [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release.gpg
  risoluzione di 'ubuntu.compiz.net' temporaneamete fallita
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Err [http://compiz-mirror.lupine.me.uk](http://compiz-mirror.lupine.me.uk) dapper/main Packages
  Impossibile risolvere 'compiz-mirror.lupine.me.uk'
Scaricato 196B in 7s (26B/s)
Impossibile ottenere [http://media.blutkind.org/xgl/dists/dapper/Release.gpg](http://media.blutkind.org/xgl/dists/dapper/Release.gpg)  Impossibile connettersi a media.blutkind.org:80 (216.55.142.216). - connect (111 Connection refused)
Impossibile ottenere [http://compiz-mirror.lupine.me.uk/dists/dapper/Release.gpg](http://compiz-mirror.lupine.me.uk/dists/dapper/Release.gpg)  Impossibile risolvere 'compiz-mirror.lupine.me.uk'
Impossibile ottenere [http://ubuntu.compiz.net/dists/dapper/Release.gpg](http://ubuntu.compiz.net/dists/dapper/Release.gpg)  risoluzione di 'ubuntu.compiz.net' temporaneamete fallita
Impossibile ottenere [http://xgl.compiz.info/dists/dapper/Release.gpg](http://xgl.compiz.info/dists/dapper/Release.gpg)  Impossibile connettersi a xgl.compiz.info:80 (195.14.0.203). - connect (111 Connection refused)
Impossibile ottenere [http://compiz-mirror.lupine.me.uk/dists/dapper/main/binary-i386/Packages.gz](http://compiz-mirror.lupine.me.uk/dists/dapper/main/binary-i386/Packages.gz) Impossibile risolvere 'compiz-mirror.lupine.me.uk'
Lettura della lista dei pacchetti in corso... Fatto
pppmax02@peregonet:~$
----------------------------------------------------------------------------------------------------------------------------
What went wrong?
I premit I know Linux very basically so forgive me for ex-Windows dependent lack of skills.
Thanx in advance
unconcrete

---

### Post by unconcrete on 2007-05-25
Please, close this thread
sincerely,
unconcete

---


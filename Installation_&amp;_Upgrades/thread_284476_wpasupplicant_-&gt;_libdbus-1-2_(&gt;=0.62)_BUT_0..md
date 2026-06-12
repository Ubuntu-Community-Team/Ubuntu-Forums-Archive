---
title: "wpasupplicant -&gt; libdbus-1-2 (&gt;=0.62) BUT 0.60-6ubuntu8 is to be installed ???"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by patagonik on 2006-10-25
I have a little problem here... in Synaptic, i can see the application wpasupplicant available for upgrade, but when trying to do so, this message comes out:

>  The following dependencies were unresolvable, blablablabla... 

wpasupplicant:

  Depends: libdbus-1-2 (>=0.62) but 0.60-6ubuntu8 is to be installed 


I have all the repositories avilable and so far i've never had problems with them. I've tried with "sudo apt-get dist-upgrade" as the upgrade manager suggested without succes. I also tried to reinstall libdbus, and nothing, and upgrades aren't available with my current configuration. Should i add any special repository? In that case, whichone? 

The point is that i would like to upgrade to Edgy Eft via gksu "update-manager -c" but the same wpasupplicant thing appears.

I do not wanna have problems with the upgrade so, if someone can kindly give me some clues, that could be great... 


Cheers ubunters!

---

### Post by patagonik on 2006-10-26
Come on... nobody? This should be an easy one... i don't think that it is due to the wapsupplicant but due to the dependencies thing!!! Heeeeeeeeelp!

---

### Post by jromer on 2006-10-29
I'm getting the same message...here's my source list


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

# add following for glx installation

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx

# Flash 9 repository
deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0

---

### Post by compuguy1088 on 2006-10-30
Your not the only person with this problem, I'm having the same issue. Though I checked the properties on the package in Synaptic, and Apparently the version it wants to upgrade to is for Dapper, not Edgy..... The version that comes with edgy is 0.5.4-5 (edgy), though what its trying to upgrade to is 0.5.5-3v1ubuntu0 (dapper).

---

### Post by compuguy1088 on 2006-10-30
I also like to show my sources.list, if that will help, at all....

```

deb file:/var/cache/apt-build/repository apt-build main
##### OFFICIAL REPOS #####

## Ubuntu
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Updates
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Backports
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe

##### UNOFFICAL REPOS #####

## Fonts
deb http://www.elisanet.fi/mlind/ubuntu edgy fonts
deb-src http://www.elisanet.fi/mlind/ubuntu edgy fonts

##### Treviño's Ubuntu Repository
##(for Flash 9 Beta)
deb http://3v1n0.tuxfamily.org dapper 3v1n0
deb-src http://3v1n0.tuxfamily.org dapper 3v1n0

##### Ubuntu Pouit Repository (v2) v6.10
##(for brasero)
deb http://mrpouit.tuxfamily.org edgy-pouit extra
deb-src http://mrpouit.tuxfamily.org edgy-pouit extra

# Latest skype
deb http://download.skype.com/linux/repos/debian/ stable non-free

#PLF Alternate Mirror
deb http://mrpouit.free.fr/plf-fallback edgy-plf free non-free
deb-src http://mrpouit.free.fr/plf-fallback edgy-plf free non-free

```

---

### Post by Nio on 2006-10-31
same problem!

when i do dist-upgrade now aptitude uninstalls ubuntu-minimal .... i think thats no good idea, because it includes upstart .... i dont know so much but i guess this is required to switch the thing on ....

---

### Post by patagonik on 2006-11-03
Thanks guys! At the end i've just upgraded to edgy without any major problem, so everything's fine... i didn't even know why that trouble started in my machine, and above all related to what!, but anyway, i'm a happy man again, "la machinna" works incredibely fine right now with edgy, i hope for you it's the same... HAVE A F***ING GOOD WEEKEND PEOPLE!:-D 

And see you arround!

pata

---


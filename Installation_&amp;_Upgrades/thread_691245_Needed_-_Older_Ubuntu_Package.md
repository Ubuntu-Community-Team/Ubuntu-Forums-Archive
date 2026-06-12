---
title: "Needed - Older Ubuntu Package"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by swu on 2008-02-08
I'm trying to build explorer-ssl on a 6.06 LTS box and it needs sun-java5-jdk and right now, java-6-jdk is the only package available.

Can I get the older 5-jdk? I've googled around a bit and don't see a way. Building explorer-ssl with 6-jdk doesn't work so I need the older version.

Thanks in advance!

- Steve

---

### Post by zvacet on 2008-02-08
Look [here](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=+sun-java5-jdk&searchon=names&subword=1&version=dapper&release=all),and be sure that you download and install dependencies(marked with red ball)first.

---

### Post by AdotB on 2008-02-08
I did a quick search and found this, hopefully its what you're looking for.

[http://packages.ubuntu.com/dapper/devel/sun-java5-jdk]("http://packages.ubuntu.com/dapper/devel/sun-java5-jdk")

---

### Post by swu on 2008-02-08
Many thanks! Still a bit of a newbie here. Once I grab this, where do I need to place it so I can do an 
 
apt-get install java... ?

Thanks again to the both of you, that was a HUGE help!

---

### Post by zvacet on 2008-02-08
You  can place it in your home dir if you want,or in var/cache/apt/archives.All of them you can install by click.Please chek if you have all repos open like [this](https://help.ubuntu.com/community/Repositories/Ubuntu).If you don´t do it.After that you should be able to find older java version in synaptic.Jusr in synaptic search box type **sun**.

---

### Post by swu on 2008-02-08
I put the file in /var/cache/apt/archives but when I do apt-get install sun-java5-jdk it says it can't find the package.

This is the server so I have no gui, I'm doing this all from the command line.

Thanks again for the input!

- Steve

---

### Post by zvacet on 2008-02-09
```
cd /var/cache/apt/archives
```

```
sudo dpkg -i sun-java5-jdk
```

---

### Post by swu on 2008-02-12
Many thanks to everyone! I pulled all the needed files and built my SSL-Explorer box without a hitch - once I had all the dependancies in place. It's up and running and so far, so good...

I did however have to hit three different sites before I found "good" packages. From the first two sites the packages had "broken pipes" when installing. I finally found clean packages at the wmich.edu site. I was beginning to get frustrated as download after download would not install...

Thanks again for everyone's help!

- Steve

---


---
title: "My mate can not check his uodates on ubuntu 10.10 (Polish)"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by pavelexpertov on 2010-12-20
My mate can not check for updates becasue of his error:
> B&#322;&#261;d GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: Nast&#281;puj&#261;ce podpisy nie mog&#322;y zosta&#263; zweryfikowane z powodu braku klucza publicznego: NO_PUBKEY 632D16BB0C713DA6B&#322;&#261;d GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: Nast&#281;puj&#261;ce podpisy nie mog&#322;y zosta&#263; zweryfikowane z powodu braku klucza publicznego: NO_PUBKEY DA360C64005E0276Nie uda&#322;o si&#281; pobra&#263; [http://ppa.launchpad.net/slawinscy/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/slawinscy/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
Nie uda&#322;o si&#281; pobra&#263; [http://ppa.launchpad.net/slawinscy/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/slawinscy/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
Nie uda&#322;o si&#281; pobra&#263; [http://ppa.launchpad.net/zgredziolo1995/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/zgredziolo1995/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
Nie uda&#322;o si&#281; pobra&#263; [http://ppa.launchpad.net/zgredziolo1995/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/zgredziolo1995/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
Nie uda&#322;o si&#281; pobra&#263; niektórych plików indeksu, zosta&#322;y one zignorowane lub zosta&#322;a u&#380;yta ich starsza wersja.

before that message appeared i used a bash line which i got it from this [trhead]("http://ubuntuforums.org/showthread.php?p=6604961") and then i got the error message (above) after i used bash line.

---

### Post by sikander3786 on 2010-12-20
Add the missing GPG keys by,

Applications > Accessories > Terminal:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 632D16BB0C713DA6
```
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DA360C64005E0276
```

Then go to Software Center > Edit > Software Sources > Other Software Tab and disable the 4 Launchpad PPAs which are not responding. They include 2 for 'slawinscy' and 2 for 'zgredziolo1995'.

Now run apt-get update again.

```
sudo apt-get update
```

If that still returns some errors, we need to see the complete output of these commands and in English please if possible.

```
sudo apt-get update
```

```
cat /etc/apt/sources.list
```

```
ls -l /etc/apt/sources.list.d
```

While posting, click the # icon in post menu and paste your text in between the generated code tags. In other words, wrap your text with [code] tags instead of [quote] tags.

Thanks.

---

### Post by pavelexpertov on 2011-01-24
Yeah thanx, but i got one question: how can i find out that 4 PPAs are not responding?

---

### Post by sikander3786 on 2011-01-24
The PPAs that are returning a 404 Error are not responding. I don't know if they might have started responding now as the above post is nearly a month old. They might have been down for maintenance.

---


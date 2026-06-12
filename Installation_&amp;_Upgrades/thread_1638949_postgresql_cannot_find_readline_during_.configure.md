---
title: "postgresql cannot find readline during ./configure"
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by rdangelojp7 on 2010-12-06
Hello there, I'm in the process of installing postgresql on 9.10 karmic, but during ./configure, readline could not be found. After searching the file system I confirmed I have readline, so how can I let postgresql know where to look?
many thanks in advance

---

### Post by uvwild on 2010-12-08
sudo apt-get install libreadline5-dev libreadline6-dev

:)

---

### Post by rdangelojp7 on 2010-12-09
Thanks for the reply! Actually it turned out that I needed 3 pieces of software during ./configure, all of them had to have both the regular (I think you call it runtime?) version AND the development version. And as you recommended, apt-get was all I needed to install all of it. I also used $ apt-cache search foo (and a bit of advice from the web) to find their latest versions. Here are the commands I used:
```

        for readline:
            $ sudo apt-cache search readline
            $ sudo apt-get install libreadline6 libreadline6-dev
                        (libreadline5-dev was already installed)
        for zlib-dev:
            $ sudo apt-cache search zlib
            $ sudo apt-get install zlib1g-dev
                        (so was zlib1g)
        for xml2:
            $ apt-cache search xml2
            $ sudo apt-get install libxml2 libxml2-dev

```

---


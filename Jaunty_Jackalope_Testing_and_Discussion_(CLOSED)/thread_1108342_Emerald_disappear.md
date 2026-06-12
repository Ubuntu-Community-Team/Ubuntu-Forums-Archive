---
title: "Emerald disappear?"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dentaku65 on 2009-03-27
Hi all,
I've found that my emerald is not available anymore.
In fusion-icon is not avail and with apt everything from emerald is installed
> emerald libemeraldengine0 libemeraldengine-dev

Any idea if I missed something?

---

### Post by dentaku65 on 2009-03-28
Well... I discovered that emerald is not belong from official repositories.
I solved in this way:
downloaded the las snapshot of emerald here
[http://gitweb.compiz-fusion.org/?p=fusion/decorators/emerald;a=summary](http://gitweb.compiz-fusion.org/?p=fusion/decorators/emerald;a=summary)
(the top right snapshot available) and compiled

```
tar xvzf emerald-2587edf409d15872140e887ea4242b72095d92f3.tar.gz
cd emerald/
./autogen.sh
make
sudo make install
sudo ln -s /usr/local/lib/libemeraldengine.so.0 /usr/lib/libemeraldengine.so.0
```

Now it's ok!

---

### Post by Nightstrike2009 on 2009-04-07
> Well... I discovered that emerald is not belong from official repositories.
I solved in this way:
downloaded the las snapshot of emerald here
[[http://gitweb.compiz-fusion.org/?p=f...rald;a=summary](http://gitweb.compiz-fusion.org/?p=f...rald;a=summary)]("http://gitweb.compiz-fusion.org/?p=fusion/decorators/emerald;a=summary")
(the top right snapshot available) and compiled

What it the file name I need to download from this page I am unsure as to which one, thanks again.

---


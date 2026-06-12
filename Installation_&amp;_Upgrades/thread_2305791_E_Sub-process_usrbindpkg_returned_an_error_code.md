---
title: "E: Sub-process /usr/bin/dpkg returned an error code"
date: 2015-12-09
forum: Installation &amp; Upgrades
---

### Post by Jordan_Karadakov on 2015-12-09
Hello guys,

The last couple of days I am getting this error every time I try to install anything. I didn't give it much thought but I need to update my flash player and I can't do it or at least I think this is the problem.

So this error message comes up at the end of an installation process in the terminal.
[img]http://i.imgur.com/GxmByc5.png[/img]

Here is an image I hope it helps you. Any help will be appreciated. Sorry for the Greek language in the image.

---

### Post by matt_symes on 2015-12-10
Hi

Open a terminal and type

```
sudo mv /usr/lib/python2.7/rfc822.pyc{,.bk}
```

```
sudo apt-get update
```

```
sudo apt-get install htop
```

Do you still get the error ?

Kind regads

---

### Post by Jordan_Karadakov on 2015-12-12
Everything is back to normal.

Thank you for your help!!

---


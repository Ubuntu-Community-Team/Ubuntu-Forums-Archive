---
title: "GDEbi problem"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by SuicideSmurf on 2009-09-24
Is anyone else experiencing this whenever they try to install anything?

[IMG]http://i35.tinypic.com/2ccwi8w.jpg[/IMG]

---

### Post by sisco311 on 2009-09-24
yep, it's a bug: [http://https://bugs.launchpad.net/ubuntu/+source/vte/+bug/388953]("http://https://bugs.launchpad.net/ubuntu/+source/vte/+bug/388953")

dpkg works just fine:
```
sudo dpkg -i packagename.deb
```

---

### Post by oboedad55 on 2009-09-24
> **sisco311 said:**
> yep, it's a bug: [http://https://bugs.launchpad.net/ubuntu/+source/vte/+bug/388953]("http://https://bugs.launchpad.net/ubuntu/+source/vte/+bug/388953")

dpkg works just fine:
```
sudo dpkg -i packagename.deb
```

I'm having the same problem regardless of method.

---

### Post by SuicideSmurf on 2009-09-24
Installing via Terminal works fine for me.

---

### Post by oboedad55 on 2009-09-24
> **SuicideSmurf said:**
> Installing via Terminal works fine for me.

Yes, I finally got Picasa installed. I had problems with fotoxx. The install recommended that I do, "sudo apt-get -f install", which I did with good results. What is the meaning of that particular command?

---

### Post by SuicideSmurf on 2009-09-24
> **oboedad55 said:**
> Yes, I finally got Picasa installed. I had problems with fotoxx. The install recommended that I do, "sudo apt-get -f install", which I did with good results. What is the meaning of that particular command?

-f is the force command. Kubuntu has an issue with Java that you have to run;

```
sudo aptitude -f install
```In the Terminal after KPackageKit bails on you.

---

### Post by oboedad55 on 2009-09-24
> **SuicideSmurf said:**
> -f is the force command. Kubuntu has an issue with Java that you have to run;

```
sudo aptitude -f install
```In the Terminal after KPackageKit bails on you.

I tried Kubuntu but couldn't get happy with the package management or the interface.

---

### Post by SuicideSmurf on 2009-09-24
> **oboedad55 said:**
> I tried Kubuntu but couldn't get happy with the package management or the interface.

Kubuntu 9.10 is a [SIZE=5][COLOR=Black]**HUGE**[/COLOR][/SIZE] improvement over previous versions.

---

### Post by oboedad55 on 2009-09-24
> **SuicideSmurf said:**
> Kubuntu 9.10 is a [SIZE=5][COLOR=Black]**HUGE**[/COLOR][/SIZE] improvement over previous versions.

Yes, it certainly is. The alpha of 9.10 is more stable then 9.04.

---

### Post by SuicideSmurf on 2009-09-24
> **oboedad55 said:**
> Yes, it certainly is. The alpha of 9.10 is more stable then 9.04.

Yeah, shame the KHTML kurse still exists though.

---


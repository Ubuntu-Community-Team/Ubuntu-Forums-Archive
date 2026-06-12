---
title: "Wine for Intrepid"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Gennn89 on 2008-10-23
Hey anyone know the command to terminal to download and install wine for intrepid?

---

### Post by Elfy on 2008-10-23
```
sudo apt-get install wine
```

---

### Post by aeiah on 2008-10-23
after spending all day messing around with some truly nerdy server apps at work, its nice to be reminded that at least some things are as simple as could be

---

### Post by forumache on 2008-10-24
> **Gennn89 said:**
> Hey anyone know the command to terminal to download and install wine for intrepid?

Why do you need to ask the command line for this?
Use System|Administration|Synaptic Package Manager.

You know, some people believe the "dark side" when it says that to use Linux you have to type commands into a terminal. This is no longer true.

If you know the command then it is much easier, but If you *need to ask* then, by all means, you have a GUI, use it :)

---

### Post by Elfy on 2008-10-24
That would work if there was an indication of which distro is being used - but there isn't here - synaptic won't work for kubuntu without being installed :)

You can search in the cli as well

```
apt-cache search *searchstring*
```

You can also find out which repository it's in

```
apt-cache madison packagename
```

---

### Post by forcecore on 2008-10-24
Why mess these apt things if there is modern way like windows has setup.exe and ubuntu has .deb [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by Elfy on 2008-10-24
Because it's easier for me :) and I like to have my debs in the same place.

---

### Post by niccholaspage on 2008-10-24
> **forcecore said:**
> Why mess these apt things if there is modern way like windows has setup.exe and ubuntu has .deb [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
Apt gets .deb files and installs them. And it takes a simple terminal command to install programs from the repository.

---

### Post by krazyd on 2008-10-24
..or just use the official winehq ubuntu repo for the latest version!
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---


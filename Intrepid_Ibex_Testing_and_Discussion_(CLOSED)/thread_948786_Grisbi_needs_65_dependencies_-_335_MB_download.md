---
title: "Grisbi needs 65 dependencies - 335 MB download"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by notoriousdbp on 2008-10-15
Hi, just upgraded to 8.10 lat night.  Gone to install Grisbi which I normally use as my personal finance app but it needs 65 dependencies and requires over 300MB to be downloaded.  Given that I have already downloaded the iso image and the necessary updates so far this week I'm wary of going over my bandwidth cap.  

Most of the dependencies are latex language packs and I only want English.  Is there a way for me to install it from the repos but without all the dependencies?

---

### Post by psyke83 on 2008-10-15
> **notoriousdbp said:**
> Hi, just upgraded to 8.10 lat night.  Gone to install Grisbi which I normally use as my personal finance app but it needs 65 dependencies and requires over 300MB to be downloaded.  Given that I have already downloaded the iso image and the necessary updates so far this week I'm wary of going over my bandwidth cap.  

Most of the dependencies are latex language packs and I only want English.  Is there a way for me to install it from the repos but without all the dependencies?

If you're worried about bandwidth, it probably wasn't a wise decision to install the beta release. You'll see updates every day until the final release.

---

### Post by mrboojive on 2008-10-15
The dependencies are almost certainly things that are necessary to run it. So even if you could install it without the dependencies, it wouldn't work.

---

### Post by pecos7 on 2008-10-15
In synaptic you have to uncheck "Consider recommended packages as dependencies" under Settings->Preferences menu.

---

### Post by marmuta on 2008-10-15
Thanks for Grisbi, just what I was looking for.

All the latex packages are only recommends. 
Grisbi seems to run just fine without them, except latex reports.
You can skip them with 
```
sudo apt-get install -o APT::Install-Recommends=false grisbi
```

---

### Post by notoriousdbp on 2008-10-16
Thanks for that - worked a treat.  Knew from previous experience it didn't need all those extras

---


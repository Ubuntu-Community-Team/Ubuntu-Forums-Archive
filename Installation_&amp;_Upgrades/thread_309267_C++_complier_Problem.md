---
title: "C++ complier Problem"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by chandrakant11 on 2006-11-29
I install ubuntu 6.01. On Intalling postgresql C++ is required . On configure postgresl error occur saying no C , C++ compiler found.
How to install C++ , C compiler.
Kind Regards
Chandrakant

---

### Post by daniminas on 2006-11-29
> sudo apt-get install gcc

¿?

---

### Post by taurus on 2006-11-29
```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by chandrakant11 on 2006-11-30
> **taurus said:**
> ```
sudo aptitude update
sudo aptitude install build-essential
```

Thanks Mates. Actually I n new to Ubuntu. Earlier I wrok on SUSE.

---

### Post by chandrakant11 on 2006-12-04
I try as described above method , but still I got no updates founds.
 Looking for c compiler.... no c compiler found.
 Plz help, with out c++ compiler , i could not anything

---

### Post by taurus on 2006-12-04
I think you are looking for g++.  What does it say when you run this command from a terminal/prompt?

```
gcc -v
```

---

### Post by maniacmook on 2006-12-08
I have had an issue with installing wine. I run
./configure

and then i get a message saying the my C compliler cannot create executables. So I performed all the suggestionsin this thread and still I am having this same issue.

Any thought, Im def a newb when it comes to this.:neutral:

---

### Post by taurus on 2006-12-08
> **maniacmook said:**
> I have had an issue with installing wine. I run
./configure

and then i get a message saying the my C compliler cannot create executables. So I performed all the suggestionsin this thread and still I am having this same issue.

Any thought, Im def a newb when it comes to this.:neutral:

Did you remember to install the build-essential package?

```
sudo aptitude update
sudo aptitude install build-essential
```

---


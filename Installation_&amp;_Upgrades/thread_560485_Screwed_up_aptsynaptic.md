---
title: "Screwed up apt/synaptic"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by neonl on 2007-09-26
Hi.

I'm having an annoying issue with aptitude.

Yesterday I was trying to install Virtualbox and I added tow addresses to /etc/apt/sources.list

Now every time I do ```
sudo apt-get install "something"
``` or ```
sudo apt-get upgrade
``` it says that Virtualbox needs to be reinstalled but there ain't no repositories for it, even though I removed those lines from sources.list...

Help, thanks...

---

### Post by TheWizzard on 2007-09-26
did you try to completely remove virtualbox?
sudo apt-get remove virtualbox

---

### Post by neonl on 2007-09-26
> **TheWizzard said:**
> did you try to completely remove virtualbox?
sudo apt-get remove virtualbox

The same thing when I try to remove. Every thing I do with apt-get or synaptic I get this damn message :(.

---

### Post by mszl_1 on 2007-09-26
have you looked at add/ remove programms and adjust the sourse lists at the top right hand corner? i founf i could add./ remove loads from there.:)

---

### Post by TheWizzard on 2007-09-26
> **neonl said:**
> The same thing when I try to remove. Every thing I do with apt-get or synaptic I get this damn message :(.

mmm, what went wrong when you tried to install virtualbox?
and can you please post the exact error message? 

please try to remove with the -f switch

```
sudo apt-get -f remove virtualbox
```

---

### Post by neonl on 2007-09-26
I'm going to post the error message, but I think it wont be very useful due to the fact that Ubuntu is installed in Portuguese but:

```
A Ler Listas de Pacotes... Pronto
Construindo Árvore de Dependências       
Lendo informação de estado... Pronto
E: O pacote virtualbox precisa ser reinstalado, mas não foi possível encontrar um repositório para o mesmo.

```

---

### Post by bapoumba on 2007-09-26
Please try:
```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

---


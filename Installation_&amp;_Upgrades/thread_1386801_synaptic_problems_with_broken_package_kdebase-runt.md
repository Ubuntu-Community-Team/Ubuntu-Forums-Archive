---
title: "synaptic problems with broken package kdebase-runtime"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by kweetniet on 2010-01-21
hello

I'm fairly a newbe.
Synaptic tells me I have a broken package: kdebase runtime
It tells when repairing:
E: /var/cache/apt/archives/kdebase-runtime_4%3a4.2.2-0ubuntu1.1_amd64.deb: poging tot overschrijven van `/usr/lib/kde4/libexec/kdesu', wat ook in pakket kdesudo zit

in english Try to overwrite......what also in the package kdesudo 

I can not repair it. Now I can not update anything. 
jaunty 
AMD64
almost everything works well

I saw on another site it&#347; an existing bug, but didn't found a solution
who can help me step by step

---

### Post by zvacet on 2010-01-21
Type in terminal 

```
sudo apt-get -f install
```

---

### Post by kweetniet on 2010-01-21
thank you very much for your reaction
so i did type interminal

then it looks like that it ends at the same point synaptic also ends

attempt to rewrite `/usr/lib/kde4/libexec/kdesu which is also in the package kdesudo
( i translated the above sentence)

looks there  is someting wrong with:
 /var/cache/apt/archives/kdebase-runtime_4%3a4.2.2-0ubuntu1.1_amd64.deb

I&#7743; struggling

---

### Post by pc-reparateur.nl on 2010-01-21
Hi kweetniet,

You are lucky I just had the same problem and I solved it with just removing kde-sudo

sudo apt-get remove kde-sudo 

After that I did the dist-upgrade without any problems!

Best regards,

Eric Schoonderwal


> **kweetniet said:**
> hello

I'm fairly a newbe.
Synaptic tells me I have a broken package: kdebase runtime
It tells when repairing:
E: /var/cache/apt/archives/kdebase-runtime_4%3a4.2.2-0ubuntu1.1_amd64.deb: poging tot overschrijven van `/usr/lib/kde4/libexec/kdesu', wat ook in pakket kdesudo zit

in english Try to overwrite......what also in the package kdesudo 

I can not repair it. Now I can not update anything. 
jaunty 
AMD64
almost everything works well

I saw on another site it&#347; an existing bug, but didn't found a solution
who can help me step by step

---

### Post by kweetniet on 2010-01-21
hoi Eric
Can I removing kde sudo without any damage (what does kde sudo do)

after dist-upgrade do i have another distribution? 9.10 or so
do i upgrade with synaptic?

Victor

---

### Post by zvacet on 2010-01-22
After 

```
sudo apt-get dist-upgrade
```

you will still have Jaunty.But yes you can upgrade via synaptic.**Refresh **and after that **mark all upgrades**.

---

### Post by kweetniet on 2010-01-22
try to remove kdesudo in terminal

answer: couldn't find kdesudo 
Problem still exist

victor

---

### Post by kweetniet on 2010-01-26
still no solution
?

---

### Post by kweetniet on 2010-01-26
unbelievable I think i did it

i found this :
sudo dpkg-divert --package kdebase-runtime --divert /usr/lib/kde4/libexec/kdesu.not-kdebase-runtime --rename /usr/lib/kde4/libexec/kdesu

this cleared the broken package syndrom in synaptic

I foun it here:

[https://bugs.launchpad.net/ubuntu/+source/kdebase-runtime/+bug/345776](https://bugs.launchpad.net/ubuntu/+source/kdebase-runtime/+bug/345776)
#13

---


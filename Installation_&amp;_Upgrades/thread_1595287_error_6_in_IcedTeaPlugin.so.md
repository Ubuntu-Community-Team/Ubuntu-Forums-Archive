---
title: "error 6 in IcedTeaPlugin.so"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by egbertsl on 2010-10-13
hi,

Yesterday I upgrade my Ubuntu 10.04 to 10.10....this upgrade finished on my Toshiba laptop without any problem until I wanted to start Chrome....nothing happened.....My Firefox is still working. I also installed Chromium but that didn't work either.There is no screen opening, only two errors in my messages log: 

1: Oct 13 09:51:23 laptop kernel: [ 1259.430944] lo: Disabled Privacy Extensions

2: Oct 13 09:51:24 laptop kernel: [ 1260.600425] chrome[6914]: segfault at 11acbf2 ip 01924cec sp b65add80 error 6 in IcedTeaPlugin.so[191d000+2e000]

Every time I try to start Chrome....this error messages appear in the log. It looks a bit like some Java error....I reinstalled Java and Chrome several times but without any luck....Since my knowledge of these things is limited...I would appreciate some help form you :-) 

Thx
greetings
Luppo   :confused:

---

### Post by Tombigel on 2010-10-14
I have the same error on a clean installation of Maverick.

---

### Post by pa4ito on 2010-10-21
I had the same problem. After upgrade from Ubuntu 10.4 to 10.10 Google Chrome stop starting. I had the same messages in the log about IcedTeaPlugin.so plugin. I try to find the solution and when remove "icedtea-6-plugin" with Synaptic, Chrome start successfully.

---

### Post by egbertsl on 2010-10-21
> **pa4ito said:**
> I had the same problem. After upgrade from Ubuntu 10.4 to 10.10 Google Chrome stop starting. I had the same messages in the log about IcedTeaPlugin.so plugin. I try to find the solution and when remove "icedtea-6-plugin" with Synaptic, Chrome start successfully.


Thanks pa4ito...that was a great suggestion.....Chrome works again :-) 


greetings
Luppo

---

### Post by earthmeLon on 2010-10-22
```
sudo apt-get remove icedtea6-plugin
```

---


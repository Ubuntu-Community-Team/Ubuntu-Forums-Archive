---
title: "W: GPG error"
date: 2010-04-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by coolcaseley67 on 2010-04-21
hi Every one 

- I hope you testing is going well ....
- have just used Synaptic package manager  and got this error :
"W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220" 

- can any help please ? thanks , i think i need to find the key for the ppa  : [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release ........


thanks

---

### Post by sisco311 on 2010-04-21
[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

You have to add the public key of the ppa repository to the list of trusted keys:
```
sudo add-apt-repository ppa:tualatrix/ppa
```
or
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
```

---

### Post by coolcaseley67 on 2010-04-21
hi 

-thanks  for your help , it worked and I will r ember way No2 .

---


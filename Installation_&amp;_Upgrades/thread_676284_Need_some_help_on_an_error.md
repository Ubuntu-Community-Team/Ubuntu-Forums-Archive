---
title: "Need some help on an error"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by Muscar on 2008-01-23
When i try to install Elisa 0.3.3, in the part where I'm supposed to paste the: deb [http://elisa.fluendo.com/packages](http://elisa.fluendo.com/packages) gutsy main into the sources.list it want me to reload the information about available software, then it gives me this error:

```
W: GPG error: [http://elisa.fluendo.com](http://elisa.fluendo.com) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7096EDEA5B4E69BB
```

---

### Post by reckless2k2 on 2008-01-23
you just need the public key added so you don't get this error. it's an "alright" error but just do this:

[http://elisa.fluendo.com/packages/](http://elisa.fluendo.com/packages/)

---

### Post by Muscar on 2008-01-24
> **reckless2k2 said:**
> you just need the public key added so you don't get this error. it's an "alright" error but just do this:

[http://elisa.fluendo.com/packages/](http://elisa.fluendo.com/packages/)

What? That's what i followed to install

---

### Post by Partyboi2 on 2008-01-24
what happens when you type in a termianal
```
wget http://elisa.fluendo.com/packages/philn.asc -O - | sudo apt-key add -
```

---

### Post by Muscar on 2008-01-24
wget [http://elisa.fluendo.com/packages/philn.asc](http://elisa.fluendo.com/packages/philn.asc) -O - | sudo apt-key add -
--14:28:35--  [http://elisa.fluendo.com/packages/philn.asc](http://elisa.fluendo.com/packages/philn.asc)
           => `-'
Resolving elisa.fluendo.com... [sudo] password for (username):
195.10.6.66
Connecting to elisa.fluendo.com|195.10.6.66|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,690 (1.7K) [text/plain]

100%[====================================>] 1,690         --.--K/s             

14:28:39 (1.55 MB/s) - `-' saved [1690/1690]

OK

---

### Post by Muscar on 2008-01-24
I tried again about 7 times and on the 7th try it worked, wierd

---

### Post by reckless2k2 on 2008-01-24
your welcome.

---


---
title: "signature could not be verified"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by aliyanage on 2006-12-06
Hi all,

Today I tried to:

```
sudo apt-get update
```

and at the end I got an error looking like this

```
W: GPG error: http://packages.freecontrib.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: You may want to run apt-get update to correct these problems
```

could someone please tell me what exactly this means or how can I make sure it's able to verify the signature?

thanks for your help
aliyanage

---

### Post by ahaslam on 2006-12-09
I'm getting the same message. Looking at their site shows that a key is required. To add the key you need to enter the following in a terminal:
```
wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg) -O- | sudo apt-key add
```
Though this is not working for me, it may for you. I'm getting the following error:
```
--23:49:07--  http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg
           => `-'
Resolving packages.freecontrib.org... gpg: can't open `': No such file or directory
88.191.37.159
Connecting to packages.freecontrib.org|88.191.37.159|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,120 (2.1K) [application/octet-stream]

 0% [                                     ] 0             --.--K/s


Cannot write to `12B83718.gpg' (Broken pipe).
```

Tony.

---

### Post by ahaslam on 2006-12-09
I've sorted it ;)

Just open a terminal & enter: **wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg)**
Followed by: **sudo apt-key add 12B83718.gpg**
It should then say OK ;)

Tony.

---

### Post by aliyanage on 2006-12-10
thank you worked fine for me. But could you explain to me what exactly the problem was?

regards
Andrew

---


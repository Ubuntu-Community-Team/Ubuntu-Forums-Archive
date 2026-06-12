---
title: "GPG Probs"
date: 2005-04-20
forum: Installation &amp; Upgrades
---

### Post by berzerked on 2005-04-20
I have just finished installing 5.04, and after adding repositories, I get the following gpg error:

berzerked@host11011:~$ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg: can't get key from keyserver: Connection refused
gpg: Total number processed: 0

Any idea as to why my connection is being refused?

TIA

---

### Post by magicfab on 2005-04-20
Can you ping the server ? Try this in a root terminal:

ping wwwkeys.eu.pgp.net
traceroute wwwkeys.eu.pgp.net

You're probably having network problems...

---

### Post by berzerked on 2005-04-20
Hi Magicfab,

Ping works
ping wwwkeys.eu.pgp.net
PING wwwkeys.eu.pgp.net (212.55.198.213) 56(84) bytes of data.
64 bytes from rex.citrin.ch (212.55.198.213): icmp_seq=1 ttl=44 time= 118 ms
64 bytes from rex.citrin.ch (212.55.198.213): icmp_seq=2 ttl=44 time=150 ms
64 bytes from rex.citrin.ch (212.55.198.213): icmp_seq=3 ttl=44 time=146 ms
64 bytes from rex.citrin.ch (212.55.198.213): icmp_seq=4 ttl=44 time=121 ms
64 bytes from rex.citrin.ch (212.55.198.213): icmp_seq=5 ttl=44 time=137 ms
64 bytes from rex.citrin.ch (212.55.198.213): icmp_seq=6 ttl=44 time=156 ms

Our network appears to be up.

TIA

---


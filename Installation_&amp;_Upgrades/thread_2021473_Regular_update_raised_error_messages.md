---
title: "Regular update raised error messages"
date: 2012-07-09
forum: Installation &amp; Upgrades
---

### Post by em wai zee on 2012-07-09
Hi, I did a regular update through the terminal...

> sudo apt-get update

Everything ran smoothly when in the end, it raised these error messages...

> Get:20 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [771 B]                 
Get:21 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [768 B]                  
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Fetched 376 kB in 2min 39s (2,361 B/s)
W: Failed to fetch [https://private-ppa.launchpad.net/commercial-ppa-uploaders/fullcircle-issue-61/ubuntu/dists/precise/main/binary-amd64/Packages](https://private-ppa.launchpad.net/commercial-ppa-uploaders/fullcircle-issue-61/ubuntu/dists/precise/main/binary-amd64/Packages)  gnutls_handshake() failed: A TLS packet with unexpected length was received.

W: Failed to fetch [https://private-ppa.launchpad.net/commercial-ppa-uploaders/fullcircle-issue-61/ubuntu/dists/precise/main/binary-i386/Packages](https://private-ppa.launchpad.net/commercial-ppa-uploaders/fullcircle-issue-61/ubuntu/dists/precise/main/binary-i386/Packages)  gnutls_handshake() failed: A TLS packet with unexpected length was received.

W: Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_precise_main_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.


I believed the error messages had prevented me to add other PPAs ... Please help me to solve this problem!

PS; I've uploaded a screenshot of the problem!

---

### Post by dino99 on 2012-07-09
ubuntu supposed you know what you are doing  :p

how much ppa do you need to install ? to do what ?
dont you have enough choice inside ubuntu archives ?

---

### Post by Old_Grey_Wolf on 2012-07-09
You need a username and password to us "private-ppa.launchpad.net".

When I went to one of the ppa links I got a login page. See attachment.

---

### Post by em wai zee on 2012-07-11
> **Old_Gray_Wolf said:**
> You need a username and password to us "private-ppa.launchpad.net".

When I went to one of the ppa links I got a login page. See attachment.

Ok ... It seems that I've being toying with 32bit arch ... So, how do I removed the 

> W: Failed to fetch [https://private-ppa.launchpad.net/co...-i386/Packages](https://private-ppa.launchpad.net/co...-i386/Packages) gnutls_handshake() failed: A TLS packet with unexpected length was received.

W: Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dist s_precise_main_binary-i386_Packages Hash Sum mismatch

---

### Post by raja.genupula on 2012-07-11
open your terminal
 type this

```
sudo rm -rf /var/lib/apt/lists/partial/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dist s_precise_main_binary-i386_Packages
```
 and press enter key .

 ```
sudo apt-get update
```

All The Best

---

### Post by em wai zee on 2012-07-13
> **raja.genupula said:**
> open your terminal
 type this

```
sudo rm -rf /var/lib/apt/lists/partial/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dist s_precise_main_binary-i386_Packages
```
 and press enter key .

 ```
sudo apt-get update
```

All The Best

TQ so much! Done & Solved!

---


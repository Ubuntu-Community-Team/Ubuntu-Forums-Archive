---
title: "erroe while sudo apt-get install kubuntu-full"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by forsubhi on 2012-05-08
I get this error while sudo apt-get install kubuntu-full


```

After this operation, 2,421 MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Err http://sy.archive.ubuntu.com/ubuntu/ precise/main libkimproxy4 amd64 4:4.8.2-0ubuntu1
  403  Forbidden [IP: 91.189.92.152 80]
Err http://archive.ubuntu.com/ubuntu/ precise/main libkimproxy4 amd64 4:4.8.2-0ubuntu1
  403  Forbidden [IP: 91.189.92.151 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkimproxy4_4.8.2-0ubuntu1_amd64.deb  403  Forbidden [IP: 91.189.92.151 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

what is the problem ?

---

### Post by RJARRRPCGP on 2012-05-08
Something looks fishy.  It looks like it was vandalized. :confused:

(I see tons of empty "ubuntu" directories at sy.archive.ubuntu.com)

---

### Post by forsubhi on 2012-05-08
How could I solve this problem ?  :popcorn:

---

### Post by cortman on 2012-05-08
Change mirrors, or check your sources.list to make sure it's not corrupted or changed in any way.

---

### Post by forsubhi on 2012-05-09
how can I change mirrors ?

---

### Post by cortman on 2012-05-09
> **forsubhi said:**
> how can I change mirrors ?

[Here.]("https://help.ubuntu.com/community/Repositories/Kubuntu")

---

### Post by forsubhi on 2012-05-12
I didn't know any ppa I should add from 
[https://launchpad.net/~kubuntu-ppa/+archive/ppa](https://launchpad.net/~kubuntu-ppa/+archive/ppa)

can you help me ?

---

### Post by forsubhi on 2012-05-12
My Internet service provider has firewall that prevent any search about word " proxy " so the package 
```

Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkimproxy4_4.8.2-0ubuntu1_amd64.deb 403  Forbidden [IP: 91.189.92.184 80]
```

libkimproxy
this word contain word " proxy " so I cannot download it , how can I put http proxy in ubuntu to download it 
and is there any proxy available for ubuntu ?

---

### Post by cortman on 2012-05-14
> **forsubhi said:**
> I didn't know any ppa I should add from 
[https://launchpad.net/~kubuntu-ppa/+archive/ppa](https://launchpad.net/~kubuntu-ppa/+archive/ppa)

can you help me ?

[URL="https://help.ubuntu.com/community/Repositories/Kubuntu"]Here.
[/URL]
> **forsubhi said:**
> My Internet service provider has firewall that prevent any search about word " proxy " so the package 
```

Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkimproxy4_4.8.2-0ubuntu1_amd64.deb 403  Forbidden [IP: 91.189.92.184 80]
```

libkimproxy
this word contain word " proxy " so I cannot download it , how can I put http proxy in ubuntu to download it 
and is there any proxy available for ubuntu ?

I don't understand what you're asking here. If your ISP is blocking anything to do with proxy, I don't think you'll be able to download it in a browser either, but you can by pasting

```
http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkimproxy4_4.8.2-0ubuntu1_amd64.deb
```

in your browser window. Is that what you were wondering?

---

### Post by forsubhi on 2012-05-14
I think the last option will work for me 
[http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkimproxy4_4.8.2-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkimproxy4_4.8.2-0ubuntu1_amd64.deb)
but I should use tor browser 

I 'll try

---

### Post by cortman on 2012-05-15
> **forsubhi said:**
> I think the last option will work for me 
[http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkimproxy4_4.8.2-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libkimproxy4_4.8.2-0ubuntu1_amd64.deb)
but I should use tor browser 

I 'll try

OK right, gotcha! Tor has come in handy more than once for me in that regard. Good luck!

---

### Post by forsubhi on 2012-05-18
tor solved my problem 

thanks

---


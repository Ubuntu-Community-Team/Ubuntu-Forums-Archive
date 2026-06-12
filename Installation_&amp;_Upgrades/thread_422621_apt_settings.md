---
title: "apt settings"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by r0ck80y on 2007-04-25
Hi!!
 
  Just removed dapper and installed feisty. The problem is with software updating. My net connection goes through a university firewall and I use the univ repos for all main, restricted etc packages, which don't require proxy settings. Outside univ repos like medubuntu need proxy settings. Unlike dapper, where there was an apt.conf file wherein i could make the necessary changes, in feisty i cant connect to both univ and non-univ repos at the same time. 
  When I give network settings in synaptic and/or  global settings through System-->Pref-->Network Proxy, i am able to connect outside univ repos but not the univ ones. When i don't give proxy settings, its the reverse case. Update Manager has no such proxy configuration settings. 
  My dapper machine had the following apt.conf file :
```
//Acquire::http::Proxy "false";
Acquire {
  http {
       Proxy "http://user:pass@proxyhost:port/";
    };
  ftp {
       Proxy "http://user:pass@proxyhost:port/";
       Proxy::proxyhost  "DIRECT";
     };
};

```

The above code took care of all kinds of repos. Should i create an apt.conf file here? I have been reading that command-line based software management isnt recommended for feisty (why?). So how to deal with this problem??

TIA :)

---

### Post by r0ck80y on 2007-04-25
Never mind...its all working now..made a typo in setting proxy :P
and also medibuntu required the gpg key which i hadn't downloaded...so :P again

---


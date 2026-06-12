---
title: "problem in using GRAILS on network"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by tapas_mishra on 2010-04-28
I added following to my /etc/apt/sources.list 
 ```

 deb [http://ftp.opentle.org/people/prach/debian/](http://ftp.opentle.org/people/prach/debian/) ./ 
 deb-src [http://ftp.opentle.org/people/prach/debian/](http://ftp.opentle.org/people/prach/debian/) ./

```
and installed grails apt-get install grails

 It was running on command prompt I could see 
```

  Welcome to Grails 1.0-RC2 - [http://grails.org/](http://grails.org/)
  Licensed under Apache Standard License 2.0
  Grails home is set to: /opt/grails-1.0-RC2        
        
    No script name specified. Use 'grails help' for more info

```
I created an application 
```

grails create-app abcd 
```
I got a folder abcd 

with following entries 
```

abcd.launch  abcd.tmproj  application.properties  build.xml  grails-app  lib  scripts  src  test  web-app 
```
so I infer that application abcd was created.

then I opened my browser [http://192.168.1.3:8080](http://192.168.1.3:8080) 
but I got an error 
```

The system returned:

    (111) Connection refused

The remote host or network may be down. Please try the request again. 


```
but I was accessing that system via SSH and there are no IPTABLES running on it.
It is a Debian Lenny Virtual Machine running on Xen.
```

 uname -r 
2.6.26-2-xen-amd64 
```
Now what is the error how can I debug that?

---


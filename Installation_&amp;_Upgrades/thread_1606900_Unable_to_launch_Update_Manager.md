---
title: "Unable to launch Update Manager"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by pinnicle329 on 2010-10-27
E:Type '--2010-06-27' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.

The above message laughs at me. Anyway, looked through the forums, couldn't find a problem similar to mine. 

Thanks in advance for any help! 

Cheers

---

### Post by Elfy on 2010-10-27
I'd guess that your medibuntu list is completely wrong as that is often the case. But it could be that it is just line 1.

Open the file for editing as root

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

All lines should start with either #, deb or deb-src.

If the whole file looks wrong paste it here.

There are thousands of threads with source list errors - not quite sure what you searched for though :) Try using googlubuntu instead of the forum search engine.

---

### Post by pinnicle329 on 2010-10-27
--2010-06-27 00:59:58--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
Resolving [www.medibuntu.org]("http://www.medibuntu.org")... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80]("http://www.medibuntu.org%7C87.98.242.110%7C:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: 276 [text/plain]
Saving to: `hardy.list'

     0K                                                       100% 22.7M=0s

2010-06-27 00:59:58 (22.7 MB/s) - `hardy.list' saved [276/276]


Here's that! I suppose replace the time and date with some sort of code i can barely understand?

Edit: Sorry for not looking around more, i did use the forums search function O.o

---

### Post by Elfy on 2010-10-27
Ok - I suspected as much - open a terminal

Remove the existing file 

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```

Get the medibuntu sources again 
```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by pinnicle329 on 2010-10-27
You are a beautiful and powerful person. Thank you.

Cheers

---

### Post by Elfy on 2010-10-27
:lol: hardly 

Can you mark the thread solved please - thread tools at the top.

---

